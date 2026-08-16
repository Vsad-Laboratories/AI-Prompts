# Planning Prompt: Multi-Cloud High-Availability & Disaster Recovery Planner

## Purpose
Design multi-cloud disaster recovery (DR) plans and active-passive or active-active failover strategies to guarantee strict Recovery Point Objectives (RPO) and Recovery Time Objectives (RTO).

## Inputs
- `CRITICAL_SERVICES`: List of core application workloads, databases, and dependencies.
- `TARGET_RPO_RTO`: RPO (e.g., RPO < 1 minute) and RTO (e.g., RTO < 15 minutes) targets.
- `PRIMARY_SECONDARY_PROVIDERS`: Target primary and secondary cloud providers (e.g., AWS primary, GCP secondary).

## Instructions
1. Assess `CRITICAL_SERVICES` data persistence and synchronization requirements across cloud provider boundaries.
2. Formulate cross-cloud data replication strategies (e.g., asynchronous database streaming, continuous block replication).
3. Design global traffic management and DNS failover mechanisms (e.g., Route53 / Cloudflare health check failovers).
4. Define explicit step-by-step failover execution playbooks for engineering incident response teams.
5. Construct a failback verification protocol to restore primary operations safely after incident resolution.

## Constraints
- Explicitly detail cross-cloud egress data costs and bandwidth latency limits.
- Address identity and access management (IAM) synchronization across differing cloud IAM models.

## Expected output
- **DR Architecture Blueprint**: High-availability multi-cloud data and compute topology.
- **Automated Failover Playbook**: Sequential incident response steps and DNS routing changes.
- **RPO/RTO & Cost Analysis**: Theoretical verification of recovery timelines and infrastructure overhead cost.
