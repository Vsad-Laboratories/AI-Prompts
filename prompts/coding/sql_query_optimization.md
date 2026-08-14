# Coding Prompt: SQL Query Optimization

## Purpose
Optimize slow-running SQL queries by analyzing their execution plans, indexing strategies, table structures, and rewrite opportunities to achieve maximum efficiency and minimal resource utilization.

## Inputs
- `RAW_SQL_QUERY`: The SQL query experiencing performance degradation.
- `TABLE_SCHEMA_AND_INDEXES`: Schema definition of the involved tables, along with existing index setups and approximate row counts.
- `DATABASE_ENGINE`: The target database platform (e.g., PostgreSQL, MySQL, Oracle, MS SQL Server).

## Instructions
1. Analyze the structure of `RAW_SQL_QUERY` for common anti-patterns such as unnecessary subqueries, inefficient joins (e.g., joining on unindexed columns), wildcard selectors (SELECT *), or functions applied on indexed columns.
2. Formulate optimization theories focusing on how the specified `DATABASE_ENGINE` processes joins, aggregates, and where clauses.
3. Recommend new indexes (e.g., composite, partial, or covering indexes) to facilitate faster scans.
4. Rewrite the query to use modern, performant alternatives (e.g., replacing subqueries with CTEs, or IN clauses with EXISTS if suitable).
5. Compare the resource consumption expectations of the original query vs. the optimized query.

## Constraints
- Do not suggest indexing strategies that could severely degrade write performance without warning.
- The output SQL must be fully compatible with the chosen `DATABASE_ENGINE`.

## Expected output
- **SQL Anti-Pattern Diagnostics**: Clear identification of why the current query is slow.
- **Recommended Schema/Index Optimizations**: Actionable DDL statements for creating performant indexes.
- **Optimized SQL Rewrite**: The rewritten, highly performance-tuned SQL query.
- **Performance Trade-Off Analysis**: Estimated read speedups vs. potential write overhead.
