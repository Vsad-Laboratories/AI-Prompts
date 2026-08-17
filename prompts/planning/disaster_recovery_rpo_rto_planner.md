# Disaster Recovery (BCDR), RPO & RTO Planner

## Purpose
Formulate a comprehensive Business Continuity and Disaster Recovery (BCDR) architectural plan for enterprise cloud services, defining explicit Recovery Point Objectives (RPO), Recovery Time Objectives (RTO), cross-region failover automation, database replication models, and operational recovery playbooks.

## Inputs
- `CRITICAL_SERVICES_CATALOG`: List of core applications, datastores, dependencies, tier classifications (Tier 0 Mission Critical, Tier 1 Core Business, Tier 2 Non-Critical).
- `TARGET_RPO_RTO_SLA`: Maximum allowable data loss duration (RPO) and maximum allowable downtime duration (RTO) per tier.
- `PRIMARY_SECONDARY_REGION_SPECS`: Primary production cloud region and secondary DR target region (e.g., AWS `us-east-1` primary $\rightarrow$ `us-west-2` secondary DR).

## Instructions
1. **Define Service Tiering Matrix**: Categorize services in `CRITICAL_SERVICES_CATALOG` into standardized DR tiers:
   - **Tier 0 (Mission Critical)**: $\text{RPO} \le 1 \text{ minute}, \text{RTO} \le 15 \text{ minutes}$ (Active-Active multi-region or Pilot Light with automated DNS failover).
   - **Tier 1 (Core Business)**: $\text{RPO} \le 15 \text{ minutes}, \text{RTO} \le 2 \text{ hours}$ (Warm Standby / pilot light).
   - **Tier 2 (Non-Critical)**: $\text{RPO} \le 24 \text{ hours}, \text{RTO} \le 24 \text{ hours}$ (Cold Standby / backup-and-restore).
2. **Architect Datastore Replication Strategies**:
   - **Relational Databases (PostgreSQL / MySQL)**: Configure asynchronous/synchronous cross-region read replicas with automated promotion.
   - **NoSQL / Key-Value Stores**: Configure multi-region global tables (DynamoDB Global Tables / CockroachDB).
   - **Object / Block Storage (S3 / EBS)**: Configure S3 Cross-Region Replication (CRR) and automated EBS snapshot lifecycle policies.
3. **Architect Automated Network & DNS Traffic Failover**:
   - Design Route 53 / Cloudflare health check probes, latency-based routing, and DNS failover record switching.
   - Define ingress traffic rerouting, TLS certificate synchronization, and global load balancer target group switching.
4. **Construct Disaster Recovery Runbook Playbook**:
   - **Phase 1: Incident Identification & Disaster Declaration**: Alert triggers, incident commander authority threshold.
   - **Phase 2: Failover Execution Protocol**: Sequential execution steps for database promotion, compute autoscaling, and DNS cutover.
   - **Phase 3: Integrity Verification**: Automated sanity test suites and data consistency validation before routing user traffic.
   - **Phase 4: Fallback / Failback Protocol**: Re-synchronizing data changes back to primary region once primary infrastructure is restored.
5. **Establish DR Testing Schedule & Tabletop Exercises**: Define bi-annual simulated failover exercises, chaotic region isolation tests (Chaos Engineering), and automated disaster drill frameworks.

## Constraints
- **Explicit Target Compliance**: Replication mechanics MUST mathematically satisfy assigned RPO/RTO time targets.
- **Split-Brain Mitigation**: Failover runbooks MUST include explicit fencing mechanics to prevent dual-primary write brain split during network partition events.
- **Cost vs Risk Optimization**: Balance multi-region active-active deployment costs against business downtime impact.

## Expected Output Format
```markdown
### 1. Service Tiering & RPO/RTO SLA Matrix
| Service Name | Category | Service Tier | Target RPO | Target RTO | Failover Architecture Model |
| :--- | :--- | :--- | :--- | :--- | :--- |
| Auth & User DB | Core Data | Tier 0 | < 1 min | < 15 min | Active-Active Multi-Region |
| Billing Pipeline | Processing | Tier 1 | < 15 min | < 2 hrs | Warm Standby (Pilot Light) |

### 2. Cross-Region Datastore & Ingress Failover Architecture
- **Database Replication**: PostgreSQL Aurora Global Database (Primary: `us-east-1`, Secondary Replica: `us-west-2`, replication lag < 1 sec).
- **DNS Failover Mechanics**: AWS Route 53 Health Checks evaluating `/healthz` endpoint every 10 seconds. Automated failover triggered after 3 consecutive failures.

### 3. Step-by-Step Failover Runbook (Phase 2 Execution)
```bash
# Step 1: Promote Secondary Database Replica to Primary Master
aws rds promote-read-replica --db-instance-identifier rds-us-west-2-dr

# Step 2: Scale Compute Target Groups in Secondary Region
aws autoscaling set-desired-capacity --auto-scaling-group-name dr-asg-west --desired-capacity 50

# Step 3: Trigger Route 53 DNS Cutover
aws route53 change-resource-record-sets --hosted-zone-id Z123456 --change-batch file://dns_cutover.json
```

### 4. Split-Brain Defense & Integrity Sanity Checks
- **Fencing Mechanism**: Revoke write IAM credentials on primary database endpoint prior to promoting secondary replica.
- **Sanity Verification Script**: Run automated smoke test suite `pytest tests/dr_smoke_tests.py` verifying API status and database read/write checks.
```

## Evaluation Criteria
- **RPO/RTO Feasibility**: Technical replication mechanics satisfy assigned recovery time objective limits.
- **Runbook Actionability**: Steps provide copy-paste CLI commands and clear operational sequence.
- **Split-Brain Defense**: Includes explicit mechanisms to isolate primary datastores before secondary promotion.

## Failure Considerations
- **Ignoring Data Return (Failback)**: Planning regional failover without defining how to sync newly written data back to the primary region after recovery.
- **Unverified Backup Restoration**: Assuming backups work without testing automated restoration pipelines.
