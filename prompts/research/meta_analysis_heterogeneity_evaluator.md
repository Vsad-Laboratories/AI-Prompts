# Meta-Analysis Study Heterogeneity Evaluator

## Purpose
Analyze quantitative meta-analysis studies, clinical trial aggregations, and empirical effect-size datasets to evaluate statistical heterogeneity ($I^2, \tau^2, Q$-test), identify publication bias, detect outlier study leverage, and perform subgroup moderator analyses.

## Inputs
- `META_ANALYSIS_DATASET`: Table or list of individual studies, sample sizes ($n$), point estimates (Odds Ratios, Risk Ratios, Standardized Mean Differences - Cohen's $d$ / Hedges' $g$), confidence intervals, and study variance.
- `TARGET_EFFECT_MEASURE`: Primary summary metric (e.g., Risk Ratio, Hazard Ratio, Cohen's $d$).
- `SUBGROUP_MODERATORS`: Potential moderating variables (e.g., dosage, geographic region, study design tier, publication year).

## Instructions
1. **Calculate Fixed-Effect vs. Random-Effects Summary**:
   - Compute inverse-variance weighted summary effect sizes under both Fixed-Effect (assuming single underlying true effect) and Random-Effects (DerSimonian-Laird or REML model assuming distribution of true effects) assumptions.
2. **Quantify Statistical Heterogeneity Metrics**:
   - **Cochran's $Q$ Test**: Evaluate $Q$-statistic against Chi-Square distribution ($\text{df} = k - 1$) to test null hypothesis of homogeneity.
   - **Higgins $I^2$ Statistic**: Calculate proportion of total variation across studies due to true heterogeneity rather than sampling error:
     $$I^2 = \max\left(0, \frac{Q - (k - 1)}{Q}\right) \times 100\%$$
     Classify: $0\text{--}40\%$ (Low), $30\text{--}60\%$ (Moderate), $50\text{--}90\%$ (Substantial), $75\text{--}100\%$ (Considerable).
   - **Between-Study Variance ($\tau^2$)**: Calculate tau-squared using DerSimonian-Laird or Restricted Maximum Likelihood (REML) estimators.
3. **Evaluate Publication Bias & Small-Study Effects**:
   - Construct Funnel Plot asymmetry diagnostics.
   - Perform Egger's regression test and Begg's rank correlation test for funnel plot asymmetry.
   - Apply Duval and Tweedie's Trim and Fill method to estimate adjusted effect size after imputing missing small negative studies.
4. **Conduct Subgroup & Sensitivity Analysis**:
   - Perform meta-regression across `SUBGROUP_MODERATORS` to explain sources of heterogeneity ($\tau^2$ reduction).
   - Perform Leave-One-Out (LOO) sensitivity analyses to identify single influential outlier studies driving overall results.

## Constraints
- **Mandatory Heterogeneity Reporting**: Always report $I^2$, $\tau^2$, and Cochran's $Q$ with exact $p$-values.
- **Model Choice Justification**: Enforce Random-Effects model selection whenever $I^2 > 40\%$.
- **Publication Bias Guardrail**: Do not claim zero publication bias based solely on visual inspection; require statistical test results (Egger's test).

## Expected Output Format
```markdown
### 1. Meta-Analysis Summary Effect & Heterogeneity Matrix
- **Total Included Studies ($k$)**: 14 Studies ($N = 12,450$ participants)
- **Primary Effect Metric**: Risk Ratio (RR)

| Model | Summary Effect (RR) | 95% Confidence Interval | $p$-value | $I^2$ Heterogeneity | $\tau^2$ Variance | Cochran's $Q$ ($p$-value) |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| **Fixed-Effect** | 0.74 | [0.68, 0.81] | $<0.001$ | 68.4% | -- | $41.2\ (p < 0.001)$ |
| **Random-Effects (REML)** | **0.68** | **[0.56, 0.82]** | **$<0.001$** | **68.4% (Substantial)** | **0.084** | **$41.2\ (p < 0.001)$** |

### 2. Publication Bias Diagnostics
- **Egger's Regression Test**: $t = 3.42, p = 0.008$ (Statistically significant funnel asymmetry detected)
- **Trim & Fill Imputed Effect**: Adjusted RR = $0.78$ [0.64, 0.94] (4 missing small studies imputed)

### 3. Subgroup Meta-Regression Analysis
| Subgroup Moderator | Included Studies ($k$) | Group RR [95% CI] | $I^2$ Within Group | Heterogeneity Explained ($R^2$) |
| :--- | :--- | :--- | :--- | :--- |
| **High Dose (>100mg)** | 8 | 0.58 [0.48, 0.70] | 22.1% (Low) | **64.2% of $\tau^2$** |
| **Low Dose ($\le$100mg)** | 6 | 0.89 [0.76, 1.04] | 18.5% (Low) | -- |

### 4. Synthesis & Methodological Guidance
- **Primary Finding**: Substantial overall heterogeneity ($I^2 = 68.4\%$) is largely driven by dosage variations ($R^2 = 64.2\%$). High-dosage interventions show robust efficacy (RR = 0.58), whereas low-dosage interventions do not achieve statistical significance.
```

## Evaluation Criteria
- **Statistical Rigor**: Correctly calculates $I^2$, $\tau^2$, Cochran's $Q$, and random-effects weightings.
- **Publication Bias Precision**: Applies Egger's test and Trim-and-Fill corrections accurately.
- **Heterogeneity Resolution**: Explains unexplained variance through systematic subgroup meta-regression.

## Failure Considerations
- **Defaulting to Fixed-Effects**: Using fixed-effect models in the presence of substantial heterogeneity ($I^2 > 50\%$).
- **Ignoring Outlier Influence**: Failing to perform leave-one-out sensitivity analysis on high-leverage studies.
