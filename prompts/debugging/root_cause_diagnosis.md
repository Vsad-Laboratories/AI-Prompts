# Debugging Prompt: Systemic Root-Cause Diagnosis

## Purpose
Guide an engineer through diagnosing a complex, intermittent, or systemic software bug, focusing on isolating the bug rather than guessing at fixes.

## Inputs
- `BUG_DESCRIPTION`: Symptoms, error traces, and user reports.
- `SYSTEM_ARCHITECTURE`: Technologies, databases, networks, or microservices involved.

## Instructions
1. Analyze the `BUG_DESCRIPTION` and `SYSTEM_ARCHITECTURE`.
2. Map the path of data flow and execution during the failure. Identify all systems or interfaces where the failure could have originated.
3. Establish 3 distinct hypotheses for the root cause of the bug.
4. For each hypothesis, design a **Diagnostic Test** or log query that would prove or disprove that hypothesis with 100% certainty.
5. Create a step-by-step troubleshooting tree: "If test A is positive, investigate system X; if negative, investigate system Y."

## Constraints
- Do not propose code fixes until a diagnostic test has successfully isolated the root cause.
- Focus heavily on boundary conditions, race conditions, network failures, or database locks.

## Expected output
- **Fault-Boundary Analysis**: Map of failure propagation across the system architecture.
- **Differential Diagnosis Table**: Hypotheses, probability, impact, and required test.
- **Isolation Walkthrough**: Explicit steps to safely test hypotheses in a development/staging environment.
- **Permanent Remediation Strategy**: Steps to ensure this bug is permanently caught by unit tests or CI monitoring.
