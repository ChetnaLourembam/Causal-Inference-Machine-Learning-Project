# Dataset Characteristics

**[Notebook](exploratory_data_analysis.ipynb)**

## Dataset Information

### Dataset Source
- **Dataset Link:** https://users.nber.org/~rdehejia/data/.nswdata2.html
- **Dataset Owner/Contact:** The original National Supported Work (NSW) Demonstration sample was collected by Robert LaLonde. The replicated and observational subsets are maintained by Rajeev Dehejia and Sadek Wahba, hosted publicly by the National Bureau of Economic Research (NBER). Note: This specific analysis uses the 614-observation subset accessed via the MatchIt repository.
- 
### Dataset Characteristics
- **Number of Observations:** 614 individuals (185 treated participants and 429 non-experimental control individuals)
- **Number of Features:** 9 (including the treatment indicator and target variable)

### Target Variable/Label
- **Label Name:** re78
- **Label Type:** Regression (Continuous)
- **Label Description:** This represents the individual's real annual earnings in 1978, recorded after the job training program concluded. The ultimate task here is causal inference—we are trying to predict what a person's re78 earnings would be with or without the training to estimate the true effect of the intervention.
- **Label Values:** Continuous monetary values, ranging from $0 to upwards of $60,000.
- **Label Distribution:** The distribution is highly right-skewed and severely zero-inflated. A massive portion of the sample had zero earnings in 1978, with a long, thin tail of higher earners.

### Feature Description
The features in this dataset primarily consist of demographic data and historical earnings used as confounding variables (covariates) to control for selection bias between our treatment and control groups.

**Example format:**
- **Feature 1 (The Intervention):**
  * treat: A binary indicator representing the treatment assignment. A value of 1 means the individual participated in the National Supported Work training program, and 0 means they were part of the observational control group.
- **Feature 2 (Demographic Features):**
  * 
- **Feature Group (group_name):** [Description of a group of related features]

## Exploratory Data Analysis

The exploratory data analysis is conducted in the [exploratory_data_analysis.ipynb](exploratory_data_analysis.ipynb) notebook, which includes:

- Data loading and initial inspection
- Statistical summaries and distributions
- Missing value analysis
- Feature correlation analysis
- Data visualization and insights
- Data quality assessment
