# Model Definition and Evaluation

**[Notebook](model_definition_evaluation)**


OVERVIEW

After seeing the severe selection bias and limitations of my naive baseline model, I transitioned from traditional predictive modeling to rigorous Causal Inference. My goal in this phase was to isolate the true, unbiased monetary impact of the job training program on 1978 earnings, filtering out the noise of demographics and historical poverty.
To do this, I implemented a progressive suite of models—starting with classical econometrics and ending with state-of-the-art causal machine learning techniques.


MODEL SELECTION

I chose a comprehensive lineup of models to see how increasingly flexible algorithms handle complex, non-linear confounding variables:
* OLS with Controls: My baseline check to see how a standard linear regression handles the covariates.
* Propensity Score Matching (PSM): A classical approach to artificially match treated individuals with nearly identical control neighbors to mimic a randomized trial.
* Inverse Probability Weighting (IPW): Using propensity scores to weight the control group so their overall demographics perfectly balance with the treated group.
* Augmented IPW (AIPW): A "doubly robust" method combining IPW with a predictive regression model.
* T-Learners (Random Forests): Training two completely separate Random Forest models (one for the treated, one for the control) to capture non-linear relationships without mathematical constraints.
* Double Machine Learning (DML): Using machine learning to "partial out" the confounding variables from both the treatment assignment and the outcome variable.
* Causal Forests: An advanced tree-based algorithm designed specifically to estimate Heterogeneous Treatment Effects—telling me exactly who benefited the most.

<img width="1584" height="2184" alt="download (7)" src="https://github.com/user-attachments/assets/ea20a446-8c71-4e9a-bc29-d56ff8d1d295" />


FEATURE ENGINEERING 

Because my models now rely on calculating probabilities (Propensity Scores) and distances (Matching), my feature engineering was strictly focused on ensuring the data was mathematically readable.
* One-Hot Encoding: I converted the categorical race variable into binary columns.
* Preserving Covariates: Unlike standard ML where I might drop highly correlated features, I kept all available demographic and historical earnings covariates (age, education, re74, re75, etc.). This is crucial to satisfy the causal unconfoundedness assumption (ensuring I don't suffer from omitted variable bias).



HYPERPARAMETER TUNING 

* Propensity Scores: I utilized a LogisticRegression model with an extended max_iter=2000 to ensure convergence when calculating the probability of each individual receiving treatment.
* Machine Learning Models: For my T-Learners, I utilized GridSearchCV on my Random Forest Regressors to tune the max_depth and n_estimators. This prevented the trees from overfitting to the highly skewed income data.



EVALUATION METRICS

In causal inference, standard predictive metrics like Accuracy or MSE are secondary because the "true" individual treatment effect is unobservable (I can't see the same person simultaneously take and not take the training). Instead, I evaluated my models using:
* Average Treatment Effect (ATE): Tracking how the estimated dollar impact stabilizes as the models get more advanced.
* Standardized Mean Differences (SMD): Used to evaluate my IPW model. An SMD below 0.1 proves that my weighting successfully balanced the demographics between the two groups.
* Individual Treatment Effects (ITE): Extracting individual-level predictions from my Causal Forest to understand the distribution of the program's impact.

<img width="1584" height="584" alt="download (6)" src="https://github.com/user-attachments/assets/96220359-fa3b-4dff-8bf3-60eee66dee39" />


COMPARATIVE ANALYSIS AND VISUALIZATION

The progression of models revealed exactly why addressing selection bias is critical. My naive baseline (OLS) provided a highly skewed estimate. However, once I applied matching, weighting, and Double Machine Learning, the estimated impact of the job training program became much more realistic and conservative. The advanced ML models successfully filtered out the noise.
I generated six advanced visualizations:
* ATE Comparison Bar Chart: Showing how the treatment effect estimates evolved and stabilized across the 7 models.
* Propensity Score Density: Highlighting the severe initial selection bias (lack of common support) that necessitated these advanced models.
* Covariate Balance (Love Plot): Visually proving that my IPW weights successfully collapsed the demographic differences between the groups to near-zero (SMD < 0.1).
* ITE Distribution: Showing that while the average effect is modest, there is a long tail of individuals who saw massive income boosts.
* Causal Feature Importance: Revealing that a person's historical earnings (re74/re75) were the biggest drivers in determining if the program would help them.
* Treatment Effect vs. Prior Income: A scatter plot demonstrating that the program generated the highest monetary returns for individuals who started with the absolute lowest pre-intervention incomes.

<img width="1584" height="584" alt="download (5)" src="https://github.com/user-attachments/assets/de6000f4-f8bb-4286-93e8-d1f2ad8d961f" />

<img width="1584" height="584" alt="download (4)" src="https://github.com/user-attachments/assets/6537ca2a-cfe1-4287-8b8e-340b21aa7f8b" />
