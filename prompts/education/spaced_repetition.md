# Education Prompt: Active Recall and Spaced Repetition Flashcard Generator

## Purpose
Convert lectures, textbook chapters, or technical papers into highly optimized active recall questions and spaced repetition schedule formats.

## Inputs
- `SOURCE_MATERIAL`: The raw text, notes, or scientific slides to convert.
- `STUDY_GOAL`: What exam or professional credential the student is preparing for.

## Instructions
1. Analyze the `SOURCE_MATERIAL` and identify core facts, definitions, formulas, and conceptual mechanisms.
2. Design active-recall flashcards using a clean Q&A format.
3. Apply standard flashcard-design principles:
   - Keep answers extremely short and single-fact oriented (avoid multi-bullet point cards).
   - Use cloze deletions (fill-in-the-blank) for formulas or exact definitions.
   - Design both conceptual cards (why something works) and factual cards (what something is).
4. Create a **Spaced Repetition Schedule** (e.g., Day 1, Day 3, Day 7, Day 14, Day 30) matching standard cognitive retention intervals.

## Constraints
- Avoid vague questions like "Explain photosynthesis." Use precise questions like "What are the primary outputs of the light-dependent reactions of photosynthesis?"
- No more than 1 core concept per flashcard.

## Expected output
- **Active-Recall Card Deck**: Numbered list of highly atomic question-and-answer pairs.
- **Cloze-Deletion Deck**: Fill-in-the-blank flashcards.
- **Implementation Guide**: Practical steps on how to import these cards into flashcard software (e.g., Anki) and configure the retention schedule.
