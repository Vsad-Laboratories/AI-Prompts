# Reasoning Prompt: Minto Pyramid Principle Thought Structuring

## Purpose
Structure complex executive communications, proposals, strategic reports, or technical recommendations using Barbara Minto's Pyramid Principle (Answer First -> Group Supporting Arguments -> Order Logical Ideas).

## Inputs
- `RAW_IDEAS`: Unstructured research findings, proposal ideas, data analysis points, or meeting notes.
- `TARGET_AUDIENCE`: Key decision-makers (e.g., C-Suite Executives, Board of Directors, Client Leadership).
- `PRIMARY_QUESTION`: The core underlying question the audience needs answered (e.g., "Should we acquire Company X?", "How do we resolve our system outage scaling issue?").

## Instructions
1. Apply the **Answer First Principle (SCQA Framework)**:
   - *Situation*: Establish the uncontroversial context baseline.
   - *Complication*: Detail the problem or change triggering the primary question.
   - *Question*: State the core decision question clearly.
   - *Answer*: State the primary governing recommendation upfront.
2. Group supporting arguments into mutually exclusive, collectively exhaustive (**MECE**) categories.
3. Structure logical arguments using either **Deductive Ordering** (Premise 1 -> Premise 2 -> Conclusion) or **Inductive Ordering** (Group of similar causes -> Action required).
4. Verify that every sub-point directly supports the parent recommendation directly above it in the pyramid.
5. Format final output into an executive communication draft.

## Constraints
- Never bury the lead; ensure the primary recommendation appears in the opening paragraph/slide.
- Enforce strict MECE compliance to eliminate overlapping arguments or missing categories.

## Expected output
- **SCQA Executive Framework**: Situation, Complication, Question, Answer setup.
- **MECE Pyramid Structure**: Hierarchical tree of parent claims and supporting evidence.
- **Executive Draft / Brief**: Polished executive communication artifact.
