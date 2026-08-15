# Writing Prompt: Blameless Incident Postmortem Generator

## Purpose
Synthesize incident timelines, IRC/Slack chat logs, telemetry graphs, and post-incident review notes into an executive, blameless engineering postmortem document focused on systemic prevention.

## Inputs
- `INCIDENT_LOGS`: Timestamps, incident chat transcripts, pager duty alerts, and metric graphs.
- `AFFECTED_SERVICES`: Impacted customer-facing systems, SLA/SLO breach durations, and business impact.
- `ROOT_CAUSE_FINDINGS`: Technical findings explaining the underlying cause of the failure.

## Instructions
1. Construct an **Executive Incident Summary**: High-level overview detailing incident severity, total downtime, customer impact, and primary cause.
2. Build a precise, chronological **Incident Timeline** mapping key event triggers, detection timestamps, escalation decisions, and mitigation actions.
3. Conduct a **Blameless Root Cause Analysis**: Focus strictly on underlying engineering flaws, missing automated alerts, or system fragile points, avoiding individual fault.
4. Detail **What Went Well**, **What Went Poorly**, and **Where We Got Lucky** during the response cycle.
5. Formulate a prioritized list of **Preventative Action Items (CAPA)** tagged by owner, ticket link, and target completion date.

## Constraints
- Strictly enforce a blameless culture: attribute failure to missing guardrails, test coverage gaps, or system complexity rather than human operator error.
- Ensure all action items are concrete, measurable engineering tasks rather than vague intentions.

## Expected output
- **Executive Postmortem Header**: Metadata block detailing impact, SLA breach, and downtime.
- **Chronological Event Timeline**: Timestamped log of the incident response.
- **Systemic Root Cause Breakdown**: Deep technical explanation of failure mechanism.
- **Actionable Preventive Backlog**: Prioritized engineering fixes to prevent recurrence.
