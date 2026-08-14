# Debugging Prompt: Distributed Tracing Debugger

## Purpose
Isolate latency bottlenecks and propagation issues in microservice architectures by tracing requests across distributed system spans.

## Inputs
- `TRACE_PAYLOAD_DATA`: A collection of spans, durations, trace IDs, parent span IDs, and service names representing a slow transaction.
- `NETWORK_TOPOLOGY_MAP`: Network layout or high-level architecture diagram describing dependencies between the participating microservices.

## Instructions
1. Map the hierarchical flow of spans using trace IDs and parent span IDs from `TRACE_PAYLOAD_DATA`.
2. Pinpoint spans that exhibit anomalous duration (long self-times or execution gaps between parent and child spans).
3. Investigate potential serialization overheads, database lock wait times, or slow third-party calls causing execution delays.
4. Diagnose propagation issues, such as lost headers (e.g., missing W3C Trace Context or B3 headers) resulting in orphaned spans.
5. Provide concrete architectural recommendations to reduce service-to-service roundtrip latency.

## Constraints
- Do not assume database/network state beyond what is specified in the input trace data.
- Ensure all recommendations match the microservice capabilities detailed in `NETWORK_TOPOLOGY_MAP`.

## Expected output
- **Trace Topology Tree**: Hierarchical markdown tree representing the request flow across service spans.
- **Critical Path Bottleneck Analysis**: Specific analysis of the highest-latency contributors.
- **Propagation/Context Audit**: Verification of metadata transfer consistency between spans.
- **Remediation Plan**: Actionable refactoring or caching suggestions to optimize service boundaries.
