# Analysis Prompt: 5 Whys Root Cause Analysis Protocol

## Purpose
Lead an analytical investigation into system failures, process bottlenecks, or quality defects by recursively applying the 5 Whys methodology to uncover underlying systemic causes.

## Inputs
- `INCIDENT_DESCRIPTION`: Detailed account of the symptom, defect, or operational outage.
- `SYSTEM_CONTEXT`: Architecture diagrams, process flows, or operational environments involved.
- `TIMELINE`: Chronological log of events leading up to and during the failure.

## Instructions
1. Establish the **Problem Statement**: Formulate a concise, objective definition of the visible symptom.
2. Execute **5 Iterative Whys**: Ask "Why did this occur?" sequentially. For each level, base the answer strictly on factual evidence from `TIMELINE` and `SYSTEM_CONTEXT`.
3. Distinguish between superficial symptoms, human error factors, and systemic root causes (e.g., missing automated safeguards, flawed policy, lack of validation).
4. Identify contributing factors and branching causal paths when a single failure has multiple underlying vectors.
5. Formulate targeted **Corrective and Preventive Actions (CAPA)** for each identified cause level.

## Constraints
- Avoid stopping at superficial human errors (e.g., "Engineer made a typo"); drill down to why the system permitted the error to reach production.
- Keep each "Why" step logically dependent on the immediate preceding step without skipping logical leaps.

## Expected output
- **Objective Problem Definition**: Concise symptom summary.
- **5 Whys Causal Tree**: Sequential breakdown of cause-and-effect relationships.
- **Root Cause & Systemic Vulnerability Summary**: Categorized systemic flaws.
- **CAPA Action Plan**: Preventative engineering and process improvements with ownership recommendations.
