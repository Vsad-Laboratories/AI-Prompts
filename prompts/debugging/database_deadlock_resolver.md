# Debugging Prompt: Database Deadlock Resolver

## Purpose
Analyze transaction concurrency flows, lock escalations, and thread behavior to resolve database deadlock situations.

## Inputs
- `DEADLOCK_LOG_DUMP`: Output logs from the database engine detailing the blocked queries, transaction IDs, and acquired lock types.
- `TRANSACTION_SOURCE_CODE`: Application source files or ORM actions that run the concurrent database operations.

## Instructions
1. Parse the `DEADLOCK_LOG_DUMP` to identify the competing transaction threads, the locks they hold, and the locks they are waiting to acquire.
2. Construct a dependency graph representing the cyclic wait conditions between the concurrent threads.
3. Trace the operations back to `TRANSACTION_SOURCE_CODE` to see how code constructs (like nested loops or conditional updates) translate into lock acquisitions.
4. Recommend modifications to the lock escalation behavior (e.g., changing isolation levels, sorting lock order, or rewriting long-lived transactions into shorter batches).
5. Formulate optimal database-specific queries or ORM patterns to prevent the deadlock.

## Constraints
- Never advise disabling lock safety mechanisms or adopting Read Uncommitted isolation levels unless explicitly acceptable.
- Ensure all query modifications preserve database consistency.

## Expected output
- **Cyclic Wait Dependency Graph**: Markdown visualization of the thread lock-wait cycle.
- **Deadlock Root Cause Diagnosis**: Deep explanation of the lock contention and escalation mechanics.
- **Source Code Mitigation**: Modified, deadlock-safe source code or ORM queries.
- **Prevention Rules**: Rules for lock ordering and query nesting.
