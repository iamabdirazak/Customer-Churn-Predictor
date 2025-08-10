# Customer Churn Prediction

## Project Overview

This project addresses the problem of predicting **customer churn** in a subscription-based service.  
**Churn** means customers who stop using the service, modeled as a **binary classification problem** (Churn = Yes/No).  
The goal is to build a reliable predictive model to identify customers likely to churn, enabling targeted retention efforts.

---

## Dataset

The dataset includes customer demographics, account details, and service usage data.  
Key features used:

- `customerID` — Unique customer identifier
- `gender` — Customer gender
- `SeniorCitizen` — Boolean flag for senior customers
- `tenure` — Number of months customer stayed
- `MonthlyCharges` — Monthly billing amount
- `TotalCharges` — Total billing amount over tenure
- `Contract` — Contract type (Month-to-month, One year, Two year)
- `PaymentMethod` — Payment method used
- `Churn` — Target variable (Yes/No)

---

## Workflow Summary

### 1. Data Inspection & Cleaning

- Loaded dataset and inspected structure and data types.
- Identified and imputed missing values in `TotalCharges` by calculating `MonthlyCharges * tenure`.
- Converted inconsistent data types (e.g., `TotalCharges` as numeric).
- Normalized categorical columns for uniformity.

### 2. Exploratory Data Analysis (EDA)

- Analyzed distribution of key variables (`tenure`, `MonthlyCharges`, `Churn`).
- Visualized churn rate by contract type and tenure length.
- Observed higher churn among short-tenure customers and month-to-month contracts.

### 3. Feature Engineering & Preprocessing

- Encoded categorical variables:
  - Label encoded `Churn` (Yes=1, No=0).
  - One-hot encoded nominal variables like `PaymentMethod` and `Contract`.
- Scaled numerical features (`MonthlyCharges`, `TotalCharges`) using StandardScaler.
- Created new feature: Average Monthly Spend = `TotalCharges / tenure`.

### 4. Modeling

- Split data into training and testing sets (80/20).
- Trained multiple classification models:
  - Logistic Regression
  - Random Forest Classifier
  - Gradient Boosting Classifier
- Evaluated models with metrics:
  - Accuracy
  - Precision, Recall, F1-Score
  - ROC-AUC Score

### 5. Model Evaluation

- Random Forest and Gradient Boosting outperformed Logistic Regression in recall and AUC, crucial for catching churners.
- Feature importance analysis highlighted `tenure`, `Contract`, and `MonthlyCharges` as key predictors.

---

## Results

Logistic Regression with updated n_estimators
ROC AUC: 0.84
precision recall f1-score support

           0       0.90      0.73      0.80      1033
           1       0.51      0.78      0.61       372

    accuracy                           0.74      1405

macro avg 0.70 0.75 0.71 1405
weighted avg 0.80 0.74 0.75 1405

Random Forest with updated n_estimators
ROC AUC: 0.814
precision recall f1-score support

           0       0.81      0.90      0.85      1033
           1       0.60      0.44      0.50       372

    accuracy                           0.77      1405

macro avg 0.71 0.67 0.68 1405
weighted avg 0.76 0.77 0.76 1405

![alt text](image.png)

---

## Technologies & Libraries Used

- Python 3.x
- pandas, NumPy for data manipulation
- scikit-learn for modeling and evaluation
- matplotlib, seaborn for visualization
- Jupyter Notebook for interactive exploration

---

## Author

Abdirazak Mubarak

## Date

August 10, 2025
