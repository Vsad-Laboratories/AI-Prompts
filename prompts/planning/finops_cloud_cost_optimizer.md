# Planning Prompt: FinOps Cloud Cost Reduction & Architecture Planner

## Purpose
Formulate a comprehensive FinOps cloud cost optimization roadmap to eliminate infrastructure wastage and optimize cloud spend without compromising application availability or performance.

## Inputs
- `CLOUD_BILLING_SUMMARY`: Invoice breakdowns, resource usage logs, or cloud architecture configurations (AWS, GCP, Azure).
- `TARGET_SAVINGS_PERCENTAGE`: Target cost reduction goal (e.g., 25% spend reduction).

## Instructions
1. Analyze `CLOUD_BILLING_SUMMARY` to categorize cloud spend across Compute, Storage, Networking, Database, and Serverless services.
2. Identify resource wastage patterns: idle EC2/Compute instances, unattached EBS volumes, over-provisioned RDS instances, uncompressed egress data transfer, and inefficient S3 lifecycle policies.
3. Formulate optimization strategies across three tiers:
   - Immediate Hygiene (e.g., deleting unattached disks, downsizing idle instances).
   - Rate Optimization (e.g., Reserved Instances, Savings Plans, Spot instance conversion).
   - Architectural Refactoring (e.g., auto-scaling policies, serverless migration, cold storage tiering).
4. Quantify estimated monthly savings and implementation effort for each action item.
5. Create a phased FinOps execution roadmap with engineering priorities.

## Constraints
- Ensure cost savings recommendations do not breach high-availability (HA) SLAs or single-point-of-failure limits.
- Account for upfront costs or lock-in risks of long-term Savings Plans.

## Expected output
- **Spend Breakdown & Wastage Audit**: Categorized spending summary and highlighted waste.
- **FinOps Action Matrix**: Cost savings vs engineering effort evaluation table.
- **Phased Implementation Roadmap**: Step-by-step rollout plan with projected ROI.
