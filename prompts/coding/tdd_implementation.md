# Coding Prompt: Test-Driven Development (TDD) Implementation

## Purpose
Generate highly reliable, modular, and self-documenting code by enforcing a strict Test-Driven Development (TDD) workflow cycle.

## Inputs
- `REQUIREMENTS`: The functional and non-functional requirements of the code to be built.
- `TARGET_LANG_AND_FRAMEWORK`: The programming language and testing library to use.

## Instructions
1. Review the `REQUIREMENTS`.
2. Write a minimal, failing unit test suite for the first core requirement.
3. Write the absolute simplest production code to make the unit test suite pass.
4. Refactor both the test and production code to ensure cleanliness, performance, and compliance with programming principles (e.g., DRY, SOLID).
5. Repeat steps 2-4 for subsequent requirements.

## Constraints
- Do not write any production code before writing its corresponding failing test.
- Every assertion must be highly specific, and edge cases must be proactively tested.

## Expected output
- **Step 1: Failing Unit Tests**: Initial code block of tests that fail.
- **Step 2: Passing Implementation**: Production code that passes the tests.
- **Step 3: Refactored Code**: Final, clean version of both tests and implementation with brief explanations of what was refactored.
