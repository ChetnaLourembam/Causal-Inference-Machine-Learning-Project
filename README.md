# [Uncovering Hetrogeneous Treatment Effects: A Causal Forest Analysis of the LaLonde NSW Data]

## Repository Link

https://github.com/ChetnaLourembam/Causal-Inference-Machine-Learning-Project]

## Description

[Evaluating the true economic impact of public policy interventions is notoriously difficult due to selection bias. In labor economics, simply comparing individuals who participated in a job training program against those who didn't yields misleading results, as volunteers often possess different baseline motivations, education levels, or earnings histories. Traditional econometric methods frequently miss how these underlying characteristics interact, failing to show for whom a policy actually works.

This project applies a Causal Forest (Generalized Random Forest) framework—a cutting-edge fusion of causal inference and machine learning—to the landmark Lalonde National Supported Work (NSW) dataset.

Instead of computing a single, flat average, the approach utilizes Double Machine Learning (DML) to isolate and "residualize" the effects of selection bias. By building an ensemble of "honest" causal trees, the model splits the data to uncover Conditional Average Treatment Effects (CATE). This allows us to map exactly how an individual's unique demographic profile (age, education, and pre-program earnings) drives their personalized financial return from the program, transforming a blunt policy evaluation into a targeted, data-driven optimization tool.]

### Task Type

[Causal Forest]

### Results Summary

#### Best Model Performance
- **Best Model:** [Name and type of the best-performing model"]
- **Evaluation Metric:** [Primary metric used, e.g., Accuracy, F1-Score, MSE, MAE]
- **Final Performance:** [Best score achieved, e.g., 95% accuracy, F1-score of 0.87, MSE of 0.12]

#### Model Comparison
- **Baseline Performance:** [Baseline model performance for comparison]
- **Improvement Over Baseline:** [Quantitative improvement, e.g., "+12% accuracy", "25% reduction in MSE"]
- **Best Alternative Model:** [Second-best model and its performance]

#### Key Insights
- **Most Important Features:** [Top 3-5 features that drive model performance]
- **Model Strengths:** [What the model does well]
- **Model Limitations:** [Known limitations and failure cases]
- **Business Impact:** [Practical implications of the model performance]

## Documentation

1. **[Literature Review](0_LiteratureReview/README.md)**
2. **[Dataset Characteristics](1_DatasetCharacteristics/exploratory_data_analysis.ipynb)**
3. **[Baseline Model](2_BaselineModel/baseline_model.ipynb)**
4. **[Model Definition and Evaluation](3_Model/model_definition_evaluation)**
5. **[Presentation](4_Presentation/README.md)**

## Cover Image

(ci.png)
