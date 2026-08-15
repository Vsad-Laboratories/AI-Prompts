# Research Prompt: Statistical Power & Study Design Auditor

## Purpose
Audit experimental, clinical, or A/B testing methodologies for statistical power, sample size adequacy, selection bias, confounding variables, and Type I / Type II error risks.

## Inputs
- `STUDY_DESIGN_SUMMARY`: Proposed or completed study protocol, hypothesis, sample size, and metric definitions.
- `EXPECTED_EFFECT_SIZE`: Minimal Detectable Effect (MDE) or expected Cohen's d / odds ratio.
- `ALPHA_BETA_LEVELS`: Significance threshold (alpha, e.g., 0.05) and power target (1-beta, e.g., 0.80).

## Instructions
1. Calculate minimal required **Sample Size** based on `EXPECTED_EFFECT_SIZE` and `ALPHA_BETA_LEVELS`.
2. Inspect `STUDY_DESIGN_SUMMARY` for threats to statistical validity:
   - **Type I Errors (False Positives)**: Multiple testing problems, p-hacking, early stopping without alpha spending functions.
   - **Type II Errors (False Negatives)**: Underpowered sample sizes, high variance noise.
   - **Confounding & Selection Bias**: Non-random assignment, attrition bias, novelty effects.
3. Assess the appropriateness of proposed statistical tests (e.g., Welch's t-test vs Mann-Whitney U test vs Chi-Square) based on data distribution assumptions.
4. Propose experimental design corrections (e.g., stratification, variance reduction via CUPED, Sequential Probability Ratio Tests).

## Constraints
- Explicitly state mathematical distribution assumptions behind statistical recommendations.
- Flag any study drawing conclusions from underpowered sample sizes without proper confidence interval disclosures.

## Expected output
- **Power & Sample Size Audit Summary**: Verification of sample sufficiency.
- **Methodological Vulnerability Inventory**: Identified biases, testing errors, or distribution mismatches.
- **Experimental Design Hardening Recommendations**: Concrete adjustments for statistical rigor.
