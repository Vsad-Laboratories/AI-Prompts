# Education Prompt: Concept Map Generator

## Purpose
Deconstruct a complex scientific or technical concept into a highly structured, relational, and visual hierarchy of subconcepts to facilitate accelerated Socratic learning.

## Inputs
- `TARGET_TECHNICAL_CONCEPT`: The primary complex idea, theory, or technology to map (e.g., Quantum Entanglement, Kubernetes scheduling, CRDTs).
- `LEARNER_COMPREHENSION_LEVEL`: The target audience's current knowledge baseline (e.g., high school student, general developer, postdoc researcher).

## Instructions
1. Break down the `TARGET_TECHNICAL_CONCEPT` into its core subconcepts, defining each simply based on the `LEARNER_COMPREHENSION_LEVEL`.
2. Map the structural and logical relationships between subconcepts (e.g., "is a part of", "causes", "inherits from", "optimizes").
3. Organize these relationships into a logical hierarchy, moving from foundational principles to advanced applications.
4. Construct a visual-friendly representation of the concept map using standard Mermaid.js flowcharts or structured nested Markdown lists.
5. Formulate Socratic questions for each node to test the learner's deeper comprehension.

## Constraints
- Do not introduce unrelated advanced subconcepts that bypass the baseline level defined in the inputs.
- Ensure the Mermaid.js syntax is fully valid and clean.

## Expected output
- **Subconcept Inventory & Definitions**: Simplified glossary of all nodes.
- **Relational Map (Mermaid.js)**: Valid Mermaid flowchart code displaying the concept hierarchy.
- **Nested Logical Hierarchy**: Alternative bullet-point breakdown of the relationships.
- **Socratic Knowledge Checks**: Tailored Q&A prompts for self-assessment.
