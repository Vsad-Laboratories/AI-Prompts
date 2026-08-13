# Planning Prompt: Cost Optimization and FinOps Planner

## Purpose
Analyze cloud architecture, service usage logs, or invoice bills to plan concrete cloud cost reductions (FinOps) without degrading system performance or reliability.

## Inputs
- `CLOUD_INVOICE_AND_RESOURCES`: List of instances, storage volumes, database sizing, cloud provider bills, or resource usage percentages.
- `PERFORMANCE_REQUIREMENTS`: Target SLAs, latency requirements, or traffic profiles.

## Instructions
1. Review the list of `CLOUD_INVOICE_AND_RESOURCES` and identify major cost drivers and under-utilized assets (e.g., CPU utilization < 5%, unattached storage volumes).
2. Apply FinOps and Cloud Optimization best practices to categorize savings opportunities:
   - **Right-sizing**: Sizing down under-utilized virtual machines or databases.
   - **Lifecycle Management**: Moving old, infrequently-accessed data to cheaper archival tiers.
   - **Commitments & Spot**: Recommending savings plans, reserved instances, or spot instances for stateless workloads.
   - **Orphan Cleanup**: Deleting unused load balancers, elastic IPs, or unattached disk snapshots.
3. Quantify the estimated monthly and annual savings for each optimization recommendation.
4. Construct a phased implementation roadmap (Immediate, Medium Term, Long Term) prioritised by ease of implementation vs. financial savings.

## Constraints
- Never recommend cost cuts that violate the specified `PERFORMANCE_REQUIREMENTS` or compromise basic system security.
- Clearly note any upfront migration effort, downtime risks, or vendor commitment penalties.

## Expected output
- **FinOps Waste Audit Sheet**: Line items of identified waste, current cost, and potential savings.
- **Resource Optimization Matrix**: Detailed actionable optimization steps for each candidate.
- **Phased Implementation Roadmap**: Step-by-step rollout plan with risk/reward analysis.
- **Automated Cost-Guardrail Rules**: Policy scripts or monitoring alerts to prevent future cost creep.
