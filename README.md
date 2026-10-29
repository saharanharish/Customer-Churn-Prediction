```markdown
# Customer Churn Prediction and Analysis

## 📌 About the Project

This project analyzes a telecommunications customer dataset to understand customer behavior, examine churn patterns, and build a machine-learning classifier to predict customer churn.

The project combines Microsoft SQL Server, Python, and Power BI to prepare customer data, visualize business metrics, evaluate a churn prediction model, and support data-driven customer retention decisions.

### Key Highlights
- Performed data exploration, null-value checks, and data cleaning in **Microsoft SQL Server**.
- Created cleaned customer data tables and SQL views for analysis and reporting.
- Developed a **Power BI dashboard** to explore customer demographics, service usage, revenue, and churn patterns.
- Trained and evaluated a **Random Forest classifier** using Python and scikit-learn.
- Analyzed model performance and feature importance to identify patterns relevant to customer retention.

---

## 📚 Table of Contents

1. [About the Project](#-about-the-project)
2. [Tech Stack](#-tech-stack)
3. [Workflow](#-workflow)
4. [Power BI Dashboard](#-power-bi-dashboard)
5. [Machine Learning Model](#-machine-learning-model)
6. [Business Insights](#-business-insights)
7. [Results](#-results)

---

## 🛠 Tech Stack

- **Database:** Microsoft SQL Server, T-SQL
- **Programming Language:** Python
- **Python Libraries:** Pandas, NumPy, Matplotlib, Seaborn, scikit-learn
- **Business Intelligence:** Power BI
- **Machine Learning Algorithm:** Random Forest Classifier

---

## 🔄 Workflow

### 1. Data Exploration and Preparation in SQL Server

- Loaded the source customer dataset into a staging table.
- Explored customer distributions by gender, contract type, customer status, and state.
- Checked columns for missing values using conditional aggregation.
- Handled missing categorical values using `ISNULL()`.
- Created a cleaned production table using `SELECT INTO`.
- Created SQL views to separate existing customers from newly joined customers for downstream analysis.

The following views were created:

- `vw_ChurnData`: Contains customers whose status is `Stayed` or `Churned`.
- `vw_JoinData`: Contains customers whose status is `Joined`.

### 2. Power BI Dashboard

Connected Power BI to the prepared SQL Server data and developed a dashboard to explore customer demographics, service usage, churn distribution, and key business metrics.

The dashboard supports descriptive analysis of customer behavior and churn patterns.

### 3. Machine Learning in Python

- Loaded the `vw_ChurnData` dataset from an Excel workbook into Pandas.
- Removed the customer identifier and churn-related columns that were not used as model features.
- Encoded categorical input features using `LabelEncoder`.
- Mapped customer status to a binary target: `Stayed = 0` and `Churned = 1`.
- Split the dataset into training and testing sets using an 80/20 split.
- Trained a Random Forest classifier with 100 decision trees.
- Evaluated the model using a confusion matrix, classification report, and feature-importance visualization.
- Applied the trained model to the separate `vw_JoinData` dataset.
- Exported records predicted as churners to a CSV file for further analysis.

### 4. Business Insight Generation

Combined customer churn analysis, dashboard findings, and model feature-importance results to examine patterns associated with customer churn and identify potential opportunities for targeted retention efforts.

---

## 📊 Power BI Dashboard

The dashboard includes a customer summary page with visualizations covering churn, customer demographics, service usage, and key performance indicators.

![Power BI Dashboard](https://github.com/saharanharish/Customer-Churn-Prediction/raw/1370cc6202413574de01d548664305cbb9834c9a/powerbidashboard.png)

---

## 🤖 Machine Learning Model

A Random Forest classifier was trained to distinguish customers who stayed from customers who churned.

### Model Configuration

- **Algorithm:** Random Forest Classifier
- **Number of Trees:** 100
- **Training/Test Split:** 80/20
- **Evaluation Methods:** Confusion matrix, precision, recall, F1-score, and accuracy
- **Feature Analysis:** Random Forest feature importance

### Model Evaluation Results

The model was evaluated on a held-out test set containing 1,202 records.

| Metric | Stayed (Class 0) | Churned (Class 1) |
|---|---:|---:|
| Precision | 0.86 | 0.82 |
| Recall | 0.94 | 0.61 |
| F1-score | 0.90 | 0.70 |
| Support | 855 | 347 |

**Overall test accuracy: approximately 84.9%, rounded to 85%.**

The model correctly classified 1,020 of the 1,202 test records.

For the churn class, it correctly identified 213 of the 347 actual churners, corresponding to approximately 61% recall. This indicates that the model identified some customers who churned but missed others.

### Feature Importance

The feature-importance visualization ranked the following variables among the model's most important features:

1. Total Revenue
2. Contract
3. Total Charges
4. Monthly Charge
5. Total Long-Distance Charges

Feature importance indicates the relative contribution of variables to the model's predictions. It does not establish that these variables directly cause customer churn.

---

## 💡 Business Insights

- Explored how churn patterns varied across customer and contract segments.
- Examined the customer and billing variables most influential in the model's predictions.
- Identified potential opportunities for targeted retention analysis based on customer segments and predicted churn.
- Used analytical findings to inform customer-retention recommendations.

These recommendations are intended to support business decision-making. The project did not measure the impact of an implemented retention campaign.

---

## ✅ Results

- Prepared customer data using SQL Server data-quality checks, transformations, and views.
- Developed a Power BI dashboard for analyzing customer demographics, service usage, revenue, and churn patterns.
- Trained and evaluated a Random Forest classifier that achieved approximately **85% test accuracy**.
- Obtained F1-scores of **0.90 for stayed customers** and **0.70 for churned customers**.
- Generated churn predictions for a separate dataset of newly joined customers and exported predicted churn records to CSV.

### 📸 Visual Results

![Model and Dashboard Results](https://github.com/saharanharish/Customer-Churn-Prediction/blob/d37641f816bb9c1c0e9562bdf065b1d71509b313/Results.png)
```
