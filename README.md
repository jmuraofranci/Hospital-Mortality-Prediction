# Hospital-Mortality-Prediction
Analyzing EHR data to identify early hospitalization predictors of mortality and develop predictive models using clinical features from the first 12 hours of admission.

## Overview
This project analyzes electronic health records (EHR) data to:
1. Identify features from the first 12 hours of hospital admission associated with mortality
2. Examine the relationship between oxygenation drops and mortality
3. Develop predictive models for hospital mortality

The analysis is divided into two main parts:
- **Part 1**: Data wrangling and feature engineering to create an analytic dataset
- **Part 2**: Statistical analysis and predictive modeling

## Data Files
### [View Dataset here.](https://drive.google.com/drive/folders/1F5DHCaBpSpYZawckb1CX8I8mlCNbgE4H?usp=drive_link)

### Original Data Files (for Part 1)
- `Vitals_cohort_sirs.csv`: Vital signs for each patient at each chart time
- `Labs_cohort.csv`: Laboratory results for each patient at each chart time
- `Diagnoses.csv`: ICD9 codes for diagnoses
- `Notes_small_cohort_v2.csv`: Clinical notes for the sample cohort

### Processed Data Files (for Part 2)
- `Patient_feature_matrix.csv`: Analytic dataset with features from first 12 hours
- `Feature_descriptions.csv`: Descriptions of features in patient_feature_matrix
- `Cohort.csv`: Contains timing information for patients

## Part 1: Data Wrangling/Feature Engineering

### Key Steps:
1. Load and merge data from multiple sources
2. Create SIRS and sepsis indicators based on clinical criteria
3. Handle missing data and temporal alignment
4. Create a timeline for each patient with binary SIRS/sepsis labels

### Definitions:
- **SIRS Criteria**: Requires ≥2 of:
  - Temperature >38°C or <36°C
  - Heart Rate >90
  - Respiratory Rate >20 or PaCO2 <32mmHg
  - WBC >12,000/mm3, <4,000/mm3, or >10% bands

- **Sepsis Criteria**: SIRS + infection (via ICD9 codes or note mentions of 'sepsis/septic')

### Implementation Notes:
- Analysis limited to first 1000 patients (smallest subject_ids)
- Multiple approaches considered for handling missing data
- Temporal alignment performed to create consistent patient timelines

## Part 2: Data Analyses

### Inference Task:
Examines the relationship between sudden oxygenation drops (in first 12 hours) and hospital mortality.

**Approach:**
- Logistic regression with appropriate covariates
- Visualization of the relationship
- Consideration of potential confounders

### Prediction Task:
Develops models to predict hospital mortality using first 12-hour data.

**Models Implemented:**
1. Logistic Regression 
2. Neural Network (MLP)

**Evaluation Metrics:**
- AUC-ROC
- Precision-Recall
- F1

### Python Packages Used:
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn
- tensorflow (for neural network)
- statsmodels

## Results

Key outputs include:
- Processed analytic dataset with SIRS/sepsis indicators
- Statistical analysis of oxygenation drop-mortality relationship
- Performance metrics for predictive models
- Visualizations of key relationships and model performance
