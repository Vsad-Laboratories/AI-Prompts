# Planning Prompt: Major Incident Command & Escalation Playbook Planner

## Purpose
Establish an Incident Command System (ICS) playbook and automated escalation matrix for enterprise engineering teams responding to major severity outages (Sev-0 / Sev-1).

## Inputs
- `ORGANIZATION_STRUCTURE`: Team composition, on-call rotation frameworks, and service ownership maps.
- `INCIDENT_SEVERITY_LEVELS`: SLA guidelines and outage impact definitions (Sev-0 to Sev-3).

## Instructions
1. Define explicit Incident Command System roles: Incident Commander (IC), Communications Lead, Operations Lead, and Subject Matter Experts (SMEs).
2. Formulate triage and severity classification rules to rapidly establish incident level.
3. Design clear internal and external communication cadences (e.g., status page updates every 15 mins for Sev-0).
4. Establish automated escalation protocols when incident response stalls or diagnostic thresholds exceed SLA limits.
5. Create post-incident transition procedures initiating blameless postmortems and remediation tracking.

## Constraints
- Keep communication templates concise and blameless; avoid ambiguous incident severity definitions.
- Ensure clear single-point-of-authority principles (the Incident Commander has absolute operational authority during incidents).

## Expected output
- **Incident Command Role Definitions**: Standardized duties and decision authority boundaries.
- **Severity & Triage Decision Matrix**: Step-by-step rules for incident classification.
- **Communication & Status Templates**: Pre-drafted internal/external update messaging formats.
- **Escalation & Handoff Playbook**: Time-bound escalation trees and rotation handoff rules.
