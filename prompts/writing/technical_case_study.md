# Writing Prompt: Technical Case Study Writer

## Purpose
Transform a complex project implementation, software release, or system recovery event into a compelling, professional, and readable engineering or business case study.

## Inputs
- `PROJECT_DETAILS`: Notes, pull requests, Slack transcripts, or system metrics documenting the event.
- `TARGET_FORMAT`: The length and style (e.g., standard tech blog post, short PDF brief, business-facing whitepaper).

## Instructions
1. Analyze the `PROJECT_DETAILS` and identify the core challenge, the chosen solution, and the measurable outcomes.
2. Structure the narrative into five logical parts:
   - **Executive Summary / TL;DR**: A brief snapshot of the issue, action, and results.
   - **The Challenge**: The starting state, technical obstacles, and what was at stake.
   - **The Evaluation / Alternatives**: Other paths considered and why they were rejected.
   - **The Implementation**: Step-by-step description of the chosen solution, including technical hurdles overcome.
   - **The Impact / Lessons**: Quantified performance metrics, team learnings, and future roadmaps.
3. Review and polish the language to match the requested `TARGET_FORMAT` (e.g., clear, metrics-driven, conversational-yet-professional).

## Constraints
- Every claim of success must be tied to a metric or clear outcome (e.g., "reduced latency by X%"). If metrics are missing, use clear indicators or specify how to measure.
- Keep the technical details precise; do not hand-wave away the hard engineering challenges.

## Expected output
- **Structured Case Study Draft**: Fully written case study sections under professional headers.
- **Key Metrics Highlight**: A distinct section or callout box containing key performance indicators (KPIs).
- **Post-Mortem Takeaways**: Clear bullet points highlighting the main organizational or engineering takeaways.
