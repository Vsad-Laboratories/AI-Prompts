# Writing Prompt: API Breaking Change & Developer Migration Guide Generator

## Purpose
Synthesize technical API diffs, breaking change lists, and deprecated endpoint schemas into a clear, developer-friendly Migration Guide for client engineers.

## Inputs
- `BREAKING_CHANGES_LIST`: List of modified endpoints, changed payload fields, deleted parameters, or updated auth flows.
- `OLD_VS_NEW_SCHEMAS`: Comparative code/JSON schemas before and after the API update.

## Instructions
1. Categorize breaking changes into High Impact (action required immediately), Medium Impact (deprecated with fallback), and Low Impact (field renames).
2. For every breaking change, provide side-by-side "Before & After" code/payload examples illustrating the exact refactoring required.
3. Formulate a step-by-step developer migration checklist ordered by dependency sequence.
4. Provide common error messages client engineers might encounter during migration and exact troubleshooting remedies.
5. Include sunset/deprecation timelines and backwards-compatibility window specifications.

## Constraints
- Provide concrete code diffs; do not rely solely on prose explanations of API changes.
- Ensure clear highlighting of required header or authentication changes.

## Expected output
- **Executive Migration Summary**: Overview of version changes and deprecation schedule.
- **Breaking Changes Matrix**: Impact rating, affected endpoints, and brief description.
- **Before & After Code Examples**: Comparative code snippets for client refactoring.
- **Developer Migration Checklist**: Sequential checklist for upgrading client applications.
