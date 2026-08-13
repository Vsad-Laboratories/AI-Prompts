# Reasoning Prompt: Counterfactual Scenario Simulation

## Purpose
Examine a past event, product failure, or major decision by simulating "counterfactual" scenarios (what-if analysis) to extract deep organizational, technical, or strategic lessons.

## Inputs
- `ACTUAL_EVENT`: The documented course of events, decisions, and final outcome.
- `WHAT_IF_CHOKEPOINT`: The specific moment, action, or decision to alter in the simulation.

## Instructions
1. Analyze the `ACTUAL_EVENT` and identify the causal chain that led to the final outcome.
2. Isolate the `WHAT_IF_CHOKEPOINT` and propose an alternative decision or state change at that exact moment.
3. Systematically trace the **Counterfactual Causal Chain**: How would that single change ripple through subsequent events?
4. Construct the alternative ending: What is the most plausible alternative outcome of this new chain?
5. Extract key comparative lessons: What does this exercise reveal about the robustness of the system or decision-making process?

## Constraints
- Keep the simulation highly plausible and grounded in reality. Avoid magical thinking where a single minor change solves all world problems.
- Address any new risks or failure modes introduced by the counterfactual decision.

## Expected output
- **Actual vs. Counterfactual Chain**: Parallel comparative timelines of events.
- **Alternative Scenario Autopsy**: Detailed description of the simulated outcome.
- **Robustness Lessons**: Strategic guidelines to make future decision-making resistant to similar choke points.
