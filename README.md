# Customer Churn Prediction

## Overview

This project aims to predict **customer churn** for a subscription-based service. Churn refers to customers who stop using the service over a given period.  
It is formulated as a **binary classification problem** (Churn: Yes/No).

The objective is to identify patterns in customer behavior that can help retain customers.  
Suitable model families for binary classification in this context include:

- **Tree-based models**: Random Forest, Gradient Boosting (XGBoost, LightGBM, CatBoost)
- **Logistic Regression**
- **Support Vector Machines**
- **Neural Networks** (for more complex feature interactions)

---

## Dataset

The dataset contains customer demographic, account, and service usage information.  
Key columns include:

- **tenure** – Number of months the customer has stayed with the company.
- **MonthlyCharges** – Amount billed to the customer each month.
- **TotalCharges** – Total amount billed over the customer’s tenure.
- **Contract** – Type of contract (month-to-month, one year, two years).
- **PaymentMethod** – Payment method chosen by the customer.
- **Churn** – Target variable (`Yes` or `No`).

---

## Data Science Workflow

### 1. Data Mining

- Load dataset and review schema.
- Identify data types, missing values, and unique value counts.
- Understand domain-specific meanings of features (e.g., **tenure** affects churn probability — shorter tenure customers are more likely to leave).

### 2. Data Cleaning

- Handle **missing values**:
  - Replace missing `TotalCharges` with `MonthlyCharges * tenure` (if applicable).
- Remove obvious data entry errors or inconsistencies.
- Standardize categorical values (e.g., "Yes"/"No" responses).

### 3. Data Exploration

- **Univariate analysis**: Distribution of tenure, monthly charges, and churn rates.
- **Bivariate analysis**: Relationship between churn and other features.
- Visualize key patterns:
  - Customers with short tenure churn more.
  - Month-to-month contracts have higher churn rates than longer contracts.

### 4. Data Transformation

- **Encoding categorical variables**:
  - One-hot encode nominal variables (e.g., `PaymentMethod`).
  - Label encode binary variables (e.g., `Churn` → 0/1).
- **Feature scaling**:
  - Standardize numeric features for models sensitive to scale (e.g., logistic regression, SVM).
- **Feature engineering**:
  - Contract length categories converted to numeric features.
  - Calculate **Average Monthly Spend** (`TotalCharges / tenure`).

### 5. Model Training & Evaluation

- Split dataset into **train** and **test** sets.
- Train multiple classification models:
  - Logistic Regression
  - Random Forest
  - Gradient Boosting
- Evaluate using:
  - Accuracy
  - Precision, Recall, F1-score
  - ROC-AUC score
- Compare performance and select the best-performing model.

---

## Results & Insights

- **Tenure** is a strong predictor of churn — customers in their first few months are more likely to leave.
- Month-to-month contracts show higher churn compared to one-year or two-year contracts.
- Automatic payment methods are associated with lower churn.

---

## Next Steps

- Implement hyperparameter tuning (GridSearchCV or RandomizedSearchCV) for the best model.
- Deploy the trained model as an API for real-time churn prediction.
- Integrate with CRM systems for proactive retention campaigns.

---

## Technologies Used

- **Python** (pandas, NumPy, scikit-learn, matplotlib, seaborn)
- **Jupyter Notebook** for experimentation and visualization

---

## How to Run

1. Clone this repository.
2. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
