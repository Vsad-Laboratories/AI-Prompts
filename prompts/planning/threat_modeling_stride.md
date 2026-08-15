# Planning Prompt: STRIDE Cybersecurity Threat Modeling Framework

## Purpose
Systematically identify, categorize, and formulate mitigation strategies for application security threats using the STRIDE threat modeling framework (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, Elevation of Privilege).

## Inputs
- `SYSTEM_ARCHITECTURE`: Technical system design, network boundaries, API endpoints, data flow diagrams, or architecture descriptions.
- `DATA_CLASSIFICATION`: Sensitivity levels of stored and transit data (e.g., PII, Payment Data, Internal Telemetry).
- `TRUST_BOUNDARIES`: Networks, auth barriers, or process isolation boundaries crossing system components.

## Instructions
1. Analyze `SYSTEM_ARCHITECTURE` to identify assets, entry points, data flows, and `TRUST_BOUNDARIES`.
2. Evaluate potential attack vectors systematically against the 6 STRIDE threat categories:
   - **Spoofing**: Authentication bypasses and identity impersonation risks.
   - **Tampering**: Data modification in transit or at rest without authorization.
   - **Repudiation**: Inadequate logging or audit trails permitting denial of actions.
   - **Information Disclosure**: Unauthorized data leaks or encryption weaknesses.
   - **Denial of Service**: Resource exhaustion, unthrottled endpoints, or algorithmic bottlenecks.
   - **Elevation of Privilege**: Authorization flaws permitting unprivileged account escalation.
3. Assign risk severity ratings (High/Medium/Low) based on impact and exploit probability.
4. Formulate specific engineering mitigations for each identified threat.

## Constraints
- Evaluate threats crossing explicit `TRUST_BOUNDARIES` rather than generic vague security advice.
- Avoid recommending generic security tools without detailing specific code or configuration changes.

## Expected output
- **System Entry Point & Trust Boundary Map**: Overview of attack surfaces.
- **STRIDE Threat Inventory Matrix**: Comprehensive table detailing threat vectors, affected components, and severity.
- **Actionable Mitigations Roadmap**: Concrete security engineering controls and remediation steps.
