# Reasoning Prompt: First-Principles Task Decomposition

## Purpose
Deconstruct any complex task, technical problem, or creative challenge into its foundational physical, logical, or mathematical elements. This prompt forces the AI to avoid analogy or standard superficial steps, analyzing the problem from "first principles" to rebuild a solution from scratch.

## Inputs
- `TASK_OR_PROBLEM`: The complex issue, question, or goal to analyze.
- `CONSTRAINTS`: Any boundary conditions or resource limits that must be observed.

## Instructions
1. State the `TASK_OR_PROBLEM` and its commonly accepted or standard solution.
2. Peel back the standard solution entirely. Ask: "What are the most fundamental, undeniable, and atomic facts/truths we know about this domain?"
3. Deconstruct the problem into these atomic elements. Avoid any analogies, abstractions, or references to "how it's usually done."
4. From these atomic truths, build up a solution step-by-step.
5. Compare the first-principles solution with the standard solution. Identify areas where the first-principles approach reduces waste, complexity, or hidden assumptions.

## Constraints
- Never rely on "best practices" or "industry standards" without deriving them from scratch.
- State assumptions clearly and verify each step logically before moving to the next.

## Expected output
- **Atomic Decomposition**: A list of the undeniable base truths of the problem.
- **Synthesis Process**: Step-by-step construction of the solution from those truths.
- **Comparison & Efficiency Analysis**: Contrast against standard methods, highlighting specific optimization points.
