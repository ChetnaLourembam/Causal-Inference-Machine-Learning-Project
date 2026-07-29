# Literature Review

Approaches or solutions that have been tried before on similar projects.

**SUMMARY OF MAIN LITERATURE**:

- **Source 1**: Evaluating the Econometric Evaluations of Training Programs with Experimental, Robert J. LaLonde, The American Economic Review, Sep., 1986, Vol. 76, No. 4 (Sep., 1986), pp. 604-620

  - **Link: (https://business.baylor.edu/scott_cunningham/teaching/lalonde-1986.pdf)**
  - **Objective**: LaLonde set out to test a core question in empirical economics: can conventional non-experimental econometric methods actually replicate the true causal effects measured by a randomized controlled trial (RCT)?
  - **Methods**: He analyzed data from the randomized National Supported Work (NSW) Demonstration job training experiment, focusing on a primary subset of 445 male participants (alongside a broader sample of AFDC women, ex-addicts, ex-offenders, and high school dropouts). To mimic an observational study, he discarded the experimental control group and replaced it with non-experimental comparison groups constructed from major public survey datasets (the PSID and CPS-SSA). He then ran these non-experimental samples through standard econometric routines—including cross-sectional OLS, difference-in-differences (fixed effects), models controlling for pre-training earnings, and Heckman two-step selection bias corrections.
  - **Outcomes**: The actual experimental baseline showed that the program increased post-training earnings by ~$851 for AFDC women and ~$886 for male participants. The non-experimental estimates, however, swung wildly depending on the choice of comparison group and model specification—ranging anywhere from negative values to over +$3,000. Most importantly, even when non-experimental models successfully passed standard specification checks (like verifying pre-training earnings comparability), they still routinely failed to hit the true experimental benchmark.
  - **Relation to the Project**: This paper is the bedrock benchmark for the entire study. By demonstrating that traditional econometric tools struggle to consistently recover true causal impacts from observational data, LaLonde established the classic stress test in causal inference. The project picks up right where he left off—testing whether modern double machine learning (DML) and CATE estimators (like Causal Forests and BCF) can finally overcome these long-standing estimation biases

- **Source 2**: Chernozhukov, V., Chetverikov, D., Demirer, M., Duflo, E., Hansen, C., Newey, W., & Robins, J. (2018). Double/debiased machine learning for treatment and structural parameters. The Econometrics Journal, 21(1), C1–C68.

  - **Link: (https://academic.oup.com/ectj/article/21/1/C1/5056401)**
  - **Objective**: The authors address a fundamental challenge in causal inference: how to use flexible, high-dimensional machine learning (ML) models for nuisance functions (like propensity scores or outcome predictions) without introducing heavy regularization bias or overfitting into the main causal estimate.
  - **Methods**: The paper introduces Double/Debiased Machine Learning (DML), built on two essential mathematical mechanisms:  Neyman Orthogonal Scores: Re-formulating estimating equations so that local errors in predicting nuisance parameters do not bias the primary target parameter (making the moment conditions locally insensitive).  Cross-Fitting: A specialized sample-splitting technique where data used to train ML nuisance models is kept strictly separate from data used to estimate the target causal effect, completely removing overfitting bias.  They prove that under cross-fitting, low-dimensional target parameters recover root-$N$ consistency and asymptotic normality, allowing for valid statistical inference.
  - **Outcomes**: Standard "naive" plug-in ML estimates suffer from severe regularization bias, leading to biased treatment effect estimates and invalid confidence intervals.  DML successfully eliminates this bias, achieving centered Gaussian distributions and enabling valid, uniformly asymptotically accurate confidence bands across a wide array of ML estimators (e.g., Random Forests, Lasso, Neural Networks, and Ensembles)
  - **Relation to the Project**: This paper provides the theoretical justification for Method 5 (DML) and the overall pre-processing pipeline in your research benchmark. Specifically, it proves why your 5-fold cross-fitting and residualization step ($\tilde{Y} = Y - \hat{Y}$ and $\tilde{W} = W - \hat{W}$) works mathematically to yield unbiased treatment effect estimates when applying complex machine learning algorithms to observational data. 

- **Source 3**: Wager, S., & Athey, S. (2018). Estimation and Inference of Heterogeneous Treatment Effects using Random Forests. Journal of the American Statistical Association, 113(523), 1228–1242.

  - **Link: (https://www.tandfonline.com/doi/full/10.1080/01621459.2017.1319839)**
  - **Objective**: The authors address the challenge of discovering individual-level, non-parametric heterogeneous treatment effects (Conditional Average Treatment Effects, or CATEs) without falling into the trap of mining data for spurious subgroups.
  - **Methods**: They adapt Leo Breiman’s Random Forest algorithm into a specialized Causal Forest explicitly designed to estimate continuous treatment heterogeneity $\tau(x) = \mathbb{E}[Y^{(1)} - Y^{(0)} \vert{} X = x]$ rather than standard outcome prediction.To guarantee valid inference, they enforce "Honesty" in tree construction—splitting the training sample so that one subsample builds the tree structure and a separate holdout subsample estimates the leaf-level treatment effects.They prove asymptotic properties for subsampled honest forests and establish that an adaptation of Efron’s Infinitesimal Jackknife provides consistent asymptotic variance estimates for constructing pointwise confidence intervals
  - **Outcomes**: Causal Forest predictions are proven to be pointwise consistent for the true treatment effect and follow an asymptotically Gaussian, centered sampling distribution.In empirical simulations, Causal Forests significantly outperform non-adaptive classical approaches like $k$-Nearest Neighbors ($k$-NN) matching, especially as feature dimensions grow and in the presence of noise/irrelevant covariates
  - **Relation to the Project**: This paper directly provides the mathematical foundation and methodology for Method 7 (Causal Forest) in your benchmarking research. It explains how tree-based models can split data to isolate moderator variables (such as age, education, and pre-training earnings) to uncover real treatment effect heterogeneity without falsely identifying random noise as true variation.
 




**SUPPORTING LITERATURE & METHODOLOGICAL FRAMEWORK**:
- **Propensity Score Matching (PSM)**
Dehejia, R. H., & Wahba, S. (2002). Propensity score-matching methods for nonexperimental causal studies. Review of Economics and Statistics, 84(1), 151–161. https://doi.org/10.1162/003465302317331982

- **Inverse Probability Weighting (IPW)**
Robins, J. M., Hernán, M. Á., & Brumback, B. (2000). Marginal structural models and causal inference in epidemiology. Epidemiology, 11(5), 550–560. https://doi.org/10.1097/00001648-200009000-00011

- **Augmented Inverse Probability Weighting (AIPW)**
Glynn, A. N., & Quinn, K. M. (2010). An introduction to the augmented inverse propensity weighted estimator. Political Analysis, 18(1), 36–56. 

- **T-Learner (ML Meta-Learner)**
Künzel, S. R., Sekhon, J. S., Bickel, P. J., & Yu, B. (2019). Metalearners for estimating heterogeneous treatment effects using machine learning. Proceedings of the National Academy of Sciences, 116(10), 4156–4165. https://doi.org/10.1073/pnas.1804597116

- **Bayesian Causal Forest (BCF)**
Hahn, P. R., Murray, J. S., & Carvalho, C. M. (2020). Bayesian regression tree models for causal inference: Regularization, confounding, and heterogeneous effects. Bayesian Analysis, 15(3), 965–1056. https://doi.org/10.1214/19-BA1195


