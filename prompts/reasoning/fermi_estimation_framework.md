# Reasoning Prompt: Fermi Estimation & Order-of-Magnitude Reasoning Engine

## Purpose
Guide an LLM through structured Fermi Estimation and order-of-magnitude quantitative reasoning to estimate complex, under-specified engineering, bandwidth, capacity, or market figures.

## Inputs
- `ESTIMATION_QUESTION`: High-level quantitative question (e.g., "Estimate daily storage throughput required for a global messaging app with 100M active users").
- `KNOWN_BOUNDARIES`: Optional known constraints, baseline population numbers, or physical limits.

## Instructions
1. Deconstruct `ESTIMATION_QUESTION` into explicit sub-components using dimensional analysis.
2. Formulate explicit, justified assumptions for every unknown variable, stating upper and lower bounds.
3. Calculate step-by-step arithmetic conversions, maintaining clear unit tracking throughout.
4. Conduct a sensitivity analysis identifying which assumed variable has the largest impact on the final result.
5. Provide a realistic order-of-magnitude range (e.g., $10^5$ to $10^6$ ops/sec) with sanity checks against known benchmarks.

## Constraints
- Explicitly state every assumed constant or behavioral frequency.
- Show dimensional units in every step of calculation to prevent math/unit errors.

## Expected output
- **Decomposition & Variable Mapping**: Formula breakdown and variable definitions.
- **Assumptions & Bounded Values**: List of baseline estimates with justifications.
- **Step-by-Step Dimensional Calculation**: Clear mathematical progression with units.
- **Order-of-Magnitude Conclusion & Sensitivity Analysis**: Final range estimate and key drivers.
