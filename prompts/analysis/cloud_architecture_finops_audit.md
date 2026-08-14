# Analysis Prompt: Cloud Architecture FinOps Audit

## Purpose
Analyze cloud resource utilization and service bills to identify wastage, evaluate cost efficiency, and formulate cloud cost optimization strategies.

## Inputs
- `CLOUD_UTILIZATION_REPORTS`: Storage usage, compute CPU/memory graphs, network data transfer logs, and database metrics.
- `MONTHLY_BILLING_EXPORT`: A line-item breakdown of monthly cloud expenses, categorized by service and region.

## Instructions
1. Cross-reference `CLOUD_UTILIZATION_REPORTS` with `MONTHLY_BILLING_EXPORT` to find underutilized or idle resources (e.g., oversized VM instances, unattached disks, over-provisioned databases).
2. Evaluate potential cost-saving purchase options (e.g., Reserved Instances, Savings Plans, Spot instances) vs. on-demand rates.
3. Identify data egress hotspots and regional storage mismatches.
4. Formulate architectural cost-saving patterns (e.g., serverless autoscale setups, lifecycle rules for cold storage).
5. Estimate the overall financial ROI of the suggested FinOps transformations.

## Constraints
- Never compromise system reliability or application SLOs (Service Level Objectives) to achieve cost reductions.
- Do not suggest migration of legacy systems to different clouds unless cost savings are thoroughly quantified.

## Expected output
- **Cloud Resource Waste Inventory**: Prioritized list of idle, oversized, or unmapped cloud assets.
- **Pricing Strategy Optimization Matrix**: Detailed comparison of purchase commitments (RI, Savings Plans, Spot).
- **Architectural Cost-Savings Plan**: Step-by-step optimization recommendations with zero downtime.
- **ROI Impact Forecast**: Projected monthly savings estimates with implementation effort ratings.
