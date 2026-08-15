# Analysis Prompt: Engineering and Business Tradeoff Matrix

## Purpose
Structure a systematic, multi-dimensional tradeoff analysis between competing technical architectures, vendor choices, or strategic product directions.

## Inputs
- `OPTIONS`: The list of architecture options, technologies, or strategies being compared.
- `EVALUATION_CRITERIA`: Key dimensions such as cost, scalability, latency, developer velocity, maintainability, and security.
- `BUSINESS_CONSTRAINTS`: Non-negotiable requirements (e.g., SLA budgets, compliance boundaries, deadline windows).

## Instructions
1. Deconstruct `OPTIONS` across all parameters defined in `EVALUATION_CRITERIA`.
2. Construct a **Weighted Decision Matrix** assigning impact scores (1-5) and weighting factors to each criterion based on `BUSINESS_CONSTRAINTS`.
3. Highlight critical failure modes, hidden operational costs, and vendor lock-in risks for each option.
4. Perform a **Sensitivity Analysis**: Explain how recommendations shift if primary business constraints change (e.g., 10x traffic surge vs. tight budget cuts).
5. Deliver a final actionable recommendation with explicit compromise statements.

## Constraints
- Do not declare a "winning" option without explicitly documenting its drawbacks and trade-offs.
- Avoid vague evaluations like "good" or "fast"; provide quantified estimates or comparative scales.

## Expected output
- **Option Comparison Summary**: Structured narrative overview of each option.
- **Weighted Tradeoff Matrix**: Quantitative table with criteria, weights, and scores.
- **Sensitivity & Edge Case Analysis**: Evaluation under changing external conditions.
- **Final Decision Recommendation**: Clear recommendation with mitigation plan for chosen tradeoffs.
