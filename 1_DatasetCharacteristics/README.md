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

- **Feature 1 (The Intervention):**
  * treat: A binary indicator representing the treatment assignment. A value of 1 means the individual participated in the National Supported Work training program, and 0 means they were part of the observational control group.
    
- **Feature 2 (Demographic Features):**
  * age: A continuous numerical feature representing the individual's age in years. The sample skews quite young, primarily heavily concentrated between the late teens and late twenties.
  * educ: A continuous numerical feature for the number of years of schooling the individual completed. This is roughly bimodal, with a massive spike exactly at 12 years (high school completion) and very few college graduates.
  * race: A categorical feature denoting the individual's race or ethnicity (black, hispan, or white).
  * married: A binary indicator for marital status (1 if married, 0 if unmarried). The majority of the treated group is unmarried.
  * nodegree: A binary indicator for educational attainment. A value of 1 means the individual dropped out of high school (lacks a degree), and 0 means they have at least a high school diploma.
- **Feature 3 (Historical Earnings (Pre-Treatment)):**
  * re74 & re75: Continuous numerical features representing the individual's real annual earnings in 1974 and 1975, prior to the job training program. Just like the target variable, these are heavily zero-inflated and right-skewed, reflecting the economically disadvantaged baseline of the participants.

 <img width="988" height="913" alt="download (1)" src="https://github.com/user-attachments/assets/6a89bfb1-29ca-4010-bd33-20ac94d14efd" />

<img width="990" height="790" alt="download (2)" src="https://github.com/user-attachments/assets/d0030ee5-8e16-4793-b2cd-4665c1e18e6d" />
<img width="541" height="392" alt="download (3)" src="https://github.com/user-attachments/assets/1b09a4a4-10d3-4e80-a9f3-7ad186071f33" />
<img width="936" height="790" alt="download" src="https://github.com/user-attachments/assets/eb6d97fa-3b5b-4e84-b75e-dd40084e9b29" />


## Exploratory Data Analysis

The exploratory data analysis is conducted in the [exploratory_data_analysis.ipynb](exploratory_data_analysis.ipynb) notebook, which includes:

- Data loading and initial inspection
- Statistical summaries and distributions
- Missing value analysis
- Feature correlation analysis
- Data visualization and insights
- Data quality assessment
