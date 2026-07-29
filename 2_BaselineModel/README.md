# Baseline Model

**[Notebook](baseline_model.ipynb)**

## Baseline Model Results

### Model Selection
- **Baseline Model Type:** Ordinary Least Squares (OLS) Linear Regression
- **Rationale:** In econometrics and causal inference, starting with a naive OLS linear regression is standard practice. It gives me a clear baseline Average Treatment Effect (ATE) by regressing 1978 earnings (re78) on the treatment indicator (treat) alongside all demographic and historical earnings covariates. This provides a simple benchmark model that my more sophisticated causal models (like Propensity Score Matching) will need to outperform.

### Model Performance
- **Evaluation Metric:** verage Treatment Effect (ATE), MAE, RMSE, and R²
- **Performance Score:**
  * ATE: +$1,378.80 (p-value: 0.080)
  * MAE: $6,300.31
  * RMSE: $9,051.88
  * R²: 0.174
- **Cross-Validation Score:** N/A (Because I used a standard OLS regression to get my causal baseline statistics, I relied on my 80/20 train-test split instead of k-fold cross-validation. I will use cross-validation for tuning my advanced machine learning models later).

### Evaluation Methodology
- **Data Split:** [Train/Validation/Test split ratios, e.g., 70/15/15]
- **Evaluation Metrics:** [List all metrics used and justify why they are appropriate for this problem]

### Metric Practical Relevance
[Explain the practical relevance and business impact of each chosen evaluation metric. How do these metrics translate to real-world performance and decision-making? What do the metric values mean in the context of your specific problem domain?]

## Next Steps
This baseline model serves as a reference point for evaluating more sophisticated models in the [Model Definition and Evaluation](../3_Model/README.md) phase.
