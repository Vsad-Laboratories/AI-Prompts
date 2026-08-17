# Incident Postmortem Action Item & Remediation Tracker

## Purpose
Synthesize blameless incident postmortem notes, root cause analyses, operational incident logs, and post-incident review transcripts into prioritized, actionable engineering remediation trackers with strict SLAs, service ownership tags, and completion verification criteria.

## Inputs
- `INCIDENT_POSTMORTEM_TEXT`: Executive postmortem document, timeline, 5-Whys root cause analysis, telemetry graphs, and chat transcript logs.
- `SERVICE_OWNERSHIP_CATALOG`: Codebase service inventory, engineering team assignments, microservice owners.
- `REMEDIATION_SLA_POLICY`: Corporate SLA resolution rules (e.g., P0 Blockers due in 48 hours, P1 High due in 2 weeks, P2 Medium due in 1 sprint).

## Instructions
1. **Analyze Root Cause & Contributing Factors**: Extract the primary technical root cause and secondary contributing systemic flaws from `INCIDENT_POSTMORTEM_TEXT`.
2. **Categorize Action Items by Reliability Hierarchy**:
   - **P0 - Root Cause Elimination**: Direct structural code, infrastructure, or architecture fixes preventing identical failure re-occurrence.
   - **P1 - Detection & Observability**: Synthetic probes, telemetry alerts, dashboard metrics, and logging improvements to reduce Time-To-Detect (TTD).
   - **P2 - Blast Radius Mitigation**: Circuit breakers, rate limiters, health check adjustments, and automated failover mechanics to reduce Time-To-Mitigate (TTM).
   - **P3 - Process & Runbook Documentation**: Runbook updates, automated testing enhancements, and disaster recovery tabletop exercises.
3. **Draft Measurable Acceptance Criteria**: Ensure every action item includes explicit, testable completion criteria (e.g., "Add automated integration test covering 404 response path in CI/CD pipeline").
4. **Assign Service Ownership & Due Window**: Map action items to microservices in `SERVICE_OWNERSHIP_CATALOG` and assign due dates based on `REMEDIATION_SLA_POLICY`.

## Constraints
- **Zero Vague Action Items**: Ban generic phrases like "Improve testing" or "Monitor DB better". Require explicit technical tasks with verifiable acceptance criteria.
- **Strict Blameless Phrasing**: Frame action items around system design, missing automation, and tooling gaps rather than individual human errors.
- **Traceable Root Cause Linkage**: Every action item MUST directly map to a specific contributing factor identified in the postmortem.

## Expected Output Format
```markdown
### 1. Incident Remediation Executive Summary
- **Incident ID**: `INC-8942`
- **Impacted Service**: Payments Processing Pipeline
- **Primary Root Cause**: Unindexed database query executed during peak load caused thread pool exhaustion.
- **Total Action Items**: [N] (P0: [N], P1: [N], P2: [N])

### 2. Action Item Remediation Tracker
| Item ID | Category | Technical Description & Acceptance Criteria | Priority | SLA Due Window | Assigned Owner / Team |
| :--- | :--- | :--- | :--- | :--- | :--- |
| `ACT-01` | Root Cause Fix | Add composite index `(user_id, status)` on `orders` table and deploy migration via Liquibase. **Acceptance**: Query execution plan shows Index Scan, duration <5ms. | P0 | 48 Hours | @payments-platform |
| `ACT-02` | Observability | Create Datadog monitor triggering PagerDuty alert when DB thread pool utilization exceeds 80% for 2 mins. **Acceptance**: Synthetic test triggers alert successfully. | P1 | 14 Days | @observability-team |

### 3. Verification & Follow-Up Protocol
- **Post-Remediation Review Date**: [Date 30 days post-incident]
- **Verification Owner**: Staff Site Reliability Engineer (@sre-lead)
```

## Evaluation Criteria
- **Actionability**: Every action item is concrete, unambiguous, and assigned to a clear team owner.
- **Root Cause Alignment**: Action items directly address identified failure modes rather than superficial symptoms.
- **Verification Precision**: Acceptance criteria allow clear binary (pass/fail) verification during audits.

## Failure Considerations
- **Superficial Action Items**: Creating purely administrative tasks without engineering code/system fixes.
- **Orphaned Items**: Generating action items without assigned team owners or SLA due dates.
