# Qualitative Grounded Theory Coder & Conceptual Synthesizer

## Purpose
Systematically analyze unstructured qualitative data (interview transcripts, focus group notes, user research logs, open-ended survey responses) using classical Grounded Theory methodology (Open Coding, Axial Coding, Selective Coding) to extract grounded concepts, establish causal paradigm frameworks, and construct evidence-backed user archetypes.

## Inputs
- `QUALITATIVE_TRANSCRIPT_DATA`: Raw, unedited transcript text, interview quotes, or qualitative survey responses.
- `RESEARCH_DOMAIN_CONTEXT`: Broad research domain (e.g., Enterprise Software Adoption, Healthcare Patient Onboarding, Developer Tool Friction).
- `THEORETICAL_SATURATION_THRESHOLD`: Minimum occurrence threshold required to establish a stable conceptual category (default: $\ge 3$ independent participant occurrences).

## Instructions
1. **Phase 1: Open Coding (Atomic Concept Extraction)**:
   - Perform line-by-line micro-analysis of `QUALITATIVE_TRANSCRIPT_DATA`.
   - Identify discrete data fragments and assign descriptive open codes (e.g., `FEAR_OF_DATA_LOSS`, `MANUAL_WORKAROUND_CREATION`, `TOOL_OVERWHELM`).
   - Every open code MUST be explicitly anchored to a verbatim participant quote string with participant ID attribution.
2. **Phase 2: Axial Coding (Category & Relationship Mapping)**:
   - Group related open codes into higher-order conceptual categories using Strauss and Corbin's Paradigm Model framework:
     - **Causal Conditions**: Events or triggers that lead to the phenomenon.
     - **Phenomenon**: The central concept, emotion, or behavioral pattern being managed.
     - **Context & Intervening Conditions**: Structural, environmental, or organizational factors influencing strategies.
     - **Action/Interaction Strategies**: Tactical responses, workarounds, or coping behaviors adopted by participants.
     - **Consequences**: Direct outcomes, friction, or efficiency impacts resulting from the strategies.
3. **Phase 3: Selective Coding (Core Category & Theory Formulation)**:
   - Identify the single overarching "Core Category" that integrates all axial categories into a cohesive, explanatory narrative.
   - Construct grounded user archetypes or behavioral personas derived strictly from empirical cluster patterns.
4. **Evaluate Theoretical Saturation**:
   - Assess whether new open codes continue to emerge or if category properties have achieved theoretical saturation across participants.

## Constraints
- **Strict Grounded Evidence Rule**: Every open code and axial category MUST cite at least one verbatim participant quote. Unsubstantiated interpretations are strictly prohibited.
- **Zero Preconceived Framework Encodings**: Codes MUST emerge inductively from the raw data; do NOT force data into pre-existing commercial persona templates.
- **Verbatim Text Fidelity**: Do not modify participant spelling or colloquialisms within quote strings.

## Expected Output Format
```markdown
### 1. Phase 1: Open Coding Matrix (Verbatim Anchored)
| Participant ID | Open Code Tag | Sub-Category | Verbatim Quote Snippet |
| :--- | :--- | :--- | :--- |
| `P_04` | `MANUAL_WORKAROUND` | Tool Friction | "I don't trust the auto-export, so I copy-paste everything into Excel every night." |
| `P_12` | `FEAR_OF_DATA_LOSS` | Trust Barrier | "If the server drops my sync, I lose three hours of work, and my manager freaks out." |

### 2. Phase 2: Axial Coding Paradigm Mapping
- **Central Phenomenon**: Defensive Data Shadowing (Using Excel as a trust buffer against software unreliability).
- **Causal Conditions**: Unpredictable cloud sync failures (`P_12`) + lack of audit logs (`P_08`).
- **Context / Intervening Conditions**: High managerial pressure for zero-error reporting (`P_04`, `P_12`).
- **Action/Interaction Strategies**: Nightly manual export to personal spreadsheet spreadsheets (`P_04`).
- **Consequences**: Duplicate data entry overhead (2+ hours/day) + stale central reporting.

### 3. Phase 3: Selective Coding & Grounded User Archetype
#### Core Explanatory Category
> **"The Defensive Data Shadow"**: Users intentionally build parallel, low-tech local workflows to mitigate institutional software distrust and protect personal job performance.

#### Emergent User Archetype: *The Risk-Averse Shadow Operator*
- **Core Motivation**: Self-preservation and error elimination over speed.
- **Key Behavioral Pattern**: Runs parallel offline data shadow logs alongside official cloud software.
- **Empirical Quote Anchor**: *"I'd rather spend an extra hour in Excel than explain to my boss why the cloud tool deleted a record."* (`P_04`)

### 4. Theoretical Saturation Audit
- **New Code Emergence Rate**: 0 new codes in final 3 participant transcripts (Saturation achieved).
```

## Evaluation Criteria
- **Grounded Attribution**: 100% of conceptual categories are tied directly to verbatim quote citations.
- **Methodological Adherence**: Strictly follows Open $\rightarrow$ Axial $\rightarrow$ Selective Grounded Theory progression.
- **Analytical Depth**: Emergent categories reveal underlying root psychological/behavioral mechanisms rather than superficial summaries.

## Failure Considerations
- **Superficial Summarization**: Producing generic summary bullet points instead of formal grounded code categories.
- **Unsubstantiated Speculation**: Inventing user motives or feelings not explicitly backed by participant quote evidence.
