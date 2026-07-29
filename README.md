# [Uncovering HeterogeneousTreatment Effects: Analysis of the LaLonde NSW (National Supported Work) Data]

## Repository Link

https://github.com/ChetnaLourembam/Causal-Inference-Machine-Learning-Project]

## Description

Evaluating public policy interventions is notoriously difficult because selection bias distorts the picture—people who volunteer for job training already bring different motivations, education levels, and work histories to the table. Traditional regression methods blur these traits together, yielding a single, flat average that hides who actually benefits from the program. To solve this, we applied a Causal Forest framework using Double Machine Learning (DML) to the landmark Lalonde dataset. By first residualizing out background noise and selection bias, then building an ensemble of "honest" causal trees, the model isolates Conditional Average Treatment Effects (CATE) across different demographic profiles. Instead of simply asking whether a policy works on average, this approach maps how individual traits like age, education, and past earnings drive personalized financial returns—transforming a traditional policy review into an actionable, targeted decision tool.

### Task Type

Causal Inference & Heterogeneous Treatment Effect (HTE) Estimation

### Results Summary

#### Best Model Performance
- **Best Model:** Causal Forest via Double Machine Learning
- **Evaluation Metric:** Policy Gain / R^2_D (DML Pseudo- R^2 for CATE heterogeneity)
- **Final Performance:** Average Treatment Effect (ATE): +$1,794 annual earnings lift ($p < 0.01$), CATE Range: -$450 to +$4,200 across individual profiles

#### Model Comparison
- **Baseline Performance:** +$886 lift (significantly attenuated due to selection bias)
- **Improvement Over Baseline:** +102% increase in treatment effect precision by controlling for high-dimensional confounding via DML residualization
- **Best Alternative Model:** +102% increase in treatment effect precision by controlling for high-dimensional confounding via DML residualization

#### Key Insights
- **Most Important Features:**  Pre-program Earnings (re75 & re74): Low historical earners saw the highest relative lift (+230% vs average), Education Level: Higher earnings lift observed in workers with $<12$ years of schooling, Age: Stronger positive treatment response among younger workers ($<25$ years old). 
- **Model Strengths:** Captures non-linear feature interactions naturally; isolates confounding via honest tree splitting without overfitting; estimates personalized treatment effects ($CATE$) rather than a blunt average.
- **Model Limitations:** Sample size constraints in the classic Lalonde dataset limit high-dimensional sub-group granularity; potential for unobserved confounders (e.g., non-quantifiable intrinsic motivation).
- **Business Impact:** Enables targeted policy intervention. Instead of enrolling candidates indiscriminately, allocating the training program to the top 40% most responsive profiles maximizes total economic ROI by ~$1.6\times$ per public dollar spent. 

## Documentation

1. **[Literature Review](0_LiteratureReview/README.md)**
2. **[Dataset Characteristics](1_DatasetCharacteristics/exploratory_data_analysis.ipynb)**
3. **[Baseline Model](2_BaselineModel/baseline_model.ipynb)**
4. **[Model Definition and Evaluation](3_Model/model_definition_evaluation)**
5. **[Presentation](4_Presentation/README.md)**
