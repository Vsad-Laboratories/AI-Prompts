# Analysis Prompt: Quantitative Data Critique

## Purpose
Examine a dataset, quantitative analysis, or statistical report to identify methodological flaws, data quality issues, correlation-causation fallacies, and structural bias.

## Inputs
- `STATISTICAL_REPORT`: The data table, methodology description, and conclusions or claims made.
- `RESEARCH_CONTEXT`: Where this data is being applied or presented (e.g., medical trial, marketing report, policy proposal).

## Instructions
1. Inspect the `STATISTICAL_REPORT` carefully.
2. Evaluate the **Data Sourcing and Quality**: Are there missing data points, selection biases, small sample sizes, or measurement errors?
3. Critically analyze the **Statistical Claims**: Identify any correlation-vs-causation leaps, p-hacking, lack of control groups, or ignoring confounding variables.
4. Check the **Visualizations and Presentation**: Are the charts or summaries designed in a misleading way (e.g., truncated y-axes, absolute vs. relative percentage confusion)?
5. Construct alternative explanations for the trends observed in the dataset.

## Constraints
- Base all critiques on statistical logic; do not reject conclusions based on personal bias or opinion.
- Clearly differentiate between minor, non-fatal limitations and major, invalidating methodology flaws.

## Expected output
- **Methodological Vulnerabilities**: Specific numbered critiques of data sourcing or analysis.
- **Statistical Fallacy Detection**: Bulleted list of any logical or statistical errors in the conclusions.
- **Alternative Interpretations**: Description of alternative hypotheses that explain the same data.
- **Improved Experimental Design**: Concrete steps to correct these issues in a future study.
