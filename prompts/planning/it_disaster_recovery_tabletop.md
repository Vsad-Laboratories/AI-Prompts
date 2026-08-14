# Planning Prompt: IT Disaster Recovery Tabletop

## Purpose
Design, coordinate, and evaluate a realistic IT disaster recovery tabletop simulation to test engineering readiness, response plans, and service restoration speed.

## Inputs
- `SYSTEM_ARCHITECTURE_SPECS`: Core cloud resources, backup structures, failover capabilities, and database setups.
- `ACTIVE_DISASTER_RECOVERY_POLICY`: Defined recovery time objectives (RTO), recovery point objectives (RPO), and communication structures.

## Instructions
1. Analyze `SYSTEM_ARCHITECTURE_SPECS` to identify high-impact failure scenarios (e.g., total regional cloud outage, ransomware on production databases, or compromised domain control).
2. Construct a multi-stage simulation timeline with realistic, chronological "injects" (events that escalate the disaster context).
3. Evaluate how the defined steps in `ACTIVE_DISASTER_RECOVERY_POLICY` would cope with each inject stage.
4. Highlight critical gaps, such as lack of communication channels during network loss, missing offline configuration copies, or lack of mock-restore tests.
5. Propose specific, actionable improvements to the recovery configurations and policy documentation to satisfy RTO/RPO targets.

## Constraints
- Keep simulation scenarios plausible and grounded in the hardware or software services detailed in the architecture specs.
- Do not suggest expensive proprietary redundancy tools when basic configuration fixes are more viable.

## Expected output
- **Disaster Tabletop Scenario Blueprint**: Complete step-by-step timeline of the simulation.
- **Escalation Injects Catalog**: Timed events to test response teams.
- **DR Policy Compliance Gap Analysis**: Review showing where policies fall short of target metrics.
- **Technical Remediation Backlog**: Actionable backlog of infrastructure and planning improvements.
