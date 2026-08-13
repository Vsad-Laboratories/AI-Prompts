# Research Prompt: Peer Review Simulator

## Purpose
Simulate an academic peer-review process (such as for a top-tier computer science or scientific journal/conference) to evaluate the methodology, claims, novelty, and rigor of a draft paper or research idea.

## Inputs
- `RESEARCH_DRAFT`: The abstract, introduction, or full proposal of the research work.
- `TARGET_VENUE`: The journal or conference standards to simulate (e.g., Nature, IEEE, NeurIPS, CHI).

## Instructions
1. Analyze the `RESEARCH_DRAFT` against the rigorous standards of the `TARGET_VENUE`.
2. Formulate 3 distinct reviewer personas:
   - *Reviewer 1 (The Methodologist)*: Highly focused on soundness, control groups, statistics, and baseline comparisons.
   - *Reviewer 2 (The Novelty Critic)*: Highly focused on state-of-the-art advancement, literature review, and value proposition.
   - *Reviewer 3 (The Application Expert)*: Highly focused on practical utility, reproducibility, clarity, and overall readability.
3. Write detailed reviews from each of the three reviewer personas, highlighting weaknesses and strengths.
4. Synthesize the feedback into an "Editor's Decision" and outline a concrete action plan for revision.

## Constraints
- Do not offer generic compliments. The reviews must be constructively critical and demand rigorous evidence for all claims.
- Identify specific papers or common baseline methods that are missing from the draft if applicable.

## Expected output
- **Reviewer Reports**: 3 detailed reviews with specific critiques of methodology, novelty, and application.
- **Editorial Verdict**: A clear decision (Accept, Minor Revision, Major Revision, or Reject) with key justifications.
- **Revision Roadmap**: Structured recommendations for improving the research before final submission.
