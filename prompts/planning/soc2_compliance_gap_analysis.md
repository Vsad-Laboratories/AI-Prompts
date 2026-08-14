# Planning Prompt: SOC2 Compliance Gap Analysis

## Purpose
Analyze organization-wide technical controls, policies, and workflows to identify gaps in achieving SOC 2 Type II compliance (Trust Services Criteria).

## Inputs
- `CURRENT_SECURITY_POLICIES`: Textual outlines of existing access control, encryption, monitoring, incident response, and change management procedures.
- `ORGANIZATION_INFRASTRUCTURE_METADATA`: Cloud providers, database setups, CI/CD tools, and workforce management mechanisms in use.

## Instructions
1. Audit `CURRENT_SECURITY_POLICIES` and `ORGANIZATION_INFRASTRUCTURE_METADATA` against the SOC 2 Trust Services Criteria (Security, Availability, Processing Integrity, Confidentiality, Privacy).
2. Identify security gaps, such as lack of multi-factor authentication (MFA), incomplete audit trails, or missing vulnerability scan pipelines.
3. Assess the operational maturity of current monitoring mechanisms (SIEM, log forwarding, alerts).
4. Develop remediation recommendations for each identified gap, providing code, tool, or process specifications.
5. Create a timeline and priority queue to achieve auditing readiness.

## Constraints
- Recommendations must be realistically actionable for the specified organization scale.
- Do not propose high-cost proprietary software where open-source or native cloud controls are equally effective.

## Expected output
- **SOC 2 Criteria Gap Assessment**: Exhaustive list of gaps categorized by Trust Services Criteria.
- **Remediation Action Plan**: Step-by-step security upgrades, tool recommendations, or policy rewrites.
- **Technical Implementation Templates**: Example configurations or policies for continuous evidence collection.
- **Audit Readiness Timeline**: Prioritized critical-path roadmaps (Phase 1 to Phase 3).
