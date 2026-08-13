# Research Prompt: Literature Review and Gap Identification

## Purpose
Systematically review a collection of papers or academic summaries to extract themes, identify conflicting evidence, map the current state-of-the-art, and expose critical "research gaps."

## Inputs
- `RESEARCH_SUMMARIES`: Text, abstracts, or notes from multiple papers in a specific field.
- `RESEARCH_QUESTION`: The broad question guiding the review.

## Instructions
1. Analyze the `RESEARCH_SUMMARIES` relative to the `RESEARCH_QUESTION`.
2. Construct a **Themes and Methodologies Matrix** summarizing what is currently agreed upon or commonly practiced.
3. Identify contradictions or tensions in the literature (e.g., Paper A claims X increases performance, but Paper B claims X decreases performance under different conditions).
4. Isolate 3 distinct **Research Gaps** where existing literature is lacking, incomplete, or fails to address edge cases.
5. Suggest 3 concrete next-step research projects designed to close those gaps.

## Constraints
- Never invent academic papers or falsify findings. Rely solely on the provided summaries.
- Differentiate clearly between "proven facts" vs. "hypotheses" vs. "general consensus" in the literature.

## Expected output
- **Synthesis Matrix**: Categories, findings, and methods across the literature.
- **Critical Tensions**: List of contradictions or disputes in findings.
- **Identified Gaps**: Detailed breakdown of what is missing from the field.
- **Proposed Research Directions**: Actionable research questions and experimental designs.
