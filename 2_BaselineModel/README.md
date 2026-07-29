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
- **Data Split:** 80% Training set (491 observations) / 20% Testing set (123 observations)
- **Evaluation Metrics:**
  * Average Treatment Effect (ATE) & p-value: To measure the estimated dollar value impact of the training program and check if the result is statistically significant.
  * MAE: To evaluate the baseline prediction error in plain dollar terms.
  * RMSE: To penalize large prediction errors, which is critical given the zero-inflated and right-skewed income data.
  * $R^2$: To measure how much variation in 1978 earnings my linear model actually explains.
    
### Metric Practical Relevance
* Average Treatment Effect (ATE): In a real-world policy setting, the ATE tells decision-makers whether spending public funds on a job training program actually increases participant earnings. My baseline estimate of $1,378.80 suggests a positive trend, but because the p-value is 0.080, I cannot confidently claim this program worked based on OLS alone.
* MAE ($6,300.31): This metric translates directly into monetary terms—on average, my model's predicted earnings for an individual are off by over $6,300. Considering many people in the dataset earned $0 in 1978, this margin of error is quite high and shows the model struggles to make precise individual income predictions.
* RMSE ($9,051.88): Because RMSE penalizes large mistakes heavily, having an RMSE almost $3,000 higher than my MAE tells me the linear model makes massive prediction errors on high earners (the long tail of the income distribution).
* $R^2$ (0.174): An $R^2$ of 17.4% shows that a basic linear combination of demographics and past earnings leaves over 82% of future income variation unexplained. It reinforces that human income is complex and highly non-linear.

## Next Steps
This baseline model serves as a reference point for evaluating more sophisticated models in the [Model Definition and Evaluation](../3_Model/README.md) phase.
