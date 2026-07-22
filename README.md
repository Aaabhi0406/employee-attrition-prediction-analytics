# Employee Attrition Prediction & Analytics

An end-to-end **Data Science, Machine Learning, and Business Intelligence project** that analyzes employee attrition, identifies key attrition drivers, predicts employees at risk of leaving, and presents actionable HR insights through an interactive Power BI dashboard.

The project demonstrates the complete journey from **raw HR data → machine learning → business intelligence → HR recommendations**.

---

## Project Overview

Employee attrition can create significant recruitment costs, productivity loss, and loss of organizational knowledge.

This project was developed to answer three major questions:

1. **What factors are associated with employee attrition?**
2. **Which employees have a higher predicted probability of leaving?**
3. **How can predictive analytics support proactive HR retention strategies?**

The project combines:

- Python-based data analysis
- Data preprocessing
- Exploratory Data Analysis
- Imbalanced classification
- Machine Learning model comparison
- Probability-based risk prediction
- Employee risk segmentation
- Power BI visualization
- Business insight generation

---

# End-to-End Project Pipeline

```text
Business Understanding
        ↓
Data Collection & Loading
        ↓
Data Quality Analysis
        ↓
Exploratory Data Analysis
        ↓
Data Preprocessing
        ↓
Train/Test Split
        ↓
Machine Learning Model Comparison
        ↓
Class-Imbalance Handling
        ↓
Model Evaluation
        ↓
Final Model Selection
        ↓
Attrition Probability Prediction
        ↓
Employee Risk Segmentation
        ↓
Dashboard Dataset Generation
        ↓
Power BI Dashboard
        ↓
Business Insights & HR Recommendations
```

---

# Dataset

The project uses the **IBM HR Analytics Employee Attrition dataset**.

The dataset contains employee-level demographic, employment, compensation, satisfaction, and workplace information.

Example features include:

- Age
- Department
- Job Role
- Monthly Income
- OverTime
- Years At Company
- Total Working Years
- Job Satisfaction
- Work-Life Balance
- Environment Satisfaction
- Relationship Satisfaction
- Job Level
- Business Travel
- Marital Status
- Stock Option Level

### Target Variable

`Attrition`

- `Yes` → Employee left
- `No` → Employee remained

Therefore, the machine-learning task was formulated as a **binary classification problem**.

---

# The Class-Imbalance Problem

One of the most important challenges in this project was **class imbalance**.

The majority of employees belonged to:

`Attrition = No`

while substantially fewer employees belonged to:

`Attrition = Yes`.

This means that **accuracy alone can be misleading**.

A model can achieve high accuracy by correctly predicting the majority class while failing to detect employees who actually leave.

Therefore, model evaluation considered:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC-AUC

Particular attention was given to **Recall for the Attrition = Yes class**.

---

# Machine Learning Model Comparison

Four classification approaches were evaluated.

| Model | Accuracy | Attrition Precision | Attrition Recall | Attrition F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | 88% | 0.87 | 0.28 | 0.42 |
| **Balanced Logistic Regression** | **70%** | **0.30** | **0.66** | **0.41** |
| Decision Tree | 83% | 0.44 | 0.17 | 0.25 |
| Random Forest | 84% | 0.44 | 0.09 | 0.14 |

---

## Why wasn't the highest-accuracy model selected?

Standard Logistic Regression achieved approximately **88% accuracy**, compared with approximately **70%** for Balanced Logistic Regression.

Looking only at accuracy would therefore suggest that standard Logistic Regression was superior.

However:

**Standard Logistic Regression Attrition Recall: ~28%**

vs.

**Balanced Logistic Regression Attrition Recall: ~66%**

Balanced Logistic Regression identified **31 of the 47 actual attrition cases** in the evaluated test data.

For an employee attrition early-warning use case, detecting a larger proportion of the minority attrition class was considered more important than maximizing overall accuracy.

Therefore, **Balanced Logistic Regression was selected as the final model**.

> **Key ML lesson:** The best model is not necessarily the model with the highest accuracy. Model selection should reflect the business objective and the cost of different prediction errors.

For the complete experiment and selection reasoning, see:

**[Machine Learning Model Comparison](MODEL_COMPARISON.md)**

---

# Final Model

### Balanced Logistic Regression

The final model achieved approximately:

| Metric | Result |
|---|---:|
| Accuracy | ~70% |
| Attrition Recall | ~66% |
| Attrition Precision | ~30% |
| Attrition F1 | ~41% |
| ROC-AUC | ~0.76 |

The model was used as a **risk-ranking and decision-support tool**, rather than as an automated employment decision system.

---

# Attrition Probability

Rather than generating only Yes/No predictions, the final pipeline calculates an:

`Attrition_Probability`

for each employee.

Example:

| Employee | Attrition Probability |
|---|---:|
| Employee A | 0.95 |
| Employee B | 0.72 |
| Employee C | 0.21 |

This makes the output more useful because employees can be ranked according to their model-estimated attrition risk.

---

# Employee Risk Segmentation

Predicted probabilities were converted into interpretable risk categories:

- **Low Risk**
- **Medium Risk**
- **High Risk**

The final prediction dataset therefore contains both:

`Attrition_Probability`

and:

`Risk_Category`

These outputs were subsequently integrated into Power BI.

---

# Power BI Dashboard

The final solution contains a **three-page interactive Power BI dashboard**.

Each page answers a different business question.

---

## Page 1 — HR Attrition Analytics Dashboard

### Question:

**What is happening across the workforce?**

The executive dashboard provides an overview of employee attrition.

### KPIs

- Total Employees: **1.47K**
- Attrition Rate: **16.12%**
- High Risk Employees: **203**
- Average Years at Company: **7.01**
- Average Monthly Income: **6.50K**

### Analysis

- Employee Attrition by Department
- Employee Attrition by Overtime
- Employee Attrition by Job Role
- Attrition Rate by Overtime
- Employee Risk Distribution
- Predicted Employee Attrition

Interactive slicers:

- Department
- Gender
- Job Role

---

## Page 2 — ML Attrition Prediction & Risk

### Question:

**Who is predicted to be at higher risk?**

This page connects the machine-learning model directly with business analysis.

### ML KPIs

- Predicted Leavers
- High-Risk Employees
- Average Attrition Probability
- Model ROC-AUC Score

### Visualizations

- Predicted Leavers by Department
- Average Attrition Risk by Job Role
- High-Risk Employee Profiles

The employee risk table contains:

- Department
- Job Role
- Age
- OverTime
- Monthly Income
- Years At Company
- Attrition Probability
- Predicted Attrition

Conditional formatting highlights employees with high predicted attrition probabilities.

Interactive slicers:

- Department
- Job Role
- OverTime

A **Reset Filters** button restores the default dashboard state.

---

## Page 3 — Attrition Drivers & Business Insights

### Question:

**What workforce factors are associated with attrition?**

This page analyzes:

- Attrition Rate by Monthly Income
- Attrition Rate by Tenure Band
- Attrition Rate by Job Satisfaction
- Attrition Rate by Work-Life Balance

It also translates analytical findings into HR recommendations.

---

# Key Business Insights

### 1. Monthly Income

Employees earning below 3K showed approximately:

**28.61% attrition**

This was the highest attrition rate among the analyzed income bands.

### 2. Employee Tenure

Employees with less than two years of tenure showed approximately:

**34.88% attrition**

This highlights early employee tenure as an important retention period.

### 3. Job Satisfaction

Employees with the lowest job-satisfaction level showed approximately:

**22.84% attrition**

compared with approximately:

**11.33%**

for employees with the highest satisfaction level.

### 4. Work-Life Balance

Employees reporting the lowest work-life balance level showed approximately:

**31.25% attrition**

indicating an association between poor work-life balance and employee turnover.

### 5. Overtime

Employees working overtime showed approximately:

**30.53% attrition**

compared with approximately:

**10.44%**

among employees who were not working overtime.

---

# HR Recommendations

Based on the analysis, organizations could consider:

### Compensation

Review compensation, benefits, and career-growth opportunities for lower-income employees.

### Early-Tenure Retention

Strengthen:

- Onboarding
- Mentorship
- Career planning
- Manager check-ins
- Employee engagement

particularly during the first two years.

### Employee Satisfaction

Conduct regular satisfaction surveys and targeted manager conversations to identify dissatisfaction earlier.

### Work-Life Balance

Monitor workload and consider:

- Flexible working arrangements
- Better workload distribution
- Employee well-being programs
- Improved leave management

### Overtime Monitoring

Identify employees experiencing sustained overtime and investigate workload or staffing issues.

### Predictive Risk Monitoring

Use machine-learning risk scores as an **early-warning signal** to prioritize further HR analysis and employee engagement.

---

# Technology Stack

### Data Science

- Python
- Pandas
- NumPy
- Jupyter Notebook

### Machine Learning

- Scikit-learn
- Logistic Regression
- Balanced Logistic Regression
- Decision Tree
- Random Forest
- Classification Metrics
- ROC-AUC
- Probability Prediction

### Business Intelligence

- Power BI
- DAX
- KPI Cards
- Interactive Slicers
- Conditional Formatting
- Business Insight Visualization

### Development

- Visual Studio Code
- Git
- GitHub

---

# Repository Structure

```text
employee-attrition-prediction-analytics/
│
├── dashboard/
│   └── Power BI dashboard files
│
├── dashboard_data/
│   └── Employee_Attrition_With_Predictions.csv
│
├── dashboard_screenshot/
│   └── Power BI dashboard screenshots
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── external/
│
├── models/
│   └── final_attrition_model.pkl
│
├── notebooks/
│   ├── 01_Business_Understanding.ipynb
│   ├── 02_Data_Loading.ipynb
│   ├── 03_Data_Preprocessing.ipynb
│   └── 04_Dashboard_Dataset.ipynb
│
├── reports/
├── src/
│
├── .gitignore
├── LICENSE
├── MODEL_COMPARISON.md
├── README.md
└── requirements.txt
```

---

# How to Run the Project

### 1. Clone the repository

```bash
git clone <repository-url>
```

### 2. Enter the project directory

```bash
cd employee-attrition-prediction-analytics
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Launch Jupyter

```bash
jupyter notebook
```

Run the notebooks in numerical order.

### 5. Open the dashboard

Open the `.pbix` file inside the `dashboard/` directory using Power BI Desktop.

---

# Responsible ML & Limitations

This project should be interpreted carefully.

- The dataset is relatively small.
- Employee attrition is an imbalanced classification problem.
- Relationships identified through analysis represent **associations, not proof of causation**.
- Model performance on this dataset does not guarantee performance in another organization.
- Employee behavior can depend on factors not represented in the dataset.
- False positives and false negatives remain present in the model.
- Predicted attrition probability does **not** mean an employee will definitely leave.

The ML system is intended as a **decision-support and analytical tool**.

It should not be used independently to make hiring, firing, promotion, compensation, or other employment decisions.

---

# Future Improvements

Potential improvements include:

- Hyperparameter optimization
- Cross-validation-based model comparison
- Classification threshold optimization
- Additional imbalance-handling techniques
- SHAP-based explainability
- Feature importance analysis
- Automated prediction pipeline
- Web/API deployment
- Integration with live HR systems
- Model monitoring
- Data and concept drift detection

---

# Key Learning

The most important technical lesson from this project was understanding that:

> **High accuracy does not necessarily mean a useful model.**

Standard Logistic Regression achieved approximately **88% accuracy** but detected only around **28% of the Attrition class**.

Balanced Logistic Regression reduced overall accuracy to approximately **70%**, but increased Attrition recall to approximately **66%**.

This demonstrated the importance of selecting evaluation metrics based on the **actual business problem rather than a single headline metric**.

---

# Conclusion

This project demonstrates an end-to-end Data Science and Business Intelligence workflow:

**Business Understanding → Data Analysis → Preprocessing → Machine Learning → Model Comparison → Risk Prediction → Power BI → Business Recommendations**

The final solution combines descriptive and predictive analytics to demonstrate how machine learning can be translated into interpretable business insights.

---

# License & Usage

**Copyright © 2026 Abhinav Mohurle. All Rights Reserved.**

This repository is publicly available for **portfolio viewing and evaluation purposes only**.

No permission is granted to copy, reproduce, modify, redistribute, republish, sublicense, sell, or reuse this project's original source code, notebooks, machine-learning workflows, trained model artifacts, dashboard designs, documentation, or other original project materials without prior written permission from the copyright holder.

Third-party datasets, libraries, frameworks, and other external materials remain subject to their respective licenses and terms.

For complete terms, see the **[LICENSE](LICENSE)** file.

---

## Author

**Abhinav Mohurle**

Data Science | Machine Learning | Artificial Intelligence | Business Analytics