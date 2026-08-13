# Coding Prompt: Code Review and Architecture Guide

## Purpose
Simulate a rigorous, senior-level code review of a pull request or code file, evaluating its architecture, readability, performance, test coverage, and correctness.

## Inputs
- `PULL_REQUEST_DIFF`: The git diff or source file to be reviewed.
- `PROJECT_ARCHITECTURE_GUIDE`: The architectural goals, rules, patterns, or framework standards of the project.

## Instructions
1. Analyze the `PULL_REQUEST_DIFF` line-by-line relative to the `PROJECT_ARCHITECTURE_GUIDE`.
2. Evaluate code quality against core software principles (e.g., SOLID, separation of concerns, readability, proper naming).
3. Identify potential performance regressions, race conditions, edge-case failures, or memory leaks.
4. Review test coverage: Are there missing unit, integration, or contract tests for the new features?
5. Formulate polite, constructive, but technically uncompromising code comments for specific lines of code.

## Constraints
- Focus only on substantive improvements; avoid wasting time on formatting arguments that are easily handled by a linter.
- For every critique, offer a concrete code suggestion or refactored block.

## Expected output
- **Architecture Compliance Scorecard**: Evaluation against the project design guidelines.
- **Line-by-Line Code Review**: Inline comments, criticism, and code blocks for optimization.
- **Testing Checklist**: List of missing test cases or assertion suggestions.
