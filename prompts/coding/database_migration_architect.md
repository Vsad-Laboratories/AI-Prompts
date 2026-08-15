# Coding Prompt: Database Schema Migration & Zero-Downtime Planner

## Purpose
Design high-performance database schema migrations (SQL/NoSQL) executed under zero-downtime constraints on high-throughput production systems.

## Inputs
- `CURRENT_SCHEMA`: Existing database table/collection structure and index configurations.
- `TARGET_SCHEMA`: Desired updated schema structure.
- `DATABASE_ENGINE`: Database technology (e.g., PostgreSQL, MySQL, MongoDB, DynamoDB).
- `TRAFFIC_PROFILE`: Read/write volume, table size, and lock sensitivity parameters.

## Instructions
1. Analyze structural differences between `CURRENT_SCHEMA` and `TARGET_SCHEMA`.
2. Formulate a multi-phase **Expand-Contract Migration Strategy** (e.g., Add new column -> Dual-write in code -> Backfill historical data -> Switch reads -> Remove legacy column).
3. Draft raw, production-grade SQL/NoSQL DDL scripts for each phase, explicitly utilizing non-blocking migration patterns (e.g., `CREATE INDEX CONCURRENTLY` in Postgres).
4. Identify locking hazards, long-running transaction risks, and foreign key constraint locks.
5. Provide rollback DDL scripts and data reconciliation verification queries for each phase.

## Constraints
- Avoid exclusive table locks on production tables with millions of rows.
- Never issue single-step column renames or data type changes on live production databases.

## Expected output
- **Multi-Phase Migration Roadmap**: Phased sequence for application and schema updates.
- **Production DDL Scripts**: Executable SQL/NoSQL scripts for each migration phase.
- **Rollback & Recovery Scripts**: Safe revert procedures for emergency aborts.
- **Data Backfill & Verification Queries**: Integrity verification queries.
