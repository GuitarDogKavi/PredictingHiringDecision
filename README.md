# Predicting Hiring Decisions in Recruitment Data

## Overview

Recruitment decisions often involve evaluating multiple candidate attributes such as experience, skills, interview performance, and educational background.

This project investigates which factors influence hiring outcomes and develops machine learning models to predict whether a candidate will be hired.

The workflow includes: Exploratory Data Analysis (EDA), statistical hypothesis testing, multivariate analysis, outlier analysis, ML model training, model interpretability using SHAP



## Problem Statement
Organizations often rely on complex recruitment processes to identify the best candidates. However, hiring decisions are influenced by multiple factors.
This project aims to: identify the key drivers of hiring decisions, develop predictive models for recruitment outcomes, provide insights that could improve hiring strategies.



## Dataset Characteristics
Total observations: 1500

Total features: 11

Target variable: Hiring Decision

Each record represents an individual candidate.

Dataset is available at https://www.kaggle.com/datasets/rabieelkharoua/predicting-hiring-decisions-in-recruitment-data



## EDA
Initial exploration revealed several key properties of the dataset.

Hiring Outcome Distribution - 31% hired and 69% not hired. This indicates a class imbalance, which was considered during modeling.



## Multivariate Analysis

Dimensionality reduction was performed using Factor Analysis of Mixed Data (FAMD).

Findings included first two components explained only ~20% of total variance, variables showed weak correlations with each other, no clear separation between hired and non-hired candidates.

This suggested that simple linear models might struggle to classify the data effectively.



### Outlier Analysis

Outliers were detected using Robust Mahalanobis Distance.

Observations beyond the 99th percentile were examined.

Findings: no data errors were detected, outliers represented legitimate candidate profiles, outliers were therefore retained for analysis.

Interestingly, some hired outliers had lower interview scores but higher skill and personality scores, indicating that hiring decisions may prioritize overall capability rather than interview performance alone.



## Class Imbalance Handling

Since the dataset had a strong imbalance in the target variable,
SMOTE was tested. However, balancing the data set increased false positives, meaning the model recommended hiring more unsuitable candidates.Because hiring unsuitable employees can create higher organizational costs, the final models were trained without balancing the dataset.



## Machine Learning Models

Multiple classification algorithms were evaluated: Logistic Regression, K-Nearest Neighbors, Decision Tree, Random Forest, Gradient Boosting, XGBoost, LightGBM, Stacked Ensemble



## Model Interpretability

To understand what drives predictions, model explanations were generated using SHAP (SHapley Additive exPlanations).

The most influential features were: Recruitment Strategy, Skill Score, Interview Score, Personality Score, Experience Years

Demographic features had much smaller SHAP values, confirming earlier EDA findings.
