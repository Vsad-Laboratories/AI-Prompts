# Debugging Prompt: Kubernetes Pod Failure Analyzer

## Purpose
Diagnose, debug, and formulate remediation steps for failing Kubernetes workloads, pods, and container clusters.

## Inputs
- `POD_DESCRIBE_AND_LOGS`: Direct outputs of standard cluster CLI commands (`kubectl describe pod` and container stdout/stderr dumps).
- `CLUSTER_YAML_MANIFEST`: The deployment, statefulset, or pod configuration manifest used to spin up the failing workload.

## Instructions
1. Audit the resource states in `POD_DESCRIBE_AND_LOGS` to identify critical failure states (e.g., CrashLoopBackOff, ImagePullBackOff, Pending, OOMKilled).
2. Trace events and stateful transitions to find the root event that triggered the crash or blocking state.
3. Analyze `CLUSTER_YAML_MANIFEST` for configuration gaps (e.g., missing environment variables, mismatched ports, incorrect liveness/readiness probes, or missing secret references).
4. Outline concrete remediation actions (e.g., modifying probe thresholds, increasing memory requests/limits, or correcting security context rules).
5. Suggest preventative monitoring practices to spot cluster-level resource starvation before failures manifest.

## Constraints
- Never advise bypasses of cluster security contexts or running containers with elevated privileges unless strictly necessary.
- Ensure the proposed manifest changes match the API version specifications of the original configuration.

## Expected output
- **Failure Classification & Timeline**: Detailed analysis of the pod transition phases leading to failure.
- **Root Cause Determination**: Pinpointed log lines or event markers causing the issue.
- **Refactored YAML Manifest**: Corrected Kubernetes deployment or pod configurations.
- **Cluster Diagnostics Checklist**: List of verification commands to run against the live cluster.
