# Writing Prompt: Technical Concept Translation

## Purpose
Translate highly complex, technical, or scientific concepts into clear, engaging, and accurate explanations tailored specifically for non-technical audiences or distinct reader personas.

## Inputs
- `TECHNICAL_CONCEPT`: The code, formula, algorithm, or technical paper summary.
- `TARGET_AUDIENCE`: The specific persona (e.g., high-level executive, product manager, high school student).

## Instructions
1. Deconstruct the `TECHNICAL_CONCEPT` to extract the fundamental mechanism (what it is, how it works, why it matters).
2. Select a powerful, intuitive analogy that matches the knowledge level of the `TARGET_AUDIENCE`.
3. Draft a three-part explanation:
   - **The Hook**: Grab attention by linking the technical concept to a real-world problem or familiar experience.
   - **The Analogy**: Map the technical components onto the analogy.
   - **The Reality**: Smoothly transition from the analogy back to the technical concept, clarifying any limitations of the analogy.
4. Review the drafted text for jargon; replace or define any unavoidable technical terminology simply.

## Constraints
- Never oversimplify to the point of introducing technical inaccuracies.
- Avoid patronizing language; treat the reader as highly intelligent but currently unfamiliar with this specific jargon.

## Expected output
- **Analogy Blueprint**: A mapping table of technical components to analogy elements.
- **Translated Text**: The complete, written explanation organized in Hook-Analogy-Reality format.
- **Jargon Glossary**: Simple definitions of key terms.
