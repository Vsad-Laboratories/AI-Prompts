# Analysis Prompt: Enterprise Compliance & Security Control Auditor

## Purpose
Audit organizational workflows, codebase configurations, and infrastructure-as-code (IaC) definitions against regulatory security compliance frameworks (SOC2, ISO 27001, HIPAA, GDPR).

## Inputs
- `COMPLIANCE_FRAMEWORK`: Target regulatory standard or compliance framework.
- `SYSTEM_SPECIFICATION`: Policies, IaC templates, access control configurations, or architecture documents to audit.

## Instructions
1. Map `SYSTEM_SPECIFICATION` controls directly against mandatory criteria in `COMPLIANCE_FRAMEWORK`.
2. Conduct a gap analysis identifying non-compliant settings, missing audit trails, insufficient encryption, or excessive privileges.
3. Assign severity ratings (Critical, High, Medium, Low) to each identified compliance deficiency.
4. Formulate specific technical remediation guidance for each failing control.
5. Generate an executive readiness score and audit checklist.

## Constraints
- Must evaluate both technical controls (e.g., encryption at rest) and administrative controls (e.g., access review schedules).
- Provide explicit framework control code mappings (e.g., SOC2 CC6.1, ISO 27001 A.12.6.1).

## Expected output
- **Executive Audit Summary**: Compliance score, overall risk posture, and summary of critical findings.
- **Compliance Matrix**: Control-by-control audit results table mapping requirement to implementation status.
- **Remediation Action Plan**: Prioritized technical fix recommendations with target completion timelines.
