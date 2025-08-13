# Predicting 5-Year Survival Among Colorectal Cancer Patients

## Overview

This project focuses on predicting the 5-year survival outcome for colorectal cancer patients using machine learning models trained on comprehensive data from the Surveillance, Epidemiology, and End Results (SEER) Program. Colorectal cancer is a leading cause of cancer-related deaths, and accurate long-term survival prediction is crucial for personalized patient care, effective resource allocation, and public health initiatives. This project aims to provide clinicians with predictive tools to assess long-term survival at diagnosis, thereby supporting informed decision-making.

## Project Goal

The primary goal of this project is to predict the 5-year survival outcome of patients diagnosed with colorectal cancer using historical clinical and demographic data from the SEER program.

## Specific Objectives

* **Build Predictive Models:** Develop and implement machine learning models to classify whether a patient will survive 5 years post-diagnosis.
* **Data Preprocessing:** Clean and preprocess the SEER colorectal cancer dataset to address real-world challenges such as missing values, data leakage, and multicollinearity.
* **Identify Key Survival Factors:** Determine the most influential features affecting long-term survival, including tumor grade, size, and patient demographics.
* **Evaluate Model Performance:** Assess model effectiveness using appropriate metrics like accuracy, ROC-AUC, precision, and recall.
* **Translate Findings into Insights:** Provide actionable insights to support clinical decisions (e.g., monitoring high-risk patients), public health policy (e.g., resource allocation), and future research.

## Data Source

The dataset used for this project is from the **Surveillance, Epidemiology, and End Results (SEER) Program** of the National Cancer Institute (NCI). 

* **Total Cases:** Over 800,000 records. 
* **Focus:** Colorectal cancer patient records. 
* **Timeframe:** Includes patients diagnosed between 1975–2020. 
* **Features:** Demographics (age, sex, race), tumor details (site, grade, histology), treatment, and outcomes. 
* **Target Variable:** A binary variable (`target`) indicating 5-year survival. 
    * `1` = Survived $\ge$ 60 months (5 years) 
    * `0` = Died within 60 months (5 years) 

## End-to-End Model Development Process

The project followed a structured end-to-end model development process:

1.  **Colorectal Cancer Data:** Initial data acquisition from the SEER program.
2.  **Feature Extraction:**
    * Feature Selection & Multicollinearity reduction (VIF, correlation, statistical tests) 
    * Encoding Categorical Features 
3.  **Machine Learning Model:**
    * Training various classification models: Logistic Regression, LightGBM, Random Forest, and CatBoost. 
    * Model Evaluation using Accuracy and ROC AUC. 

## Data Cleaning & Preprocessing Steps

The following steps were performed to clean and preprocess the raw SEER data:

* **Removed Columns with 100% Missing Values:** Initial dataset had 149 columns; reduced after dropping fully null columns. 
* **Handled Partial Missing Values:** * `< 25% missing`: Imputed using median or mode (e.g., `YR_BRTH`, `IHS`). 
    * `25%–65% missing`: Imputed + added missing indicators (e.g., `CS_SIZE`, `D_AJCC_T`). 
    * `> 65% missing`: Columns were dropped due to excessive nulls or low predictive power. 
* **Dropped Data-Leaking Variables:** Variables containing post-outcome information (e.g., `SRV_TIME_MON`, `DTH_CLASS`) were removed to prevent unfair model performance. 
* **Multicollinearity Reduction:** Used Variance Inflation Factor (VIF) to drop highly collinear features (VIF > 10 threshold). 
* **Feature Selection:** Selected features based on chi-square, ANOVA, correlation with target, and domain understanding. The final feature count was reduced from an initial ~110 features to about 40 informative variables. 
* **Categorical Variable Encoding:** Applied One-Hot Encoding to nominal categorical features. 

## Feature Importance

Key features identified as influential for 5-year survival prediction include:

* `HST_STGA`: Cancer stage – strongest survival predictor 
* `DATE_yr`: Year of diagnosis – reflects treatment era 
* `AGE_REC`: Age at diagnosis – older age typically correlates with lower survival 
* `CS_SSF1`: Site-specific factor – biomarker/tumor information 
* `NUMPRIMS`: Number of primary tumors – indicates disease burden 
* `NO_SURG`: Surgery indicator – critical for treatment status 
* `EOD10_PN`: Lymph node involvement – key staging factor 
* `MAR_STAT`: Marital status – social support can influence outcomes 
* `ICDOT10V`: Tumor site – affects treatment and prognosis 

## Model Performance

Several machine learning models were evaluated for their ability to predict 5-year survival. The key metrics used were Accuracy, Precision, Recall, F1 Score, and AUC Score.

| Metric            | Logistic Regression | Random Forest | LightGBM | CatBoost |
| :---------------- | :------------------ | :------------ | :------- | :------- |
| **Accuracy** | 0.6865              | 0.7764        | 0.8024   | **0.8032** |
| **Precision** | 0.6287              | 0.6962        | 0.7223   | **0.7228** |
| **Recall** | 0.4387              | 0.7360        | 0.7848   | **0.7866** |
| **F1 Score** | 0.5168              | 0.7156        | 0.7523   | **0.7534** |
| **AUC Score** | 0.7269              | 0.8611        | 0.8904   | **0.8910** |

## Model Summary & Recommendations

* **CatBoost** emerged as the best-performing model, achieving the highest accuracy, precision, recall, F1 score, and AUC. This makes it the most balanced and robust classifier for predicting survivor outcomes in this dataset.
* **LightGBM** performed very similarly to CatBoost and is a strong alternative, especially when computational speed and resource efficiency are priorities. 
* **Random Forest** showed good overall performance, outperforming Logistic Regression but slightly lagging behind the boosting models in recall and AUC. 
* **Logistic Regression**, while interpretable, had the lowest performance, particularly in recall, indicating it struggled to capture the complexity of the data. 

**Recommendations:**

1.  **Integrate Survival Prediction Tools into SEER Dashboards:** The developed machine learning model (preferably CatBoost) could be incorporated into SEER dashboards. This would empower clinicians and researchers with an estimated 5-year survival chance for patients based on their medical details, aiding in treatment planning and informed decision-making. 
2.  **Identify High-Risk Patients for Enhanced Care:** The model can effectively flag patients with a lower probability of 5-year survival. This allows for closer follow-up, earlier intervention, or specialized care, particularly beneficial in underserved communities. 

## Project Team

* Ayush Shrivastava
* Ashutosh Masulkar
* Rahul Swami
* Rishikesh Mankar
* Shantanu Dahiphale

**Mentor:** Prof. Hamed Zolbanin 

University of Dayton, MBAN 710 Capstone Project 
May 2025 

