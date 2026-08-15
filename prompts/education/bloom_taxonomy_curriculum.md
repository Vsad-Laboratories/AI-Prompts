# Education Prompt: Bloom's Taxonomy Course & Curriculum Generator

## Purpose
Design pedagogical learning modules, course outlines, and assessment frameworks structured around the six cognitive levels of Bloom's Revised Taxonomy (Remember, Understand, Apply, Analyze, Evaluate, Create).

## Inputs
- `SUBJECT_TOPIC`: Technical or scientific topic to be taught (e.g., Quantum Computing Basics, Distributed Consensus Systems).
- `TARGET_AUDIENCE`: Skill level and background of learners (e.g., Junior Software Engineers, Undergraduate Biology Students).
- `COURSE_DURATION`: Total instructional hours or number of module units available.

## Instructions
1. Break down `SUBJECT_TOPIC` into logical sub-modules distributed across `COURSE_DURATION`.
2. Construct learning objectives explicitly mapped to the 6 cognitive tiers of Bloom's Revised Taxonomy:
   - **Remember**: Define key terms, formulas, and baseline principles.
   - **Understand**: Explain core mechanisms in the student's own words.
   - **Apply**: Solve standard concrete problems using foundational models.
   - **Analyze**: Deconstruct edge cases, architectural tradeoffs, or failure logs.
   - **Evaluate**: Critique competing approaches or audit flawed solutions.
   - **Create**: Design a novel system, protocol, or synthesis artifact.
3. Design formative assessment tasks for each taxonomy level to evaluate mastery.
4. Provide instructor rubrics with explicit passing vs. failing criteria for subjective assignments.

## Constraints
- Do not linger exclusively on lower-level cognitive tiers (Remembering/Understanding); ensure upper tiers (Analyze/Evaluate/Create) comprise at least 40% of the curriculum.
- Ensure all learning objectives are measurable using explicit action verbs.

## Expected output
- **Curriculum Architecture Overview**: Course roadmap and module distribution.
- **Bloom's Taxonomy Objective Matrix**: Objectives and activities grouped by cognitive level.
- **Formative & Summative Assessments**: Exam questions, lab assignments, and design prompts.
- **Grading Rubric**: Objective scoring rubrics for project evaluations.
