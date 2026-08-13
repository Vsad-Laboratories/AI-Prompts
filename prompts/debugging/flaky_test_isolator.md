# Debugging Prompt: Flaky Test and Race Condition Isolator

## Purpose
Inspect, isolate, and debug intermittent test failures ("flaky tests") or suspected concurrent race conditions in multi-threaded/async code.

## Inputs
- `FLAKY_TEST_SUITE_AND_LOGS`: The code of the failing test, output logs, or standard error traces from CI/CD.
- `ASYNC_SOURCE_CODE`: The production code being tested, showing how threads, asynchronous operations, or databases are accessed.

## Instructions
1. Analyze the `FLAKY_TEST_SUITE_AND_LOGS` to find common symptoms of concurrency issues (e.g., deadlocks, mismatched expectations, non-deterministic execution order, shared-state mutation).
2. Examine `ASYNC_SOURCE_CODE` to locate shared state, race conditions, unawaited promises/futures, or timing dependencies.
3. Formulate 3 plausible reasons why the test is failing intermittently (e.g., database clean-up timing, shared static variables, network mocking delays).
4. Provide a rewritten, thread-safe, and deterministic version of both the test code and production code.
5. Create a stress-testing command or script (such as running the test 100 times in parallel) to verify the fix.

## Constraints
- Do not use lazy fixes like simple thread sleeps (`time.sleep` or hard-coded delays) unless absolutely unavoidable; use deterministic synchronizations (e.g., locks, events, mock timers).
- Do not remove the test to "fix" the flake; the test must be made resilient.

## Expected output
- **Concurrency Bottleneck Audit**: Trace of potential race paths between concurrent entities.
- **Intermittency Diagnoses**: Detailed list of possible flake causes with probability rankings.
- **Deterministic Code Improvements**: Secure, synchronized code with architectural explanations.
- **Reliability Verification Routine**: Run instructions or bash scripts to check test stability.
