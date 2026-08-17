# Memory Fragmentation & Custom Allocator Profiler

## Purpose
Inspect, diagnose, and resolve high native memory fragmentation, heap bloat, and Virtual Memory vs. Resident Set Size (VSZ/RSS) drift in low-latency C/C++, Rust, Go, or Java applications using custom memory allocators (`jemalloc`, `tcmalloc`, `mimalloc`, `ptmalloc`).

## Inputs
- `ALLOCATOR_PROFILE_DATA`: Output from `jeprof`, heap profiling dumps, `/proc/meminfo`, `malloc_info()` XML, or eBPF allocation tracepoints.
- `SYSTEM_MEMORY_METRICS`: Process RSS, VSZ, active heap bytes, allocated object bytes, page fault counters, swap activity.
- `ALLOCATOR_CONFIGURATION`: Current environment variables or runtime flags (e.g., `MALLOC_CONF`, `TCMALLOC_SAMPLE_PARAMETER`).

## Instructions
1. **Differentiate Memory Fragmentation Types**:
   - **External Fragmentation**: Total free heap memory is sufficient, but contiguous unmapped pages are unavailable due to scattered active allocations. Calculate the RSS vs Active Heap gap:
     $$\text{Fragmentation Ratio} = \frac{\text{Process RSS} - \text{Active Allocated Bytes}}{\text{Process RSS}}$$
   - **Internal Fragmentation**: Wasted padding bytes within fixed allocator size classes (e.g., allocating 33 bytes into a 48-byte bucket).
2. **Analyze Allocator Heap Dump**: Parse allocation profiling logs to identify active arenas, size class distributions, thread cache (`tcache`) retention, and call sites responsible for high page retention.
3. **Isolate High-Frequency Allocation Hotspots**: Identify code locations triggering high-frequency, short-lived heap allocations that bypass thread caches or trigger excessive `brk()` / `mmap()` syscalls.
4. **Formulate Allocator Parameter Tuning Plan**:
   - **`jemalloc` Tuning**: Optimize `dirty_decay_ms`, `muzzy_decay_ms`, `narenas`, `lg_chunk`, and `background_thread` settings.
   - **`tcmalloc` Tuning**: Adjust thread cache limits (`tcmalloc.max_total_thread_cache_bytes`) and memory release rates.
   - **`ptmalloc` (glibc) Tuning**: Adjust `M_MMAP_THRESHOLD`, `M_ARENA_MAX`, and `M_TRIM_THRESHOLD`.
5. **Architect Code-Level Refactoring Solutions**: Design object pools, slab allocators, arena/bump allocators, or fixed-size freelists to eliminate runtime heap allocations in hot execution paths.

## Constraints
- **Preserve Low-Latency Guarantees**: Allocator parameter changes MUST NOT introduce severe lock contention across concurrent threads or stop-the-world page purges.
- **Provide Production Environment Presets**: Deliver copy-paste `MALLOC_CONF` or environment variable configurations.
- **Traceable Attribution**: Reference explicit call stack frame lines, size class buckets, and arena IDs in diagnostic outputs.

## Expected Output Format
```markdown
### 1. Memory Fragmentation Diagnostics
- **Process RSS**: [N] MB
- **Active Allocated Heap**: [N] MB
- **Unmapped Unused Heap**: [N] MB
- **Calculated Fragmentation Ratio**: [X%]
- **Primary Mechanism**: [External Fragmentation / Internal Size-Class Padding / Unpurged Arena Decay]

### 2. High-Impact Allocation Hotspots
| Call Site / Stack Trace Frame | Allocation Size | Size Class Bucket | Frequency (allocs/sec) | Contributed Fragmentation |
| :--- | :--- | :--- | :--- | :--- |
| `BufferPool::allocate()` (line 142) | 33 bytes | 48 bytes (Internal) | 120,000/sec | High |

### 3. Allocator Runtime Tuning (`MALLOC_CONF`)
```bash
# Optimized jemalloc configuration string
export MALLOC_CONF="background_thread:true,dirty_decay_ms:1000,muzzy_decay_ms:2000,narenas:4"
```

### 4. Code-Level Refactoring Strategy
- **Architectural Change**: [Arena Allocation / Slab Pool / Stack Allocation]
- **Refactored Code Example**:
```cpp
// Arena-based allocation eliminating individual malloc heap allocations
void process_packet_batch(const PacketBatch& batch) {
    auto arena = ArenaAllocator::thread_local_arena();
    // Rapid bump allocation
}
```
```

## Evaluation Criteria
- **Diagnostic Precision**: Pinpoints exact allocation call sites and size classes causing heap drift.
- **Tuning Effectiveness**: Proposed allocator configurations measurably reduce RSS without degrading runtime throughput.
- **Zero-Allocation Execution**: Code refactoring successfully moves high-frequency allocations out of global heap allocators.

## Failure Considerations
- **Confusing Leaks with Fragmentation**: Treating monotonic memory leaks as fragmentation issues instead of un-freed pointers.
- **Over-Aggressive Page Purging**: Setting decay times to `0ms`, causing CPU starvation due to continuous `madvise(DONTNEED)` syscall loops.
