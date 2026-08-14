# Analysis Prompt: Product-Market Fit Survey Analyzer

## Purpose
Analyze quantitative and qualitative product-market fit (PMF) survey responses to identify core user personas, feature priorities, and key drivers of user retention.

## Inputs
- `PMF_SURVEY_RESPONSES`: Structured tabular or textual survey logs detailing user roles, usage frequency, satisfaction scores, and answers to "how would you feel if you could no longer use this product?".
- `PRODUCT_GOALS_AND_METRICS`: High-level retention targets, active user milestones, and current product value propositions.

## Instructions
1. Parse the `PMF_SURVEY_RESPONSES` to calculate the exact percentage of users who would be "very disappointed" if the product disappeared (the standard Sean Ellis PMF benchmark).
2. Segment the responses based on cohorts (e.g., highly active vs. occasional users) to locate the "high-expectation customer" (HXC) profile.
3. Analyze qualitative feedback to identify main themes explaining why the product is valuable and what specific features or capabilities are missing.
4. Synthesize the results to discover friction points that prevent low-engagement users from experiencing the core value ("aha!" moment).
5. Map these insights back to `PRODUCT_GOALS_AND_METRICS` to prioritize the product backlog.

## Constraints
- Do not make broad statistical claims if the sample size in the survey responses is too small; highlight data limitations where appropriate.
- Focus on actionable product adjustments rather than generic growth-marketing recommendations.

## Expected output
- **Sean Ellis PMF Benchmark Score**: Calculated score with detailed cohort segmentation.
- **High-Expectation Customer (HXC) Persona**: Profile definition of the core retained audience.
- **Qualitative Sentiment & Feature Matrix**: Map of desired capabilities and friction points categorized by user segments.
- **Product Backlog Priorities**: Prioritized engineering or feature roadmap items with an impact vs. effort scoring.
