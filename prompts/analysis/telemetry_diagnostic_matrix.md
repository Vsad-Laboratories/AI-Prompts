# Analysis Prompt: Telemetry Diagnostic & Log Metric Analyzer

## Purpose
Examine multi-service telemetry, structured log streams, metrics counters, and distributed trace spans to isolate system anomalies and performance degradations.

## Inputs
- `TELEMETRY_LOGS`: Raw or JSON-formatted log entries, metric time-series data, or trace span summaries.
- `EXPECTED_BASELINE`: Normal operating metrics (e.g., latency p99 < 200ms, error rate < 0.01%).

## Instructions
1. Parse `TELEMETRY_LOGS` to cluster log entries by severity, timestamp, service name, and error code.
2. Cross-reference observed metrics against `EXPECTED_BASELINE` to detect threshold breaches and anomalous metric spikes.
3. Construct a temporal timeline mapping incident progression from initial signal anomaly to failure propagation.
4. Categorize root-cause candidates into Infrastructure, Application Code, Network/I/O, or External Dependencies.
5. Provide actionable remediation steps and telemetry monitoring alerts to detect recurrence.

## Constraints
- Focus exclusively on empirical evidence present in `TELEMETRY_LOGS`; avoid unverified speculation.
- Differentiate clearly between correlation and causation in multi-service failure chains.

## Expected output
- **Incident Summary & Severity Level**: Concise evaluation of the telemetry anomaly.
- **Anomaly Timeline**: Chronological progression of error signals and metric breaches.
- **Diagnostic Matrix**: Structured table mapping symptoms, probable root causes, and verification steps.
- **Remediation & Alert Specifications**: Immediate fix recommendations and Prometheus/Datadog alert rules.
