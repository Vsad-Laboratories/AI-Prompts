# Debugging Prompt: API Latency Bottleneck Profiler

## Purpose
Inspect execution profiles, flame graphs, and network telemetry to localize and resolve latency bottlenecks in high-throughput API endpoints.

## Inputs
- `API_EXECUTION_PROFILE`: Flame graph statistics, CPU/memory trace data, database query logs, and execution time breakdowns for the bottleneck endpoint.
- `ENDPOINT_SOURCE_CODE`: The controller, service, and database interface code executing the target transaction.

## Instructions
1. Analyze the performance statistics in `API_EXECUTION_PROFILE` to separate the total transaction duration into CPU time, I/O wait, network latency, and synchronization overhead.
2. Locate performance hotpaths (e.g., serialization bottlenecks, N+1 query loops, or heavy cryptographic actions) in the `ENDPOINT_SOURCE_CODE`.
3. Investigate potential concurrency bottlenecks (e.g., thread starvation, lock contention, or slow external API dependencies).
4. Propose code optimizations, such as lazy evaluation, query batching, asynchronous background execution, or caching strategies.
5. Provide estimated throughput improvement curves before and after optimization.

## Constraints
- Ensure all recommendations maintain API response correctness and keep memory growth within safe operational boundaries.
- Avoid introducing external runtime dependencies unless local code enhancements are insufficient.

## Expected output
- **Performance Execution Analysis**: Detailed breakdown of the latencies in the profile.
- **Code Hotpath Diagnosis**: Specific annotations of suboptimal loops or synchronous operations in the source code.
- **Optimized Controller & Service Code**: Performance-tuned code snippets using asynchronous, optimized patterns.
- **Caching & Pooling Policy**: Configuration specs for connection pools or key-value caches.
