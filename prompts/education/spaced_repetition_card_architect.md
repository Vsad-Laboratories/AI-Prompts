# Spaced Repetition Flashcard Architect

## Purpose
Convert dense technical documentation, complex software engineering architectures, academic research papers, or API specifications into highly optimized active recall questions and spaced repetition flashcards formatted for Anki (`.apkg` / TSV) adhering to atomic memory principle guidelines.

## Inputs
- `SOURCE_TECHNICAL_TEXT`: Raw technical document, architecture spec, code pattern guide, or textbook chapter.
- `TARGET_AUDIENCE_LEVEL`: Knowledge baseline (Beginner, Intermediate, Senior Engineer, Domain Specialist).
- `OUTPUT_FORMAT`: Desired export format (Anki TSV / Cloze Deletion Markdown / JSON Schema).

## Instructions
1. **Deconstruct Technical Source Material**: Identify fundamental atomic facts, core operational concepts, syntax signatures, architectural trade-offs, and failure modes in `SOURCE_TECHNICAL_TEXT`.
2. **Apply Minimum Information Principle (Atomic Cards)**: Ensure every generated card tests **exactly one** discrete concept or retrieval step. Break complex multi-part questions into individual atomic flashcards.
3. **Design Diverse Card Types**:
   - **Basic Front/Back**: Question testing conceptual recall or definition.
   - **Cloze Deletion (`{{c1::...}}`)**: Sentence with hidden key terms testing precise terminology, code parameters, or mathematical equations.
   - **Reverse / Bidirectional**: Testing mapping from concept $\rightarrow$ term AND term $\rightarrow$ concept.
   - **Diagnostic / Scenario**: Short realistic code snippet or system failure asking for immediate root cause identification.
4. **Formulate Unambiguous Questions**: Ensure questions provide sufficient contextual constraints so there is only ONE correct, concise answer.
5. **Incorporate Visual / Structural Anchors**: Add formatting bolding, code syntax block tags, and explanatory back-of-card extra context (`Extra / Explanation`).

## Constraints
- **Strict Atomicity**: No card front may contain "List 5 reasons..." or multi-bullet answers. Split multi-part lists into distinct Cloze or Overlapping Cloze cards.
- **No Ambiguous Prompts**: Avoid open-ended prompts like "What about X?". Use specific prompts like "In PostgreSQL, what index type is default for scalar equality checks?".
- **Zero Hallucination**: Card facts MUST strictly align with `SOURCE_TECHNICAL_TEXT`.

## Expected Output Format
```markdown
# Anki Flashcard Export (TSV / Anki Import Compatible)

### Card 1 (Basic Conceptual)
- **Front**: What is the default index data structure used in PostgreSQL when running `CREATE INDEX` without specifying a type?
- **Back**: B-Tree index
- **Extra/Context**: B-Trees handle equality and range queries (`<`, `<=`, `=`, `>=`, `>`).

### Card 2 (Cloze Deletion - Code Parameter)
- **Text**: In Rust, to safely pass shared read-only data across threads, you wrap the data in `Arc<{{c1::T}}>`. To enable shared mutable state across threads, you combine it as `Arc<{{c2::Mutex<T>}}>`.
- **Extra/Context**: `Arc` handles multi-thread reference counting, while `Mutex` provides interior mutability and lock synchronization.

### Card 3 (Diagnostic Scenario)
- **Front**: **Code Context**:
  ```python
  import asyncio
  async def fetch():
      # Missing keyword
      res = requests.get("https://api.internal/data")
  ```
  **Question**: Why does this function block the Python asyncio event loop?
- **Back**: `requests.get()` is a synchronous blocking HTTP library call.
- **Extra/Context**: Replace with an async HTTP library like `httpx` or `aiohttp` using `await`.
```

## Evaluation Criteria
- **Atomicity Score**: 100% of generated cards test a single atomic fact.
- **Retrieval Precision**: Question phrasing allows immediate, unambiguous answer retrieval.
- **Format Compliance**: Perfectly parses into Anki import tools without CSV/TSV delimiter errors.

## Failure Considerations
- **Bloated Fronts**: Pasting paragraphs of text onto the card front.
- **Complex Multi-Item Lists**: Asking users to memorize 8 bullet points on a single card.
