# Autonomous AI Prompts Repository

Welcome to the AI Prompts Repository, engineered and updated autonomously by Jules, your Dedicated AI Prompt Research Agent. This repository contains high-quality, production-ready, model-agnostic, and thoroughly validated prompt templates across multiple professional and scientific disciplines.

Our mission is to cultivate one of the most organized, deeply researched, and reliable prompt libraries available for developers, engineers, educators, researchers, and project planners.

## Repository Structure & Organization
All prompts follow a rigorous, standardized format to ensure predictable execution, clarity, and adaptability across LLMs. Every prompt contains:
- **Purpose**: A clear explanation of what the prompt achieves.
- **Inputs**: Defined variables (e.g., `REQUIREMENTS`, `TASK`) to inject contextual data.
- **Instructions**: Precise sequential steps for the LLM to follow.
- **Constraints**: Essential boundaries, limitations, and failure mitigations.
- **Expected output**: Structured markdown layout instructions for the LLM's response.

---

## Daily Prompt Catalog (Indexed Autonomously)

### Agents
- [Autonomous Agent Persona Architect](prompts/agents/agent_persona.md) - Design robust, state-aware system instructions for autonomous agents.
- [Human-in-the-Loop Collaboration Protocol](prompts/agents/human_in_the_loop.md) - Protocols for agents to hand over complex edge-cases to humans.
- [Multi-Agent Orchestration Protocol](prompts/agents/agent_orchestration.md) - Coordinate multi-agent tasks with clean handoff specifications.

### Analysis
- [Competitive Intelligence Synthesis](prompts/analysis/competitive_intelligence.md) - Extract competitor roadmap strategies, SWOT matrix, and strategic opportunities.
- [Qualitative Sentiment Synthesis](prompts/analysis/sentiment_synthesis.md) - Group unstructured app reviews/feedback into emotional themes.
- [Quantitative Data Critique](prompts/analysis/quantitative_critique.md) - Audit datasets for statistical fallacies, p-hacking, and biases.
- [Root Cause Analysis and Ishikawa Diagrammer](prompts/analysis/ishikawa_rca.md) - Perform formal root cause analysis with Fishbone mapping.

### Coding
- [Code Review and Architecture Guide](prompts/coding/code_review.md) - Senior-level pull request review with architectural feedback.
- [Legacy Code Refactoring and Modernization](prompts/coding/legacy_refactoring.md) - Safely migrate old legacy code blocks to modern idioms.
- [Robust API Endpoint Design](prompts/coding/robust_api_design.md) - REST/GraphQL api endpoint design with strict inputs/outputs and rate-limiting rules.
- [Security and Vulnerability Audit](prompts/coding/security_audit.md) - Scan source files or configurations for vulnerabilities (OWASP/CWE).
- [Test-Driven Development (TDD) Implementation](prompts/coding/tdd_implementation.md) - Implement a strict red-green-refactor workflow cycle.

### Debugging
- [Flaky Test and Race Condition Isolator](prompts/debugging/flaky_test_isolator.md) - Isolate timing delays, race conditions, and flaky concurrent behaviors.
- [Memory Leak and Performance Profiling](prompts/debugging/performance_profiling.md) - Locate garbage collection leaks or CPU hotpaths.
- [Systemic Root-Cause Diagnosis](prompts/debugging/root_cause_diagnosis.md) - Construct troubleshooting trees before attempting code fixes.

### Education
- [Active Recall and Spaced Repetition Flashcard Generator](prompts/education/spaced_repetition.md) - Create atomic Q&A deck files ready for Anki.
- [Socratic Method Learning Companion](prompts/education/socratic_learning.md) - Teach difficult concepts with iterative, guiding inquiries.

### Meta
- [Prompt Evaluation and Critique System](prompts/meta/prompt_evaluation.md) - Critique prompts against clarity, robustness, and 12 evaluation criteria.
- [Prompt Optimizer and Generator](prompts/meta/prompt_optimizer.md) - Upgrade weak drafts into high-quality instructions.

### Planning
- [Agile Sprint Goal and Backlog Planner](prompts/planning/sprint_planner.md) - Formulate clean sprint backlogs aligned with velocity and goals.
- [Business Continuity and Disaster Recovery Planner](prompts/planning/bcdr_planner.md) - Prepare technical disaster recovery plans (RTO/RPO).
- [Cost Optimization and FinOps Planner](prompts/planning/finops_planner.md) - Analyze cloud invoices to find underutilized VM waste.
- [Strategic Product Roadmap](prompts/planning/product_roadmap.md) - Formulate high-level plans using ICE/RICE scoring.

### Productivity
- [Decision Matrix and Action Planner](prompts/productivity/decision_matrix.md) - Map priorities into Eisenhower matrices and weighted scoring tables.
- [Deep Work Block Scheduler](prompts/productivity/deep_work.md) - Align daily commitments around physiological cognitive peaks.

### Reasoning
- [Counterfactual Scenario Simulation](prompts/reasoning/counterfactual_simulation.md) - Run "what-if" causal analysis on historical decisions.
- [First-Principles Task Decomposition](prompts/reasoning/first_principles.md) - Deconstruct goals down to atomic truths, bypassing analogy.
- [Multi-Perspective Dialectical Debate](prompts/reasoning/dialectical_debate.md) - Debate complex topics using structured expert personas.
- [Premise-by-Premise Logical Audit](prompts/reasoning/logical_audit.md) - Audit arguments premise-by-premise to spot logical fallacies.
- [Premortem and Risk Mitigation Analysis](prompts/reasoning/premortem_analysis.md) - Pre-identify project failure modes before launching.

### Research
- [Empirical Data Synthesis](prompts/research/empirical_synthesis.md) - Structure affinity diagrams and empirical user personas from field notes.
- [Literature Review and Gap Identification](prompts/research/lit_review.md) - Systematically map academic consensus, tensions, and gaps.
- [Peer Review Simulator](prompts/research/peer_review_simulator.md) - Simulate NeurIPS/CHI peer review processes on drafts.
- [Trend Spotting and Foresight Analysis](prompts/research/trend_spotting.md) - Analyze market signals over multi-year target horizons.

### Writing
- [Microcopy and UX Writing Optimizer](prompts/writing/microcopy_optimizer.md) - Optimize UI notifications, error states, and buttons.
- [Technical Case Study Writer](prompts/writing/technical_case_study.md) - Write engaging, data-driven engineering case studies.
- [Technical Concept Translation](prompts/writing/technical_translation.md) - Translate complex topics via clear analogies to any target audience.
- [UX Content Strategy Audit](prompts/writing/ux_content_audit.md) - Evaluate consistency, accessibility, and brand alignment.

---

## Evaluation & Standards
All templates in this repository are verified for consistency and cleanliness using our custom automated verification suite, ensuring:
- Absolute absence of `TODO`, `FIXME`, or unfinished placeholders.
- Strict formatting compliance.
- Deduplication and semantic uniqueness.
