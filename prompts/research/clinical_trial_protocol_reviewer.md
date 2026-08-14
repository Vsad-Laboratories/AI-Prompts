# Research Prompt: Clinical Trial Protocol Reviewer

## Purpose
Analyze biomedical and clinical trial protocols to evaluate patient safety measures, statistical power, study design robustness, and regulatory compliance.

## Inputs
- `CLINICAL_PROTOCOL_DRAFT`: Draft protocol covering objectives, patient cohort criteria, dosing regimens, endpoints, and adverse event tracking.
- `REGULATORY_GUIDANCE`: Directives or ethical frameworks from regulatory bodies (e.g., FDA, EMA, or ICH GCP guidelines).

## Instructions
1. Read the `CLINICAL_PROTOCOL_DRAFT` carefully to outline the research objective, study phases, and selection criteria.
2. Evaluate inclusion and exclusion criteria for cohort representation and risk-mitigation (e.g., protecting vulnerable patients).
3. Review the statistical design: Is the sample size justified by power calculations? Are primary and secondary endpoints clearly defined and measurable?
4. Audit patient safety measures, focusing on dose escalation rules, stopping criteria, and adverse event reporting timelines.
5. Check alignment with `REGULATORY_GUIDANCE` to find potential compliance gaps or ethical discrepancies.

## Constraints
- Never approve a medical trial draft that contains unsafe dosing increases or lacks explicit stopping criteria.
- Recommendations must rely strictly on clinically validated research practices and safety principles.

## Expected output
- **Protocol Design Scorecard**: High-level evaluation of scientific rigor, study endpoints, and statistical validity.
- **Patient Safety & Ethical Audit**: Critical review of cohort constraints, dose escalation, and stopping rules.
- **Regulatory Compliance Check**: Identified gaps relative to the specified guidelines.
- **Actionable Optimization Recommendations**: Textual revisions and testing alterations.
