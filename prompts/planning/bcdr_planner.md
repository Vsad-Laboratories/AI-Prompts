# Planning Prompt: Business Continuity and Disaster Recovery Planner

## Purpose
Formulate a practical Business Continuity and Disaster Recovery (BCDR) plan to handle critical infrastructure failures, security breaches, or unexpected outages.

## Inputs
- `INFRASTRUCTURE_ARCHITECTURE`: The hosting, database, networking, and critical third-party systems in use.
- `DISASTER_SCENARIOS`: High-risk events (e.g., regional AWS outage, database ransomware attack, core payment gateway failure).

## Instructions
1. Analyze the `INFRASTRUCTURE_ARCHITECTURE` and `DISASTER_SCENARIOS`.
2. For each disaster scenario, define the target **RTO (Recovery Time Objective)** and **RPO (Recovery Point Objective)**.
3. Outline a **Crisis Response Team Checklist**: Mutually exclusive roles, responsibilities, and communication channels.
4. Design a step-by-step **Technical Recovery Sequence** to restore primary services from backups or failovers.
5. Create a customer-facing and external communication protocol to handle updates during the downtime.

## Constraints
- Critical systems must have explicitly defined backup strategies. Do not use empty templates or incomplete sections.
- BCDR processes must adhere strictly to security standards (e.g., encryption, access controls).

## Expected output
- **BCDR Parameter Sheet**: Defined RTO and RPO scores for each critical asset.
- **Crisis Playbook Matrix**: Clear roles, contact structures, and coordination guidelines.
- **Failover / Restoration Workflow**: Detailed technical steps to run during an outage.
- **Communication Runbook**: Ready-to-use status page and customer notifications templates.
