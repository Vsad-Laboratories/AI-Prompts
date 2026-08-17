# Runbook & Standard Operating Procedure (SOP) Writer

## Purpose
Transform raw system deployment notes, infrastructure maintenance tasks, emergency failover procedures, or incident response steps into production-ready, zero-ambiguity Standard Operating Procedures (SOPs) and Runbooks equipped with validation checks, rollback commands, and safety gates.

## Inputs
- `PROCEDURE_GOAL`: Operational task objective (e.g., Database Index Rebuild, Kubernetes Cluster Upgrade, Secret Rotation).
- `TARGET_SYSTEM_ENVIRONMENT`: Environment target (Production, Staging, Multi-Region, On-Premises).
- `SAFETY_CRITICALITY_LEVEL`: Operational risk tier (Low, Medium, High Risk / Destructive Data Change).

## Instructions
1. **Define Operating Context & Prerequisites**:
   - Required IAM privileges / RBAC permissions.
   - Estimated execution time and maintenance window requirements.
   - Pre-execution cluster/system health checks.
2. **Construct Step-by-Step Execution Protocol**:
   - Every execution step MUST contain:
     - **Action Description**: What is happening and why.
     - **Execution Command**: Syntactically valid, copy-pasteable terminal command.
     - **Expected Output**: What successful stdout/stderr should look like.
     - **Validation Command**: Command verifying step completion before proceeding to the next step.
3. **Incorporate Automated Safety Gates & Rollback Protocols**:
   - For every state-mutating command, provide an explicit **Failure Trigger Condition** and **Rollback Command** restoring the prior state.
4. **Formulate Post-Execution Sanity Verification**:
   - Define end-to-end smoke test scripts verifying full service recovery.

## Constraints
- **Zero Ambiguous Commands**: Never write pseudo-commands like `sudo do_upgrade.sh`. Every command MUST be fully specified with exact flags, variable placeholders (`<PLACEHOLDER>`), and environment parameters.
- **Mandatory Verification Step**: No step may proceed without an explicit validation command.
- **Fail-Safe Rollback Gate**: Every destructive or state-altering step MUST have a tested rollback command.

## Expected Output Format
```markdown
# Runbook: Production PostgreSQL Database Zero-Downtime Index Rebuild

## 1. Prerequisites & Operational Context
- **Target Environment**: Production DB Cluster (`db-prod-us-east-1`)
- **Required Role/Privileges**: `postgres_admin` database role
- **Estimated Execution Time**: 25 Minutes
- **Safety Criticality**: MEDIUM (Non-blocking concurrently executed schema update)

### Pre-Execution Health Checks
Run the following command to verify database replica lag and CPU headroom:
```bash
psql -h <DB_HOST> -U postgres -c "SELECT client_addr, replay_lag FROM pg_stat_replication;"
```
*Expected Output*: `replay_lag` MUST be `< 00:00:05` (5 seconds) across all read replicas.

## 2. Step-by-Step Execution Protocol

### Step 1: Rebuild Index Concurrently
Execute index creation using `CONCURRENTLY` to avoid blocking concurrent write transactions.

```bash
psql -h <DB_HOST> -U postgres -d production_db -c "CREATE INDEX CONCURRENTLY IF NOT EXISTS idx_orders_user_id_v2 ON orders (user_id);"
```

**Validation Command**:
```bash
psql -h <DB_HOST> -U postgres -d production_db -c "SELECT relname, indisvalid FROM pg_class c JOIN pg_index i ON c.oid = i.indexrelid WHERE relname = 'idx_orders_user_id_v2';"
```
**Expected Output**:
```text
        relname         | indisvalid
------------------------+------------
 idx_orders_user_id_v2  | t
(1 row)
```

**Failure Trigger & Rollback Command**:
If `indisvalid` returns `f` (invalid index due to query deadlock):
```bash
# Rollback: Drop invalid index and retry during low-traffic window
psql -h <DB_HOST> -U postgres -d production_db -c "DROP INDEX CONCURRENTLY IF EXISTS idx_orders_user_id_v2;"
```

## 3. Post-Execution Sanity Verification
Run execution plan verification to confirm query optimizer utilizes new index:
```bash
psql -h <DB_HOST> -U postgres -d production_db -c "EXPLAIN ANALYZE SELECT * FROM orders WHERE user_id = 'usr_1042';"
```
*Expected Output*: Query plan displays `Index Scan using idx_orders_user_id_v2`.
```

## Evaluation Criteria
- **Command Precision**: 100% syntactically valid commands with explicit placeholders.
- **Operational Safety**: Includes pre-checks, step validation, and tested rollback procedures for every destructive step.
- **Usability Under Pressure**: Clear layout designed for rapid execution by on-call engineers.

## Failure Considerations
- **Missing Validation Commands**: Assuming commands succeeded without running explicit validation checks.
- **Destructive Commands Without Rollbacks**: Omitting rollback commands for state-altering operations.
