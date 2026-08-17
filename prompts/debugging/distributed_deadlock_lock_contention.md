# Distributed Deadlock & Lock Contention Debugger

## Purpose
Inspect, isolate, and resolve distributed database deadlocks, thread lock contention, and resource locking cycle dependencies across microservice architectures, multi-threaded application runtimes, and relational/NoSQL datastores (PostgreSQL, MySQL, Distributed SQL, Redis).

## Inputs
- `TRANSACTION_LOCK_LOGS`: Database engine deadlock graphs (e.g., `SHOW ENGINE INNODB STATUS`, PostgreSQL `pg_locks` / `pg_stat_activity` views, Redis lock timeout traces).
- `THREAD_DUMP_TRACES`: Application stack dumps showing thread state (`WAITING (on object monitor)`, `BLOCKED (on mutex)`), lock addresses, and thread IDs.
- `APPLICATION_SOURCE_CODE`: Transactional data access code, ORM queries, explicit lock blocks (`SELECT FOR UPDATE`, mutex synchronization blocks).

## Instructions
1. **Construct Lock Dependency Graph**: Parse `TRANSACTION_LOCK_LOGS` and `THREAD_DUMP_TRACES` to build a directed lock wait-for graph:
   - **Nodes**: Transactions / Threads ($T_1, T_2, \dots, T_n$).
   - **Edges**: Directed wait dependencies ($T_1 \xrightarrow{\text{waits for lock on R_A}} T_2 \xrightarrow{\text{waits for lock on R_B}} T_1$).
2. **Detect Cycle Path**: Identify closed loop cycle paths ($T_1 \rightarrow T_2 \rightarrow \dots \rightarrow T_1$) establishing a definitive circular deadlock condition.
3. **Analyze Code-Level Lock Acquisition Sequence**: Cross-reference wait-for nodes against `APPLICATION_SOURCE_CODE`. Pinpoint inconsistent lock acquisition sequences across concurrent execution paths:
   - Thread A acquires Lock Alpha, then attempts to acquire Lock Beta.
   - Thread B acquires Lock Beta, then attempts to acquire Lock Alpha.
4. **Evaluate Isolation Level & Lock Scope**: Assess if explicit locks (`SELECT FOR UPDATE`, table-level locks) or gap locks (InnoDB) are acquiring broader resource ranges than necessary under current database isolation levels (`REPEATABLE READ`, `SERIALIZABLE`).
5. **Formulate Resolution Strategy**:
   - **Enforce Deterministic Lock Ordering**: Guarantee all threads/transactions acquire resources in a strict, uniform order (e.g., sort entity IDs before acquiring row locks).
   - **Reduce Transaction Scope**: Move non-database external calls (HTTP, RPC, file I/O) out of active transactional lock boundaries.
   - **Optimistic Locking with Retry**: Replace pessimistic row locks (`FOR UPDATE`) with version-based optimistic concurrency control (`WHERE version = :expected`).
   - **Index Optimization**: Add missing secondary indexes to prevent lock escalation from row-level locks to full table scan locks.

## Constraints
- **Absolute Lock Order Consistency**: Every proposed resolution MUST mathematically enforce uniform lock acquisition ordering across all execution paths.
- **No Long-Lived Transactions**: Never keep active database transactions open across network RPC calls.
- **Traceable Attribution**: Explicitly cite resource IDs, row primary keys, lock types (Exclusive vs Shared vs Intention), and file/line numbers in diagnostic summaries.

## Expected Output Format
```markdown
### 1. Deadlock / Contention Graph Analysis
```text
[Transaction T1 (PID: 1042)] --Holds (Exclusive Row Lock R_1)--> [Resource 1]
    ^                                                               |
    | Waits For Lock R_2                                            | Waits For Lock R_1
    |                                                               v
[Resource 2] <--Holds (Exclusive Row Lock R_2)-- [Transaction T2 (PID: 1088)]
```

### 2. Root Cause & Code Analysis
- **Execution Path A**: `OrderService.processOrder()` (line 42) acquires Lock `User(10)` then Lock `Account(20)`.
- **Execution Path B**: `BillingService.processRefund()` (line 88) acquires Lock `Account(20)` then Lock `User(10)`.
- **Lock Type**: Exclusive Row-Level Lock (`SELECT FOR UPDATE`).

### 3. Application & SQL Refactoring Solution
#### Application Code Refactoring (Deterministic Lock Ordering)
```java
// Refactored to enforce deterministic ID sorting before locking
public void processBatch(List<Long> entityIds) {
    // Sort IDs to guarantee consistent lock acquisition order across all threads
    List<Long> sortedIds = entityIds.stream().sorted().collect(Collectors.toList());
    for (Long id : sortedIds) {
        repository.findAndLockById(id);
    }
}
```

#### SQL Schema / Query Optimization
```sql
-- Missing index causing table scan lock escalation
CREATE INDEX CONCURRENTLY idx_orders_user_status ON orders (user_id, status);
```
```

## Evaluation Criteria
- **Graph Accuracy**: Correctly parses transaction logs and extracts the exact circular wait-for dependency graph.
- **Resolution Soundness**: Proposed code refactoring completely eliminates deadlock probability under concurrent load.
- **Performance Preservation**: Avoids throughput degradation by preferring fine-grained locks or optimistic versioning over global coarse locks.

## Failure Considerations
- **Band-Aid Timeout Fixes**: Recommending raising lock wait timeouts (`innodb_lock_wait_timeout`) without resolving the underlying lock cycle.
- **Blind Sleep Injection**: Adding arbitrary `Thread.sleep()` delays instead of fixing lock ordering logic.
