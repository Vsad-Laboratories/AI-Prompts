# Analysis Prompt: Data Anomaly & Outlier Explanation Engine

## Purpose
Examine anomalous data points, sudden metric spikes/drops, or statistical outliers in telemetry/business datasets to hypothesize, isolate, and explain root causes.

## Inputs
- `ANOMALY_DATA`: Quantitative metrics, log snippets, or time-series data showing the anomaly.
- `BASELINE_METRICS`: Historical averages, seasonal trends, or expected normal distributions.
- `SYSTEM_CHANGES`: Recent deployments, configuration changes, external events, or market shifts.

## Instructions
1. Characterize the **Anomaly Profile**: Quantify the magnitude, duration, variance, and confidence interval deviation from `BASELINE_METRICS`.
2. Cross-reference `ANOMALY_DATA` against `SYSTEM_CHANGES` to detect temporal correlations.
3. Formulate three competing hypotheses explaining the anomaly:
   - **Data Quality / Ingestion Flaw** (e.g., pipeline bug, duplicate counting).
   - **Internal Operational Vector** (e.g., deployment change, infrastructure failure).
   - **External Behavioral Vector** (e.g., bot traffic, seasonal shock, partner API shift).
4. Outline diagnostic queries or validation experiments required to prove or disprove each hypothesis.
5. Summarize findings into a clear anomaly diagnosis report.

## Constraints
- Do not confuse correlation with causation; explicitly flag unverified assumptions.
- Provide statistical significance assessments where metric variance is present.

## Expected output
- **Anomaly Statistical Overview**: Deviation magnitude, peak timestamp, and baseline comparison.
- **Hypothesis Matrix**: Structured analysis of potential causes with likelihood scores.
- **Diagnostic Validation Steps**: Specific queries or tests to isolate the exact cause.
- **Summary & Next Steps**: Actionable resolution recommendations.
