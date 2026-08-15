# Debugging Prompt: Heap Dump Diagnostics & Memory Leak Analysis

## Purpose
Analyze memory heap dump summaries, garbage collection (GC) metrics, and object allocation trees to pinpoint memory leaks and optimize memory footprint.

## Inputs
- `HEAP_SUMMARY`: Text summary of heap dump, top retained sizes, object count tables, or memory allocation profiles.
- `RUNTIME_ENVIRONMENT`: Language runtime and memory manager (e.g., JVM, V8 Engine, Python GC, Go Runtime).
- `GC_LOGS`: Garbage collection log outputs, pauses, and generational memory metrics.

## Instructions
1. Inspect `HEAP_SUMMARY` to identify objects occupying disproportionate retained memory sizes.
2. Trace retainment paths (GCRoots) leading back to leaky objects (e.g., unclosed listeners, global caches, un-evicted maps, cyclic references).
3. Correlate `GC_LOGS` with heap usage to differentiate between insufficient memory sizing and true programmatic memory leaks.
4. Formulate specific code refactoring strategies to clear references when objects exit active lifecycles (e.g., implementing WeakReferences, LRU eviction, explicit event unsubscription).
5. Recommend monitoring alerts and heap thresholds for production detection.

## Constraints
- Focus on root allocation sources rather than transient short-lived objects.
- Distinguish between high memory throughput (normal allocation churn) and memory leaks (monotonic retainment growth).

## Expected output
- **Dominant Leak Candidates**: Ranked list of retained objects and their allocation roots.
- **GCRoot Retainment Path Analysis**: Step-by-step memory retention graph explanation.
- **Code Fix & Remediation**: Specific code pattern adjustments to prevent leak.
