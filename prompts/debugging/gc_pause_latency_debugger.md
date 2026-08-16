# Debugging Prompt: Garbage Collection (GC) Pause & Latency Bottleneck Debugger

## Purpose
Inspect garbage collection logs, runtime memory allocation graphs, and GC pause metrics (Java JVM, Go, Node.js V8) to eliminate stop-the-world latency spikes.

## Inputs
- `GC_LOG_DATA`: Raw GC logs (e.g., `-Xlog:gc*`, Go `gctrace`, Node.js `--trace-gc`).
- `RUNTIME_ENGINE`: Target runtime environment and heap configuration specs.

## Instructions
1. Analyze `GC_LOG_DATA` for allocation rates, object promotion rates, survivor space exhaustion, and GC pause durations.
2. Determine GC bottleneck mode: Young generation size pressure, Old generation fragmentation, Concurrent Mark failure, or Full GC triggers.
3. Evaluate object allocation patterns in application code leading to excessive garbage generation.
4. Formulate optimized runtime tuning flags (e.g., JVM G1GC/ZGC parameters, Go `GOGC` / `GOMEMLIMIT` thresholds).
5. Recommend code refactorings (e.g., object pooling, zero-allocation buffers, primitive arrays) to reduce allocation churn.

## Constraints
- Tailor tuning flags explicitly to `RUNTIME_ENGINE` version to avoid deprecated JVM/Go parameters.
- Prioritize application-level allocation reduction over pure runtime flag tuning.

## Expected output
- **GC Performance Profile**: Pause latency distribution, throughput percentage, and promotion rate analysis.
- **Root Cause Diagnostic**: Detailed cause of GC pause spikes.
- **Runtime Tuning Parameters**: Recommended CLI flags and heap configuration settings.
- **Zero-Allocation Code Recommendations**: Refactoring suggestions to minimize object creation.
