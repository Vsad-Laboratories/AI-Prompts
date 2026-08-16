# Research Prompt: Systematic Evidence Extraction & Quality Assessment Matrix

## Purpose
Systematically extract empirical findings, statistical effect sizes, sample parameters, and methodological quality scores from scientific literature or technical reports.

## Inputs
- `LITERATURE_TEXT`: Academic paper text, experimental study results, or empirical research reports.
- `RESEARCH_QUESTION`: Primary research query guiding extraction.

## Instructions
1. Inspect `LITERATURE_TEXT` to extract core study attributes: sample size (N), methodology, control variables, and key quantitative findings.
2. Calculate or extract statistical metrics (e.g., p-values, confidence intervals, effect sizes $d$ or $r$, odds ratios).
3. Evaluate study risk of bias using standard criteria (selection bias, reporting bias, measurement error, confounding variables).
4. Assign a Methodological Quality Grade (e.g., High, Moderate, Low, Very Low) adhering to GRADE framework principles.
5. Synthesize findings into a structured evidence extraction matrix.

## Constraints
- Extract only empirical evidence present in the text; explicitly mark missing statistical parameters as `[NOT REPORTED]`.
- Maintain strict objectivity when grading study quality.

## Expected output
- **Study Metadata & Context**: Sample size, population, and methodological framework.
- **Quantitative Findings Table**: Statistical metrics, effect sizes, and confidence intervals.
- **Risk of Bias & Quality Rating**: GRADE quality assessment and identified methodological limitations.
