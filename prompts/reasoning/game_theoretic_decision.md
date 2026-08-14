# Reasoning Prompt: Game-Theoretic Decision Maker

## Purpose
Formulate optimal strategic decisions in competitive, multi-agent scenarios by applying game theory, Nash Equilibrium, and payoff matrix optimizations.

## Inputs
- `DECISION_SCENARIO`: The strategic context (e.g., market entry, pricing wars, negotiation, or resource allocation).
- `PARTICIPATING_PLAYERS`: List of competitors, their core motivations, potential actions, and known risk tolerances.
- `PAYOFF_UTILITIES`: Known or estimated utility functions, payoff tables, or outcomes for each combination of actions.

## Instructions
1. Structure the `DECISION_SCENARIO` as either a simultaneous, sequential, cooperative, or non-cooperative game.
2. Map out a comprehensive multi-agent payoff matrix or tree based on `PAYOFF_UTILITIES`.
3. Analyze dominant and dominated strategies for all `PARTICIPATING_PLAYERS`.
4. Solve for the Nash Equilibrium (or equilibria) in pure or mixed strategies.
5. Identify potential coordination failures, prisoner's dilemmas, or free-rider risks.
6. Provide strategic recommendations for the primary user to maximize their long-term payoff.

## Constraints
- Do not assume perfectly rational actors; include considerations for bounded rationality or irrational competitor moves where appropriate.
- Payoff estimates must be logically anchored in the provided utility definitions.

## Expected output
- **Game-Theoretic Model Structure**: Classification of game type, players, action spaces, and time steps.
- **Payoff Matrix & Dominance Analysis**: Detailed utility maps showing dominant choices.
- **Nash Equilibrium Determinations**: Clear mathematical or logical formulation of steady-state strategies.
- **Competitive Strategic Playbook**: Actionable roadmap for maximizing payoffs while mitigating competitive threats.
- **Behavioral Robustness Check**: Analysis of outcomes under irrational or sub-optimal opponent behavior.
