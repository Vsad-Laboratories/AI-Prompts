# Analysis Prompt: System Dependency Risk Auditor

## Purpose
Identify, assess, and catalog structural and single-point-of-failure (SPOF) risks within software architectural dependencies, libraries, and external systems.

## Inputs
- `SYSTEM_DEPENDENCY_GRAPH`: List of active libraries, internal microservice connections, database clusters, and external third-party API dependencies.
- `SERVICE_LEVEL_OBJECTIVES`: Uptime targets (SLAs), max latency tolerances, and system fallback constraints.

## Instructions
1. Map the `SYSTEM_DEPENDENCY_GRAPH` to identify cyclic dependencies, highly coupled clusters, and single points of failure.
2. Evaluate the risk profile of each dependency: check for outdated libraries, lack of redundancy, or APIs that lack failovers.
3. Trace how a sudden failure in a peripheral service or third-party API propagates through the system (cascade-failure analysis).
4. Assess current timeout, retry, circuit-breaker, and bulkhead patterns against the standards in `SERVICE_LEVEL_OBJECTIVES`.
5. Formulate fallback designs and graceful degradation steps for high-risk nodes.

## Constraints
- Recommendations must preserve existing system logic; do not propose complete rewrites of stable services without strong risk justification.
- Ensure the proposed mitigations conform to standard site reliability engineering (SRE) practices.

## Expected output
- **Structural SPOF Risk Log**: Catalog of single-point-of-failure nodes with calculated risk indices.
- **Cascade-Failure Simulation Trace**: Step-by-step description of system behavior if a critical node fails.
- **Architectural Mitigation Plan**: Concrete specifications for implementing circuit breakers, fallbacks, or bulkheads.
- **SRE SLO Alignment Assessment**: Review showing where current setups fall short of uptime targets.
