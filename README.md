# Predicting 5-Year Survival Among Colorectal Cancer Patients

## Overview

This project focuses on predicting the 5-year survival outcome of colorectal cancer patients using machine learning models trained on comprehensive data from the Surveillance, Epidemiology, and End Results (SEER) Program. Colorectal cancer is a leading cause of cancer-related deaths, and accurate long-term survival prediction is crucial for personalized patient care, effective resource allocation, and public health initiatives. This project aims to provide clinicians with predictive tools to assess long-term survival at diagnosis, thereby supporting informed decision-making.

## Project Goal

The primary objective of this project is to predict the 5-year survival outcome of patients diagnosed with colorectal cancer using historical clinical and demographic data from the SEER program.

## Specific Objectives

- Build predictive models to classify whether a patient will survive five years post-diagnosis.
- Clean and preprocess the SEER dataset to address missing values, data leakage, and multicollinearity.
- Identify the most influential features affecting long-term survival, such as tumor characteristics and patient demographics.
- Evaluate model performance using appropriate metrics including accuracy, precision, recall, F1 score, and ROC AUC.
- Translate predictive results into practical insights that can support clinical decision-making and public health strategies.

## Data Source

The dataset used in this project is obtained from the Surveillance, Epidemiology, and End Results (SEER) Program of the National Cancer Institute (NCI).

- Total Records: Over 800,000 cases
- Focus: Colorectal cancer patients
- Timeframe: Diagnoses from 1975 to 2020
- Features: Demographics, tumor details, treatment history, and survival outcomes
- Target Variable: A binary indicator for 5-year survival
    - 1 = Survived at least 60 months
    - 0 = Died within 60 months

## Methodology

1. Data Acquisition  
   Initial retrieval and exploration of colorectal cancer records from SEER.

2. Feature Engineering  
   Selection of relevant features using statistical tests and domain knowledge. Reduction of multicollinearity using Variance Inflation Factor (VIF). Categorical features encoded using One-Hot Encoding.

3. Data Preprocessing  
   - Removed columns with 100 percent missing values.
   - Imputed columns with partial missingness (median/mode or indicators based on threshold).
   - Dropped variables with excessive missing data or those that introduced data leakage.
   - Finalized a reduced feature set of approximately 40 columns.

4. Model Development  
   Multiple machine learning models were trained and evaluated, including:
   - Logistic Regression
   - Random Forest
   - LightGBM
   - CatBoost

## Key Features Identified

Important predictors of 5-year survival included:

- HST_STGA: Cancer stage at diagnosis
- DATE_yr: Year of diagnosis
- AGE_REC: Age of patient
- CS_SSF1: Tumor-specific biological factors
- NUMPRIMS: Number of primary tumors
- NO_SURG: Surgery status
- EOD10_PN: Lymph node involvement
- MAR_STAT: Marital status
- ICDOT10V: Tumor site

## Model Evaluation

| Metric           | Logistic Regression | Random Forest | LightGBM | CatBoost |
|------------------|----------------------|----------------|-----------|-----------|
| Accuracy         | 0.6865               | 0.7764         | 0.8024    | 0.8032    |
| Precision        | 0.6287               | 0.6962         | 0.7223    | 0.7228    |
| Recall           | 0.4387               | 0.7360         | 0.7848    | 0.7866    |
| F1 Score         | 0.5168               | 0.7156         | 0.7523    | 0.7534    |
| ROC AUC Score    | 0.7269               | 0.8611         | 0.8904    | 0.8910    |

## Conclusion

The CatBoost model achieved the best performance across all metrics, indicating strong predictive capability for classifying colorectal cancer patients by their 5-year survival likelihood. LightGBM also performed competitively and could be considered for applications where faster training is desired.

Logistic Regression was the least effective model, highlighting the need for more complex techniques in this context. Random Forest served as a robust baseline model with solid performance but was slightly outperformed by boosting models.

## Recommendations

1. Integration of this predictive model into SEER dashboards can assist clinicians and researchers in assessing individual patient outcomes and optimizing treatment strategies.

2. Healthcare providers and policymakers can use the model’s output to proactively monitor and allocate resources for patients with lower predicted survival probabilities.

## Project Team

- Ayush Shrivastava  
- Ashutosh Masulkar  
- Rahul Swami  
- Rishikesh Mankar  
- Shantanu Dahiphale

Mentor: Professor Hamed Zolbanin  
University of Dayton – MBAN 710 Capstone Project  
May 2025

## Contact

Shantanu Dahiphale  
Email: cdahiphale@gmail.com  
LinkedIn: https://www.linkedin.com/in/shantanu-dahiphale  
GitHub: https://github.com/wckd111/ColorectalCancerSurvivalPrediction-Shantanu
