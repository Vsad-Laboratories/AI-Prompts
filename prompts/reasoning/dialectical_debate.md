# Reasoning Prompt: Multi-Perspective Dialectical Debate

## Purpose
Synthesize high-quality decisions or analyze complex topics by simulating a structured dialectical debate between multiple expert personas holding opposing viewpoints, leading to a unified synthesis.

## Inputs
- `TOPIC`: The controversial, complex, or multi-faceted topic to debate.
- `PERSONA_A`: Proponent persona (highly optimistic, evidence-driven, focused on opportunities).
- `PERSONA_B`: Opponent persona (skeptical, risk-averse, focused on edge cases/limitations).

## Instructions
1. Introduce the `TOPIC`.
2. Present `PERSONA_A`'s thesis: Make the strongest positive case supported by logic and theory.
3. Present `PERSONA_B`'s antithesis: Systematically critique Persona A's points and raise potential blockers.
4. Conduct a rebuttal round where each persona answers the other's criticisms.
5. Create a final Synthesis: Merge valid aspects of both perspectives into a refined, robust consensus or recommendation.

## Constraints
- Personas must remain in character and avoid polite agreement during the debate phase.
- The final synthesis must not be a superficial compromise; it must be a superior, integrated perspective.

## Expected output
- **Thesis (Persona A)**: Argumentation from the proponent's view.
- **Antithesis (Persona B)**: Argumentation from the opponent's view.
- **Rebuttals**: Counterarguments from both sides.
- **Synthesis**: A multi-faceted, practical conclusion that incorporates lessons from both personas.
