# FinOps Cloud Cost Anomaly Analyzer

## Purpose
Examine multi-cloud usage metrics, billing telemetry logs, infrastructure resource utilization spikes, and service invoice line items to isolate, diagnose, quantify, and remediate unexpected cost anomalies and cloud spending waste.

## Inputs
- `TELEMETRY_BILLING_LOGS`: Raw cost and usage report (CUR) items, metric spikes (EC2, S3, Kubernetes pod allocations, egress bandwidth, database IOPS).
- `EXPECTED_BASELINE_BUDGET`: Standard monthly budget, expected growth thresholds, historical spending baselines.
- `CLOUD_ENVIRONMENT_SPECS`: Provider details (AWS/GCP/Azure), instance types, pricing models (On-Demand, Savings Plans, Reserved Instances, Spot).

## Instructions
1. **Detect Cost Anomalies**: Compare `TELEMETRY_BILLING_LOGS` against `EXPECTED_BASELINE_BUDGET`. Identify resource categories exhibiting cost growth exceeding standard baseline variance (>15% variance).
2. **Isolate Anomaly Drivers**: Pinpoint specific cloud services, resource IDs, regions, availability zones, cluster namespaces, or tag keys driving the spending surge.
3. **Categorize Root Cause**: Classify identified cost anomalies into FinOps operational root cause categories:
   - *Zombie / Abandoned Resources* (unattached EBS volumes, idle ELBs, unassociated Elastic IPs).
   - *Overprovisioned Compute/Database* (oversized EC2/RDS instances running at <5% CPU utilization).
   - *Cross-AZ / Data Egress Spikes* (unexpected inter-region traffic or NAT Gateway data transfer surges).
   - *Sub-Optimal Purchasing Options* (running steady-state production workloads on 100% On-Demand pricing instead of Reserved Instances/Savings Plans).
   - *Misconfigured Storage Lifecycle* (storing petabytes of uncompressed log files on S3 Standard without Glacier transition rules).
4. **Quantify Financial Impact**: Calculate total wasted spend ($ USD) per day/month and forecast annualized runaway cost if unmitigated.
5. **Formulate Prioritized Remediation Strategy**: Generate actionable, low-risk engineering remediation steps categorized by implementation effort (Immediate / Medium-Term / Architectural).

## Constraints
- **Preserve System Reliability**: Remediation recommendations MUST NOT compromise high availability, failover redundancy, or performance SLAs.
- **Provide Dollar Quantifications**: Every cost savings proposal MUST cite estimated monthly savings ($) and percentage reduction.
- **Traceable Attribution**: Reference explicit Resource IDs, Account IDs, and Service Names in diagnostic outputs.

## Expected Output Format
```markdown
### 1. Cost Anomaly Executive Summary
- **Total Anomaly Spend**: $[Amount] USD / month above baseline
- **Primary Driver**: [Service Name / Resource Category]
- **Runaway Cost Risk**: $[Annualized Amount] USD / year

### 2. Anomaly Breakdown Matrix
| Resource ID / Service | Region / Account | Baseline Spend | Anomaly Spend | Variance (%) | Identified Root Cause |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `i-0a123bc456def789` | us-east-1 | $120/mo | $1,850/mo | +1441% | Overprovisioned r5b.8xlarge at 2% CPU |

### 3. Actionable FinOps Remediation Plan
#### Immediate Actions (Zero Risk / Low Effort)
- [ ] **Action**: [Specific CLI or IaC terraform change]
  - **Estimated Savings**: $[Amount]/mo

#### Medium-Term Architectural Optimizations
- [ ] **Action**: [Lifecycle rule / Spot integration / Rightsizing]
  - **Estimated Savings**: $[Amount]/mo
```

## Evaluation Criteria
- **Diagnostic Precision**: Pinpoints exact resource IDs and telemetry events responsible for cost spikes.
- **ROI Accuracy**: Provides realistic, mathematically sound cost reduction estimates.
- **Risk Awareness**: Evaluates performance trade-offs prior to recommending instance rightsizing or termination.

## Failure Considerations
- **Generic Cost Advice**: Recommending generic "buy savings plans" without analyzing actual workload steady-state metrics.
- **Destructive Rightsizing**: Advising compute downsizing for burstable workloads that require peak headroom.
