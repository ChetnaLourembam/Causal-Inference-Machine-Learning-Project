# [Uncovering HeterogeneousTreatment Effects: Analysis of the LaLonde NSW (National Supported Work) Data]

## Repository Link

https://github.com/ChetnaLourembam/Causal-Inference-Machine-Learning-Project]

## Description

Evaluating public policy interventions is notoriously difficult because selection bias distorts the picture—people who volunteer for job training already bring different motivations, education levels, and work histories to the table. Traditional regression methods blur these traits together, yielding a single, flat average that hides who actually benefits from the program. To solve this, we applied a Causal Forest framework using Double Machine Learning (DML) to the landmark Lalonde dataset. By first residualizing out background noise and selection bias, then building an ensemble of "honest" causal trees, the model isolates Conditional Average Treatment Effects (CATE) across different demographic profiles. Instead of simply asking whether a policy works on average, this approach maps how individual traits like age, education, and past earnings drive personalized financial returns—transforming a traditional policy review into an actionable, targeted decision tool.

### Task Type

Causal Inference & Heterogeneous Treatment Effect (HTE) Estimation

### Results Summary

#### Best Model Performance
- **Best Model:** Causal Forest
- **Evaluation Metric:** Average Treatment Effect (ATE) Stabilization & Covariate Balance (SMD < 0.1)
- **Final Performance:** The Causal Forest estimated an ATE of -$973.91. While the overall average impact was slightly negative, the Individual Treatment Effect (ITE) distribution revealed a long right-tail of specific individuals who experienced significant positive earnings lifts.
- 
#### Model Comparison
- **Baseline Performance:** $1,378.80 ATE (massively inflated due to selection bias and failure to account for baseline poverty levels).
- **Improvement Over Baseline:** Successfully controlled for high-dimensional confounding, mathematically collapsing the demographic differences between the treated and control groups to simulate a randomized trial.
- **Best Alternative Model:** Double Machine Learning (Bayesian Ridge), which provided a highly stable, doubly-robust ATE estimate of $628.43.
  
#### Key Insights
- **Most Important Features:**  Pre-program Earnings (re74 & re75) were the dominant drivers of the treatment effect. The scatter plot analysis revealed a distinct downward trend: individuals with the absolute lowest historical incomes saw the highest positive returns from the training.
- **Model Strengths:** Captures non-linear feature interactions naturally; isolates confounding without overfitting; estimates personalized individual treatment effects (ITE) rather than relying on a misleading global average.
- **Model Limitations:** Sample size constraints in the classic Lalonde dataset limit high-dimensional sub-group granularity; potential for unobserved confounders (e.g., non-quantifiable intrinsic motivation or interview performance).
- **Business Impact:** Enables targeted policy intervention. The data proves this job training program is not a universal solution for unemployment, but rather a highly effective intervention for those in extreme poverty. Allocating future program funding strictly to the lowest pre-intervention income brackets will maximize the economic ROI per public dollar spent.
  
## Documentation

1. **[Literature Review](0_LiteratureReview/README.md)**
2. **[Dataset Characteristics](1_DatasetCharacteristics/exploratory_data_analysis.ipynb)**
3. **[Baseline Model](2_BaselineModel/baseline_model.ipynb)**
4. **[Model Definition and Evaluation](3_Model/model_definition_evaluation)**
5. **[Presentation](4_Presentation/README.md)**
