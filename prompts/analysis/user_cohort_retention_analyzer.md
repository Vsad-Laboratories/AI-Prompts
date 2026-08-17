# User Cohort Retention & Churn Behavior Analyzer

## Purpose
Examine product usage telemetry, user session event logs, feature adoption histories, and qualitative exit survey data to perform multi-cohort retention analysis, isolate early churn indicator signals, and formulate targeted product and lifecycle retention playbooks.

## Inputs
- `USAGE_TELEMETRY_DATA`: User activity logs, session counts, feature engagement events, active days per week/month (WAU/MAU).
- `COHORT_REGISTRATION_DATA`: User sign-up dates, acquisition channels, plan tiers, onboarding completion timestamps.
- `EXIT_SURVEY_FEEDBACK`: Unstructured qualitative cancellation notes, churn reason survey selections, support ticket histories.

## Instructions
1. **Analyze Cohort Retention Curves**: Parse user activity logs to calculate baseline retention percentages across key time milestones: Day 1, Day 7, Day 14, Day 30, and Day 90.
2. **Identify Flattening vs. Bleeding Curves**: Determine whether cohort retention curves flatten into a stable asymptote (indicating long-term product-market fit) or continuously bleed toward zero.
3. **Isolate "Activation Threshold" Key Actions**: Identify early habit-forming user behaviors during the first 72 hours that correlate most strongly with Day 30+ retention (e.g., "created 3 projects and invited 1 team member").
4. **Isolate Churn Predictor Signals**: Identify behavioral drop-off triggers prior to cancellation (e.g., 50% drop in weekly active sessions over 14 days, repeated error encounters, zero team invites).
5. **Synthesize Qualitative Exit Motifs**: Cluster unstructured cancellation survey feedback into core churn drivers (Pricing/Value mismatch, Missing Feature, UX Friction, Performance/Bugs, Competitor Migration).
6. **Formulate High-Impact Retention Playbooks**: Design concrete product optimizations, triggered re-engagement email flows, and onboarding friction removal steps targeted at primary churn triggers.

## Constraints
- **Correlation vs. Causation Guardrail**: Distinguish between correlated engagement markers and true causal activation actions before recommending product changes.
- **Actionable UX/Product Interventions**: Every identified churn driver MUST be paired with a specific product, onboarding, or lifecycle email mitigation.
- **Percentage & Segment Precision**: State retention rates and churn risk metrics as exact percentages tied to specific user segments or acquisition cohorts.

## Expected Output Format
```markdown
### 1. Cohort Retention Summary
- **Day 1 Retention**: [X%]
- **Day 7 Retention**: [X%]
- **Day 30 Retention**: [X%]
- **Retention Curve Status**: [FLATLINED AT X% (HEALTHY) / CONTINUOUS BLEED (UNHEALTHY)]
- **Primary Activation Milestone**: [e.g., "3 exported files within first 48 hours"]

### 2. Behavioral Churn Predictor Matrix
| Behavioral Signal | Churn Correlation | Lead Time Before Churn | Identified Friction / Root Cause |
| :--- | :--- | :--- | :--- |
| Session frequency drops >60% in Week 2 | 84% | 12 Days | Failed first-run setup experience |

### 3. Qualitative Exit Motifs
| Theme | % of Churned Users | Key Quotes / Customer Sentiment Summary |
| :--- | :--- | :--- |
| UX Friction / Onboarding | 42% | "Couldn't figure out how to configure SSO/teams" |

### 4. Retention Optimization Roadmap
- **Onboarding UX Fixes**: [Concrete product UI change]
- **Triggered Re-engagement Loops**: [Lifecycle email or in-app notification trigger]
- **Feature Adoption Guidance**: [Tooltips or interactive onboarding walkthroughs]
```

## Evaluation Criteria
- **Analytical Rigor**: Accurately calculates cohort retention trajectories and isolates statistical activation thresholds.
- **Data Triangulation**: Synthesizes quantitative telemetry with qualitative exit survey comments seamlessly.
- **Actionability**: Delivers specific, high-leverage product recommendations rather than generic user growth advice.

## Failure Considerations
- **Overestimating Activation**: Selecting passive onboarding steps (e.g., "viewed dashboard") as activation milestones rather than value-creation actions.
- **Ignoring Cohort Dynamics**: Blending disparate user acquisition channels into a single monolithic retention average.
