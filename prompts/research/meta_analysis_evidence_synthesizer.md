# Research Prompt: Meta-Analysis Evidence Synthesizer

## Purpose
Synthesize quantitative findings, effect sizes, and statistical confidence levels from multiple academic or empirical research papers to form a unified consensus summary.

## Inputs
- `EMPIRICAL_STUDIES_EXTRACTS`: Extracted tables, sample sizes (N), p-values, effect sizes, and confidence intervals from multiple related studies.
- `SYNTHESIS_OBJECTIVES`: The specific hypothesis or research question being investigated.

## Instructions
1. Analyze `EMPIRICAL_STUDIES_EXTRACTS` to standardize results (e.g., converting different effect size metrics into a single standard index).
2. Weight the findings of each study based on sample size, methodology rigor, and statistical significance.
3. Identify contradictions, outlier papers, and potential publication bias (e.g., underreporting of null results).
4. Formulate a synthesized statistical conclusion addressing the `SYNTHESIS_OBJECTIVES`.
5. Specify the overall confidence level of the synthesized evidence and outline areas where further research is required.

## Constraints
- Do not perform mathematical calculations that are unsupported by the input study parameters; clearly describe any mathematical assumptions.
- Avoid treating low-sample-size anecdotal studies with equal weight as large-scale randomized trials.

## Expected output
- **Standardized Evidence Matrix**: Unified table showing study parameters, weighted values, and effect sizes.
- **Statistical Consensus Synthesis**: Comprehensive summary of the empirical findings relative to the research question.
- **Bias & Outlier Audit**: Detailed analysis of outliers and publication bias risks.
- **Evidence Confidence Rating**: Overall strength classification of the aggregated findings.
