# Education Prompt: Adaptive Mastery Assessment & Diagnostic Quiz Generator

## Purpose
Generate adaptive, misconception-aware technical assessments that accurately evaluate learner comprehension and isolate specific conceptual blind spots.

## Inputs
- `SUBJECT_MATTER`: Topic or domain for assessment (e.g., Distributed Systems Consensus, SQL Indexing, React Reconciliation).
- `DIFFICULTY_RANGE`: Bloom's Taxonomy targeting (e.g., Application, Analysis, Evaluation).

## Instructions
1. Design diagnostic multiple-choice and short-answer questions targeted at core principles of `SUBJECT_MATTER`.
2. Ensure every incorrect option (distractor) represents a well-known technical misconception or common junior engineer trap.
3. Provide detailed conceptual explanations for why each distractor is incorrect and why the correct answer holds.
4. Map questions to explicit learning outcomes and difficulty tiers.
5. Formulate remediation learning paths tailored to specific failure patterns observed in student responses.

## Constraints
- Avoid trick questions that rely on trivia or obscure syntax; focus purely on deep conceptual mastery.
- Distractors must be plausible and reflect real-world misunderstandings.

## Expected output
- **Adaptive Diagnostic Question Set**: Structured questions with calibrated difficulty ratings.
- **Distractor Misconception Key**: Detailed mapping of incorrect choices to underlying conceptual misunderstandings.
- **Remediation Feedback Matrix**: Customized study recommendations based on specific missed questions.
