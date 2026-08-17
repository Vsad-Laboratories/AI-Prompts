# Bayesian Hypothesis Updating Framework

## Purpose
Execute rigorous probabilistic reasoning and quantitative belief updating across competing hypotheses when presented with new evidence, noisy diagnostic data, or ambiguous operational signals, preventing base rate neglect and confirmation bias.

## Inputs
- `COMPETING_HYPOTHESES`: Exhaustive set of mutually exclusive hypotheses ($H_1, H_2, \dots, H_n$).
- `PRIOR_PROBABILITIES`: Baseline prior probabilities assigned to each hypothesis ($P(H_1), P(H_2)$) based on historical base rates.
- `NEW_EVIDENCE_OBSERVED`: Observed data, telemetry anomaly, experimental result, or log event ($E$).
- `DIAGNOSTIC_LIKELIHOODS`: Conditional probability likelihoods of observing evidence $E$ given each hypothesis ($P(E|H_1), P(E|H_2)$).

## Instructions
1. **Define Prior Probability Distribution ($P(H_i)$)**: Establish explicit prior baseline probabilities based on long-term historical base rates. Verify $\sum P(H_i) = 1.0$.
2. **Evaluate Diagnostic Likelihoods ($P(E|H_i)$)**: Determine the conditional probability of observing `NEW_EVIDENCE_OBSERVED` under each competing hypothesis:
   - $P(E|H_1)$: Likelihood evidence appears if $H_1$ is true (True Positive Rate / Sensitivity).
   - $P(E|\neg H_1)$: Likelihood evidence appears if $H_1$ is false (False Positive Rate).
3. **Calculate Total Marginal Likelihood ($P(E)$)**: Apply the Law of Total Probability:
   $$P(E) = \sum_{i=1}^n P(E|H_i) \cdot P(H_i)$$
4. **Compute Posterior Probabilities ($P(H_i|E)$)**: Apply Bayes' Theorem:
   $$P(H_i|E) = \frac{P(E|H_i) \cdot P(H_i)}{P(E)}$$
5. **Formulate Bayes Factor / Likelihood Ratio**: Compute the relative strength of evidence between top competing hypotheses:
   $$\text{Bayes Factor} (K) = \frac{P(E|H_1)}{P(E|H_2)}$$
6. **Determine Information Value of Next Tests**: Recommend high-information diagnostic tests or experiments designed to maximize expected information gain (entropy reduction) for subsequent updating turns.

## Constraints
- **Strict Mathematical Balance**: Posterior probabilities MUST sum to exactly $1.0$ ($100\%$).
- **Anti-Base Rate Neglect Guardrail**: Never calculate posterior probability without explicitly factoring in prior base rates $P(H_i)$.
- **Explicit Sensitivity/Specificity Modeling**: Always account for false positive probabilities in telemetry or diagnostic checks.

## Expected Output Format
```markdown
### 1. Bayesian Updating Matrix
- **Observed Evidence ($E$)**: High CPU spike + Redis connection pool timeout in Region A

| Hypothesis ($H_i$) | Prior $P(H_i)$ | Likelihood $P(E\|H_i)$ | Unnormalized Joint $P(E \cap H_i)$ | Posterior $P(H_i\|E)$ | Change ($\Delta$) |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **$H_1$: Redis Memory Exhaustion** | 0.15 | 0.85 | $0.15 \times 0.85 = 0.1275$ | **62.3%** | +47.3% |
| **$H_2$: Network Partition** | 0.05 | 0.90 | $0.05 \times 0.90 = 0.0450$ | **22.0%** | +17.0% |
| **$H_3$: Garbage Collection Pause** | 0.80 | 0.04 | $0.80 \times 0.04 = 0.0320$ | **15.7%** | -64.3% |
| **Total Marginal $P(E)$** | **1.00** | -- | **0.2045** | **100.0%** | -- |

### 2. Bayes Factor & Evidence Assessment
- **Bayes Factor ($H_1$ vs $H_3$)**: $K = \frac{0.85}{0.04} = 21.25$
- **Evidence Strength**: Strong evidence favoring $H_1$ over $H_3$ (Redis Memory Exhaustion vs GC Pause).

### 3. Maximum Information Gain Next Action
- **Recommended Test**: Execute `redis-cli info memory` to check `used_memory_rss`.
- **Expected Information Gain**: High entropy reduction ($\Delta H > 1.2\text{ bits}$).
```

## Evaluation Criteria
- **Mathematical Accuracy**: Bayes' Theorem calculations and total marginal probability are mathematically exact.
- **Base Rate Integration**: Properly weights priors to avoid overreacting to noisy diagnostic alerts.
- **Actionable Testing Guidance**: Identifies subsequent experiments that maximize expected information gain.

## Failure Considerations
- **Base Rate Neglect**: Jump to high posterior probability based on a diagnostic alert without considering that the underlying event is extremely rare.
- **Ignoring False Positives**: Assuming $P(E|\neg H) = 0$, leading to overconfident posterior estimates.
