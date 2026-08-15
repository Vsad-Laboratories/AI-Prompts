# Planning Prompt: Infrastructure & Distributed Systems Capacity Planner

## Purpose
Calculate infrastructure resource requirements, compute scaling thresholds, bandwidth budgets, and storage volume growth for high-scale distributed systems over projected growth horizons.

## Inputs
- `TRAFFIC_PROJECTIONS`: Expected Daily Active Users (DAU), Requests Per Second (RPS), or transactions per minute over target growth horizons (6mo, 12mo, 36mo).
- `PAYLOAD_SIZES`: Average and peak read/write request/response sizes.
- `SLA_LATENCY_TARGETS`: Percentile latency requirements (e.g., p99 < 100ms) and availability target (e.g., 99.99%).

## Instructions
1. Calculate raw throughput and storage metrics:
   - Compute **Peak Read/Write RPS** incorporating peak-to-average traffic ratios.
   - Compute **Bandwidth Requirements** (Ingress / Egress Mbps).
   - Compute **Storage Accumulation** (Daily, Monthly, Yearly storage footprints including index overhead and duplication factor).
2. Calculate compute cluster capacity (CPU cores, RAM footprint, connection pooling boundaries) needed to maintain `SLA_LATENCY_TARGETS`.
3. Design **Database Sharding & Caching Strategy**: Estimate Redis/Memcached cache sizes based on working set memory calculations (e.g., 80/20 rule).
4. Establish horizontal auto-scaling thresholds and infrastructure cost estimates across growth milestones.

## Constraints
- Account for replication factors, backup retention copies, and index overhead in storage sizing (do not calculate raw data alone).
- Incorporate headroom margins (e.g., 30-50% safety buffer) above raw theoretical minimums.

## Expected output
- **Traffic & Bandwidth Baseline**: Detailed calculation breakdown of RPS and network I/O.
- **Storage & Memory Sizing Matrix**: Database growth and cache memory footprint requirements.
- **Compute Cluster & Sharding Architecture**: Infrastructure node recommendations and scaling triggers.
