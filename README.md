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
- [Multi-Agent Orchestration Protocol](prompts/agents/agent_orchestration.md) - Coordinate and orchestrate multiple specialized AI agents working together toward a complex goal, ensuring clear task handoff, conflict resolution, and information convergence.
- [Autonomous Agent Persona Architect](prompts/agents/agent_persona.md) - Design a highly robust, instruction-compliant, and state-aware persona for an autonomous AI agent or system of cooperating agents.
- [Agent Prompt Injection Guard](prompts/agents/agent_prompt_injection_guard.md) - Inspect, sanitize, and validate user inputs to protect LLM agents and system pipelines against indirect and direct prompt injection attacks.
- [Human-in-the-Loop Collaboration Protocol](prompts/agents/human_in_the_loop.md) - Design a highly reliable collaboration protocol that lets an autonomous AI agent smoothly escalate complex, edge-case, or high-risk tasks to a human supervisor, and integrate human feedback back into its workflow.
- [Multi-Agent Blackboard Orchestrator](prompts/agents/multi_agent_blackboard_orchestrator.md) - Coordinate and orchestrate multiple specialized AI agents using a shared Blackboard pattern to solve complex, multi-step workflows cooperatively.
- [Stateful Dialogue Flow](prompts/agents/stateful_dialogue_flow.md) - Design a state-aware agent dialogue manager that maintains conversational context, user intent history, and handles multi-turn state transitions reliably.

### Analysis
- [Cloud Architecture FinOps Audit](prompts/analysis/cloud_architecture_finops_audit.md) - Analyze cloud resource utilization and service bills to identify wastage, evaluate cost efficiency, and formulate cloud cost optimization strategies.
- [Competitive Intelligence Synthesis](prompts/analysis/competitive_intelligence.md) - Synthesize messy, unstructured competitive information, product releases, and market news to reveal competitor strategies, strengths, weaknesses, and potential market gaps.
- [Root Cause Analysis and Ishikawa Diagrammer](prompts/analysis/ishikawa_rca.md) - Structure a systematic Root Cause Analysis (RCA) using an Ishikawa (Fishbone) model to map, analyze, and resolve serious operational or process failures.
- [Product-Market Fit Survey Analyzer](prompts/analysis/product_market_fit_survey_analyzer.md) - Analyze quantitative and qualitative product-market fit (PMF) survey responses to identify core user personas, feature priorities, and key drivers of user retention.
- [Quantitative Data Critique](prompts/analysis/quantitative_critique.md) - Examine a dataset, quantitative analysis, or statistical report to identify methodological flaws, data quality issues, correlation-causation fallacies, and structural bias.
- [Qualitative Sentiment Synthesis](prompts/analysis/sentiment_synthesis.md) - Synthesize unstructured qualitative comments from surveys, app reviews, or feedback forums into clear, clustered emotional sentiments and behavioral trends.
- [System Dependency Risk Auditor](prompts/analysis/system_dependency_risk_auditor.md) - Identify, assess, and catalog structural and single-point-of-failure (SPOF) risks within software architectural dependencies, libraries, and external systems.
- [UI/UX Heuristic Evaluation](prompts/analysis/ui_ux_heuristic_evaluation.md) - Evaluate a user interface's design, flow, and user experience against Jakob Nielsen's 10 usability heuristics and accessibility standards.

### Coding
- [Code Review and Architecture Guide](prompts/coding/code_review.md) - Simulate a rigorous, senior-level code review of a pull request or code file, evaluating its architecture, readability, performance, test coverage, and correctness.
- [CSS Grid and Flexbox Troubleshooter](prompts/coding/css_grid_flexbox_troubleshooter.md) - Inspect, debug, and optimize complex frontend layout code using CSS Grid and Flexbox to resolve responsive design, alignment, overflow, and rendering issues across modern browsers.
- [Legacy Code Refactoring and Modernization](prompts/coding/legacy_refactoring.md) - Safely refactor, clean up, and modernize legacy code while preserving its exact functionality and performance characteristics.
- [Regex Engineering](prompts/coding/regex_engineering.md) - Design, construct, and optimize highly precise, readable, and safe regular expressions to parse complex strings while mitigating Catastrophic Backtracking.
- [Robust API Endpoint Design](prompts/coding/robust_api_design.md) - Design a highly secure, performant, resilient, and well-documented REST or GraphQL API endpoint that handles error cases gracefully and handles load efficiently.
- [Secure Secrets Management](prompts/coding/secure_secrets_management.md) - Design and implement programmatic patterns, environment controls, and pipeline architectures to securely manage application secrets, API keys, and certificates.
- [Security and Vulnerability Audit](prompts/coding/security_audit.md) - Examine production code or system configurations to detect common security vulnerabilities, architectural security flaws, or compliance risks.
- [SQL Query Optimization](prompts/coding/sql_query_optimization.md) - Optimize slow-running SQL queries by analyzing their execution plans, indexing strategies, table structures, and rewrite opportunities to achieve maximum efficiency and minimal resource utilization.
- [System Design Architect](prompts/coding/system_design_architect.md) - Design high-performance, fault-tolerant, scalable, and secure system architectures for web applications or distributed microservices based on specific scaling requirements.
- [Test-Driven Development (TDD) Implementation](prompts/coding/tdd_implementation.md) - Generate highly reliable, modular, and self-documenting code by enforcing a strict Test-Driven Development (TDD) workflow cycle.
- [TypeScript Type Gymnastics](prompts/coding/typescript_type_gymnastics.md) - Design, implement, and audit complex, compile-time safe, and highly optimized TypeScript utility types for type-driven APIs and library architectures.

### Debugging
- [API Latency Bottleneck Profiler](prompts/debugging/api_latency_bottleneck_profiler.md) - Inspect execution profiles, flame graphs, and network telemetry to localize and resolve latency bottlenecks in high-throughput API endpoints.
- [Database Deadlock Resolver](prompts/debugging/database_deadlock_resolver.md) - Analyze transaction concurrency flows, lock escalations, and thread behavior to resolve database deadlock situations.
- [Distributed Tracing Debugger](prompts/debugging/distributed_tracing_debug.md) - Isolate latency bottlenecks and propagation issues in microservice architectures by tracing requests across distributed system spans.
- [Flaky Test and Race Condition Isolator](prompts/debugging/flaky_test_isolator.md) - Inspect, isolate, and debug intermittent test failures ("flaky tests") or suspected concurrent race conditions in multi-threaded/async code.
- [Kubernetes Pod Failure Analyzer](prompts/debugging/kubernetes_pod_failure_analyzer.md) - Diagnose, debug, and formulate remediation steps for failing Kubernetes workloads, pods, and container clusters.
- [Memory Leak and Performance Profiling](prompts/debugging/performance_profiling.md) - Examine application behaviors, logs, and profiling summaries to locate, explain, and fix memory leaks or CPU bottlenecks.
- [Systemic Root-Cause Diagnosis](prompts/debugging/root_cause_diagnosis.md) - Guide an engineer through diagnosing a complex, intermittent, or systemic software bug, focusing on isolating the bug rather than guessing at fixes.

### Education
- [Concept Map Generator](prompts/education/concept_map_generator.md) - Deconstruct a complex scientific or technical concept into a highly structured, relational, and visual hierarchy of subconcepts to facilitate accelerated Socratic learning.
- [Socratic Method Learning Companion](prompts/education/socratic_learning.md) - Teach complex concepts, theories, or mathematical techniques using the Socratic method of dialogue, asking guiding questions rather than directly giving answers.
- [Active Recall and Spaced Repetition Flashcard Generator](prompts/education/spaced_repetition.md) - Convert lectures, textbook chapters, or technical papers into highly optimized active recall questions and spaced repetition schedule formats.

### Meta
- [Few-Shot Example Generator](prompts/meta/few_shot_example_generator.md) - Synthesize highly diverse, contextually accurate, and edge-case-heavy few-shot examples to optimize the in-context learning of downstream prompts.
- [Negative Constraint Compiler](prompts/meta/negative_constraint_compiler.md) - Analyze and translate complex negative instructions, constraints, and safety guidelines into highly robust, model-compliant prompt instructions.
- [Prompt Evaluation and Critique System](prompts/meta/prompt_evaluation.md) - Systematically review, critique, and grade an existing prompt against 12 core criteria to identify weaknesses, redundancies, or hidden assumptions.
- [Prompt Optimizer and Generator](prompts/meta/prompt_optimizer.md) - Optimize a basic, unstructured, or weak user prompt into a high-quality, professional, and instruction-compliant prompt.

### Planning
- [Business Continuity and Disaster Recovery Planner](prompts/planning/bcdr_planner.md) - Formulate a practical Business Continuity and Disaster Recovery (BCDR) plan to handle critical infrastructure failures, security breaches, or unexpected outages.
- [Cost Optimization and FinOps Planner](prompts/planning/finops_planner.md) - Analyze cloud architecture, service usage logs, or invoice bills to plan concrete cloud cost reductions (FinOps) without degrading system performance or reliability.
- [IT Disaster Recovery Tabletop](prompts/planning/it_disaster_recovery_tabletop.md) - Design, coordinate, and evaluate a realistic IT disaster recovery tabletop simulation to test engineering readiness, response plans, and service restoration speed.
- [OKR Alignment Mapper](prompts/planning/okr_alignment_mapper.md) - Formulate company-wide Objectives and Key Results (OKRs) and map them systematically down to team-level and individual contributor (IC) targets.
- [Strategic Product Roadmap](prompts/planning/product_roadmap.md) - Formulate a long-term, high-impact product roadmap that balances technical debt, user demands, strategic business goals, and resource constraints.
- [SOC2 Compliance Gap Analysis](prompts/planning/soc2_compliance_gap_analysis.md) - Analyze organization-wide technical controls, policies, and workflows to identify gaps in achieving SOC 2 Type II compliance (Trust Services Criteria).
- [Agile Sprint Goal and Backlog Planner](prompts/planning/sprint_planner.md) - Convert a list of high-priority backlog issues into a highly focused, balanced, and commitment-ready sprint plan for a development team.

### Productivity
- [Decision Matrix and Action Planner](prompts/productivity/decision_matrix.md) - Resolve decision paralysis or prioritisation confusion when facing multiple competing, high-stakes options or tasks.
- [Deep Work Block Scheduler](prompts/productivity/deep_work.md) - Optimize a daily schedule around cognitive peaks, energy levels, and professional responsibilities to guarantee 3-4 hours of uninterrupted "deep work."
- [Prioritized Inbox Triage](prompts/productivity/prioritized_inbox_triage.md) - Automate email and messaging triage by analyzing incoming message content, sender urgency, and scheduling actions based on a matrix of priority.

### Reasoning
- [Cognitive Bias Mitigator](prompts/reasoning/cognitive_bias_mitigator.md) - Examine personal, professional, or organizational reasoning to identify, dissect, and actively mitigate cognitive biases (e.g., confirmation bias, anchoring, loss aversion).
- [Counterfactual Scenario Simulation](prompts/reasoning/counterfactual_simulation.md) - Examine a past event, product failure, or major decision by simulating "counterfactual" scenarios (what-if analysis) to extract deep organizational, technical, or strategic lessons.
- [Multi-Perspective Dialectical Debate](prompts/reasoning/dialectical_debate.md) - Synthesize high-quality decisions or analyze complex topics by simulating a structured dialectical debate between multiple expert personas holding opposing viewpoints, leading to a unified synthesis.
- [First-Principles Task Decomposition](prompts/reasoning/first_principles.md) - Deconstruct any complex task, technical problem, or creative challenge into its foundational physical, logical, or mathematical elements. This prompt forces the AI to avoid analogy or standard superficial steps, analyzing the problem from "first principles" to rebuild a solution from scratch.
- [Game-Theoretic Decision Maker](prompts/reasoning/game_theoretic_decision.md) - Formulate optimal strategic decisions in competitive, multi-agent scenarios by applying game theory, Nash Equilibrium, and payoff matrix optimizations.
- [Premise-by-Premise Logical Audit](prompts/reasoning/logical_audit.md) - Examine a highly complex argument, policy claim, or philosophical point to verify its structural logic by breaking it down into distinct premises and auditing each one.
- [Premortem and Risk Mitigation Analysis](prompts/reasoning/premortem_analysis.md) - Prevent failures before they happen by imagining a scenario where a project or idea has completely failed, identifying all plausible causes of that failure, and constructing mitigation strategies.
- [Second-Order Effects Analysis](prompts/reasoning/second_order_effects_analysis.md) - Forecast and map the indirect, long-term, systemic, and unintended consequences of complex business or technical decisions.

### Research
- [Clinical Trial Protocol Reviewer](prompts/research/clinical_trial_protocol_reviewer.md) - Analyze biomedical and clinical trial protocols to evaluate patient safety measures, statistical power, study design robustness, and regulatory compliance.
- [Empirical Data Synthesis](prompts/research/empirical_synthesis.md) - Synthesize qualitative and quantitative research findings from interviews, user research, or field observations into coherent user insights and archetypes.
- [Expert Interview Protocol Designer](prompts/research/expert_interview_protocol_designer.md) - Design highly focused, bias-free, and deep expert interview guides to extract technical, structural, or industry insights.
- [Literature Review and Gap Identification](prompts/research/lit_review.md) - Systematically review a collection of papers or academic summaries to extract themes, identify conflicting evidence, map the current state-of-the-art, and expose critical "research gaps."
- [Meta-Analysis Evidence Synthesizer](prompts/research/meta_analysis_evidence_synthesizer.md) - Synthesize quantitative findings, effect sizes, and statistical confidence levels from multiple academic or empirical research papers to form a unified consensus summary.
- [Patent Novelty Search](prompts/research/patent_novelty_search.md) - Perform systematic, rigorous prior art audits and novelty analyses for patent applications, ensuring technical inventions meet strict patentability criteria.
- [Peer Review Simulator](prompts/research/peer_review_simulator.md) - Simulate an academic peer-review process (such as for a top-tier computer science or scientific journal/conference) to evaluate the methodology, claims, novelty, and rigor of a draft paper or research idea.
- [Trend Spotting and Foresight Analysis](prompts/research/trend_spotting.md) - Examine industry news, patent filings, academic abstracts, or market events to identify emerging macro trends, map their trajectories, and assess their strategic impact.

### Writing
- [Microcopy and UX Writing Optimizer](prompts/writing/microcopy_optimizer.md) - Optimize UI text, buttons, modals, error messages, and onboarding microcopy to improve user clarity, conversion, and task success rates.
- [Press Release Synthesizer](prompts/writing/press_release_synthesizer.md) - Synthesize raw product documentation, engineering breakthroughs, or business milestones into professional, media-ready, and SEO-optimized press releases.
- [Technical Case Study Writer](prompts/writing/technical_case_study.md) - Transform a complex project implementation, software release, or system recovery event into a compelling, professional, and readable engineering or business case study.
- [Technical Concept Translation](prompts/writing/technical_translation.md) - Translate highly complex, technical, or scientific concepts into clear, engaging, and accurate explanations tailored specifically for non-technical audiences or distinct reader personas.
- [UX Content Strategy Audit](prompts/writing/ux_content_audit.md) - Audit an entire website, product module, or set of user-facing communications to assess terminology consistency, brand voice compliance, and user comprehension.

---

## Evaluation & Standards
All templates in this repository are verified for consistency and cleanliness using our custom automated verification suite, ensuring:
- Absolute absence of `TODO`, `FIXME`, or unfinished placeholders.
- Strict formatting compliance.
- Deduplication and semantic uniqueness.
