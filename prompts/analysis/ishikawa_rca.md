# Analysis Prompt: Root Cause Analysis and Ishikawa Diagrammer

## Purpose
Structure a systematic Root Cause Analysis (RCA) using an Ishikawa (Fishbone) model to map, analyze, and resolve serious operational or process failures.

## Inputs
- `INCIDENT_REPORT`: Detailed narrative of an outage, defect, or process breakdown.
- `KNOWN_CONSTRAINTS`: Any environmental, technical, or structural boundary conditions.

## Instructions
1. Read the `INCIDENT_REPORT` to identify the central failure event (the "Head of the Fish").
2. Systematically map contributing factors across the standard 6 Ishikawa categories:
   - **Methods**: Operating processes, policies, or workflows.
   - **Machines**: Tech stack, hosting, databases, tooling.
   - **Materials**: Code, data formats, configurations, third-party integrations.
   - **Measurements**: Metrics, alert configurations, dashboards, QA checks.
   - **Mother Nature**: Environmental factors, physical constraints, external shocks.
   - **Manpower**: Training, communications, staffing levels, human error.
3. Apply the "5 Whys" methodology to the primary root causes discovered under these categories to drill down to fundamental flaws.
4. Construct an actionable containment and remediation plan.

## Constraints
- Do not let the analysis settle for superficial human error; seek systemic, process-level root causes under "Manpower" and "Methods."
- Every remediation action must correspond directly to an identified root cause.

## Expected output
- **Ishikawa Categories Map**: Grouped list of contributing factors for each of the 6 areas.
- **5 Whys Deep-Dive**: Lineage of cascading root causes for the top 2-3 factors.
- **Root Cause Verdict**: Concise definition of the actual underlying systemic flaw.
- **Corrective Action Plan**: Near-term containment actions and permanent preventative measures.
