# Coding Prompt: Async & Concurrency Pattern Refactoring Guide

## Purpose
Refactor synchronous, blocking, or poorly synchronized code into high-throughput, thread-safe asynchronous routines while preventing deadlocks, race conditions, and resource exhaustion.

## Inputs
- `BLOCKING_CODE`: Code snippet containing blocking calls, synchronous loops, or unhandled concurrency.
- `PROGRAMMING_LANGUAGE`: Target language/runtime (e.g., Python asyncio, Node.js Event Loop, Go Goroutines, Rust tokio).
- `CONCURRENCY_TARGETS`: Concurrency limits, connection pool limits, and rate limits.

## Instructions
1. Identify blocking I/O operations, shared state mutations, and unthrottled worker spawns in `BLOCKING_CODE`.
2. Redesign code using idiomatic concurrency primitives (e.g., semaphores, worker pools, channels, async/await futures).
3. Implement explicit concurrency bounding mechanisms (e.g., bounded semaphores or rate limiters) to prevent memory exhaustion under high concurrency.
4. Add atomic operations or mutex locking around shared state variables to eliminate data races.
5. Provide before-and-after benchmarks or complexity analysis highlighting throughput improvements.

## Constraints
- Do not spawn unbounded background tasks/goroutines without worker pool limits.
- Ensure proper cancellation and timeout handling on all network or async calls.

## Expected output
- **Concurrency Audit**: Vulnerabilities identified in legacy code.
- **Refactored Asynchronous Code**: Clean, well-commented, thread-safe code block.
- **Resource Management Rules**: Timeout, cancellation, and concurrency pool guidelines.
