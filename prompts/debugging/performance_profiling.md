# Debugging Prompt: Memory Leak and Performance Profiling

## Purpose
Examine application behaviors, logs, and profiling summaries to locate, explain, and fix memory leaks or CPU bottlenecks.

## Inputs
- `PROFILING_LOGS`: Profiler summaries, heap dumps, CPU profiles, or flame graph reports.
- `SOURCE_SNIPPET`: The code block suspected of causing the memory leak or CPU spike.

## Instructions
1. Inspect the `PROFILING_LOGS` to locate signs of high memory growth or high CPU utilization.
2. Read the `SOURCE_SNIPPET` to find common patterns that lead to leaks or bottlenecks (e.g., dangling references, closures, global state, nested loops, unclosed database sessions).
3. Draft a logical flow explaining how memory or CPU is consumed and why it is not properly reclaimed.
4. Provide a rewritten, optimized version of the code that resolves the leak or bottleneck.
5. Create a verification routine to ensure the fix is successful and doesn't introduce side effects.

## Constraints
- Do not make generic recommendations; the optimization must directly address the specific lines of code in `SOURCE_SNIPPET`.
- Ensure all garbage collection or memory cleanup methods are handled safely and automatically.

## Expected output
- **Profiling Verdict**: Precise identification of the line(s) causing the leak or bottleneck.
- **Root-Cause Explanation**: Narrative explanation of the mechanism of the bug.
- **Optimized Implementation**: Corrected code with explanation of the improvements.
- **Stress-Test Guide**: Simple test scripts or commands to verify performance under heavy load.
