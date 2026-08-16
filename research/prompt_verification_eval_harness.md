# Model-Agnostic Prompt Verification and Evaluation Harness

## Executive Summary
Evaluating prompt performance across distinct LLM architectures (e.g., OpenAI GPT-4o, Anthropic Claude 3.5 Sonnet, Google Gemini 1.5 Pro) presents significant challenges due to variance in tokenization, instruction compliance style, and context processing. This research document defines a lightweight, standardized, model-agnostic prompt evaluation framework. It includes quantitative scoring dimensions, automated schema verification protocols, edge-case test suite synthesis, and benchmark metrics.

---

## 1. Quantitative Evaluation Dimensions

Every prompt in production environments should be scored against 5 key dimensions on a normalized 1-10 scale:

```text
    Instruction Adherence (30%)
            │
            ├────── Output Schema Compliance (25%)
            │
            ├────── Boundary & Constraint Resistance (20%)
            │
            ├────── Context & Token Efficiency (15%)
            │
            └────── Cross-Model Stability (10%)
```

### Evaluation Rubric

| Metric | Description | Scoring Criteria (1-10) |
| :--- | :--- | :--- |
| **Instruction Adherence (IA)** | Degree to which the LLM executes all explicitly specified steps without skipping steps. | **10**: 100% steps executed in order.<br>**1**: Ignores multi-step instructions. |
| **Output Schema Compliance (OSC)** | Adherence to target format (e.g., exact Markdown headers, JSON schema keys, tabular structures). | **10**: Perfectly valid schema formatting.<br>**1**: Freeform text violating output requirements. |
| **Boundary & Constraint Resistance (BCR)** | Ability to obey negative constraints (e.g., "Do NOT mention X", token limits, parameter safety). | **10**: Zero constraint violations under stress.<br>**1**: Frequently breaks negative instructions. |
| **Context & Token Efficiency (CTE)** | Information density and minimization of overhead tokens relative to task complexity. | **10**: Maximum conciseness without factual loss.<br>**1**: Excessive verbosity and filler phrases. |
| **Cross-Model Stability (CMS)** | Variance in output quality when executed across GPT, Claude, Gemini, and open weights (Llama 3). | **10**: Identical structural quality across all models.<br>**1**: Works on only one specific model. |

---

## 2. Test Suite Construction Methodology

To evaluate a prompt, construct a 3-tier test dataset (`test_cases.json`):

1. **Baseline Inputs**: Standard, clean, typical user queries.
2. **Complex / Multi-Constraint Inputs**: Long-context inputs with nested requirements.
3. **Adversarial / Edge-Case Inputs**: Inputs with missing variables, contradicting data, prompt injection attempts, or extreme boundaries.

### Example Evaluation Case Definition
```json
{
  "prompt_id": "prompts/coding/robust_api_design.md",
  "test_cases": [
    {
      "case_id": "TC_BASE_01",
      "inputs": {
        "ENDPOINT_NAME": "/v1/users/checkout",
        "BUSINESS_LOGIC": "Process shopping cart payment and trigger order confirmation email."
      },
      "expected_assertions": [
        "contains_section: Endpoint Specification",
        "contains_section: Error Handling Matrix",
        "valid_json_schema: true",
        "no_forbidden_phrases: ['As an AI', 'Sure, here is']"
      ]
    }
  ]
}
```

---

## 3. Automated Output Verification Schema

An evaluation harness validates LLM responses against expected schema contracts:

```python
# Conceptual Verification Logic
def verify_prompt_output(response_text: str, assertions: dict) -> dict:
    results = {"passed": True, "failed_assertions": []}

    # 1. Structural Section Check
    for section in assertions.get("required_sections", []):
        if f"## {section}" not in response_text and f"### {section}" not in response_text:
            results["passed"] = False
            results["failed_assertions"].append(f"Missing section: {section}")

    # 2. Negative Phrase Check
    for phrase in assertions.get("forbidden_phrases", []):
        if phrase.lower() in response_text.lower():
            results["passed"] = False
            results["failed_assertions"].append(f"Contains forbidden phrase: {phrase}")

    return results
```

---

## 4. Benchmark Scoring Matrix
Calculating the overall **Prompt Quality Index (PQI)**:

$$\text{PQI} = (0.30 \times \text{IA}) + (0.25 \times \text{OSC}) + (0.20 \times \text{BCR}) + (0.15 \times \text{CTE}) + (0.10 \times \text{CMS})$$

- **PQI $\ge$ 8.5**: Production-Ready
- **7.0 $\le$ PQI $<$ 8.5**: Needs Optimization
- **PQI $<$ 7.0**: Needs Prompt Decomposition / Redesign
