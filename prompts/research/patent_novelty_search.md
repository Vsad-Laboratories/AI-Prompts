# Research Prompt: Patent Novelty Search

## Purpose
Perform systematic, rigorous prior art audits and novelty analyses for patent applications, ensuring technical inventions meet strict patentability criteria.

## Inputs
- `INVENTION_DISCLOSURE`: Detailed technical specification of the target invention, including core components, operational flows, and unique mechanics.
- `KNOWN_PRIOR_ART_LITERATURE`: Textual summaries, abstracts, or claims of existing patents and published scientific literature in the same technological space.

## Instructions
1. Analyze the core claims and mechanisms detailed in `INVENTION_DISCLOSURE` to isolate the primary patentable features.
2. Cross-reference these primary features against the technical specifications in `KNOWN_PRIOR_ART_LITERATURE`.
3. Identify direct overlaps, minor derivative differences, and genuinely novel technical elements.
4. Assess the non-obviousness criteria: Would a Person Having Ordinary Skill In The Art (PHOSITA) find the proposed invention an obvious combination of the prior art?
5. Formulate defensive drafting recommendations to refine invention boundaries and preempt examiner rejections.

## Constraints
- This prompt is an architectural research tool and does not constitute formal legal advice or binding patent filings.
- Ensure all technical claims are categorized strictly based on the provided inputs.

## Expected output
- **Novelty Matrix & Feature Audit**: Mapping of invention features against prior art citations with similarity scores.
- **Non-Obviousness Assessment**: Critical PHOSITA-based evaluation of the technological leap.
- **Preemptive Rejection Audit**: Identification of potential double-patenting or anticipation risks.
- **Defensive Claim Refinements**: Actionable recommendations for narrowing or widening claim parameters.
