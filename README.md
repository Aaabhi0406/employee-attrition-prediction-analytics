
# Employee Attrition Prediction & Analytics

An end-to-end **Data Science, Machine Learning, and Business Intelligence project** designed to analyze employee attrition, identify major attrition drivers, predict employees at risk of leaving, and present actionable HR insights through an interactive Power BI dashboard.

The project combines **Python, exploratory data analysis, machine learning, predictive analytics, and Power BI** to demonstrate a complete data science workflow from raw HR data to business decision support.

---

## Project Overview

Employee attrition is a major challenge for organizations because employee turnover can increase recruitment costs, reduce productivity, and result in the loss of experienced talent.

The objective of this project is to answer three major business questions:

1. **What patterns are associated with employee attrition?**
2. **Which employees have a higher predicted risk of leaving?**
3. **What actions can HR teams take to improve employee retention?**

To address these questions, the project follows an end-to-end analytics pipeline:

**Raw HR Data → Data Cleaning → Exploratory Data Analysis → Feature Preparation → Machine Learning → Attrition Probability → Risk Segmentation → Power BI Dashboard → Business Recommendations**

---

## Business Objectives

The project aims to:

- Analyze overall employee attrition patterns.
- Identify departments and job roles with higher attrition.
- Study the relationship between attrition and factors such as:
  - Monthly income
  - Employee tenure
  - Overtime
  - Job satisfaction
  - Work-life balance
- Build a machine learning model to estimate employee attrition risk.
- Generate employee-level attrition probabilities.
- Categorize employees into risk groups.
- Develop an interactive Power BI dashboard for HR decision-making.
- Translate analytical findings into actionable retention recommendations.

---

## Dataset

The project uses the **IBM HR Analytics Employee Attrition dataset**.

The dataset contains employee-level information covering demographic, compensation, job, satisfaction, and employment-related characteristics.

Examples of features include:

- Age
- Department
- Job Role
- Monthly Income
- OverTime
- Job Satisfaction
- Work-Life Balance
- Years At Company
- Total Working Years
- Job Level
- Environment Satisfaction
- Relationship Satisfaction
- Training Times Last Year
- Business Travel
- Marital Status
- Stock Option Level

### Target Variable

`Attrition`

- `Yes` → Employee left the organization
- `No` → Employee remained with the organization

This makes the machine learning task a **binary classification problem**.

---

# Project Workflow

## 1. Business Understanding

The first stage focused on defining the HR problem and identifying the analytical questions that the project should answer.

Key questions included:

- What is the overall employee attrition rate?
- Which departments experience the most attrition?
- Does overtime relate to higher attrition?
- Does employee income relate to attrition?
- Are employees in their early years at the organization more likely to leave?
- How are job satisfaction and work-life balance associated with attrition?
- Can machine learning identify employees with elevated attrition risk?

---

## 2. Data Loading and Inspection

The dataset was loaded and inspected using Python.

Initial analysis included:

- Dataset dimensions
- Data types
- Missing-value inspection
- Duplicate inspection
- Target-variable distribution
- Numerical and categorical feature identification
- Basic descriptive statistics

This stage helped establish the quality and structure of the dataset before modeling.

---

## 3. Data Preprocessing

The preprocessing pipeline prepared the HR data for machine learning.

Major preprocessing activities included:

- Removing irrelevant or non-informative columns where appropriate
- Separating features and target variable
- Encoding categorical variables
- Preparing numerical features
- Creating training and testing datasets
- Ensuring transformations were applied consistently

Special attention was given to the **class imbalance** in the Attrition target because considerably fewer employees belong to the Attrition = Yes class.

This is important because relying only on accuracy can produce misleading results for an imbalanced classification problem.

---

# Machine Learning Pipeline

The machine learning stage was designed to predict whether an employee is likely to leave the organization.

The overall modeling workflow was:

**Data Preparation → Train/Test Split → Preprocessing → Model Training → Model Evaluation → Probability Prediction → Risk Classification**

---

## Model Evaluation

The model was evaluated using classification metrics rather than relying only on accuracy.

Evaluation considerations included:

- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC-AUC

### ROC-AUC

The final model achieved an ROC-AUC score of approximately:

**0.76**

ROC-AUC was particularly useful because the target variable is imbalanced and the project focuses on the model's ability to distinguish between employees with relatively higher and lower attrition risk.

The model should be interpreted as a **decision-support model**, not as a system for making automated employment decisions.

---

# Attrition Probability

Instead of using only binary predictions, the model generates an:

`Attrition_Probability`

for each employee.

This provides more useful information than a simple Yes/No prediction because HR teams can understand the relative level of predicted risk.

For example:

| Employee | Attrition Probability |
|---|---:|
| Employee A | 0.95 |
| Employee B | 0.72 |
| Employee C | 0.21 |

Higher probabilities indicate higher model-estimated attrition risk.

---

# Risk Segmentation

Employees were categorized into risk groups using their predicted attrition probabilities.

The dashboard uses risk categories such as:

- **Low Risk**
- **Medium Risk**
- **High Risk**

This allows HR teams to move from individual probability values to easily interpretable employee risk segments.

---

# Power BI Dashboard

The final analytical output is an interactive **three-page Power BI dashboard**.

The dashboard connects descriptive HR analytics with machine learning predictions.

---

## Page 1 — HR Attrition Analytics Dashboard

The Executive Dashboard provides a high-level overview of workforce attrition.

### Key KPIs

- Total Employees: **1.47K**
- Attrition Rate: **16.12%**
- High Risk Employees: **203**
- Average Years at Company: **7.01**
- Average Monthly Income: **6.50K**

### Visual Analysis

The dashboard analyzes:

- Employee Attrition by Department
- Employee Attrition by Overtime
- Employee Attrition by Job Role
- Attrition Rate by Overtime
- Employee Risk Distribution
- Predicted Employee Attrition

Interactive slicers allow users to filter results by:

- Department
- Gender
- Job Role

---

## Page 2 — ML Attrition Prediction & Risk

The second dashboard page focuses specifically on machine-learning predictions and employee risk.

### ML KPIs

- Predicted Leavers
- High Risk Employees
- Average Attrition Probability
- Model ROC-AUC Score

### Risk Analysis

The page includes:

- Predicted Leavers by Department
- Average Attrition Risk by Job Role
- High-Risk Employee Profiles

The employee-level risk table includes information such as:

- Department
- Job Role
- Age
- OverTime
- Monthly Income
- Years at Company
- Attrition Probability
- Predicted Attrition

Conditional formatting is used to make high attrition probabilities easier to identify.

Interactive filters include:

- Department
- Job Role
- OverTime

A **Reset Filters** button is included to restore the default dashboard state.

---

## Page 3 — Attrition Drivers & Business Insights

The third page focuses on understanding factors associated with employee attrition.

It analyzes:

- Attrition Rate by Monthly Income
- Attrition Rate by Tenure Band
- Attrition Rate by Job Satisfaction
- Attrition Rate by Work-Life Balance

---

# Key Business Insights

## 1. Lower-income employees show higher attrition

Employees earning below 3K showed an attrition rate of approximately:

**28.61%**

This was the highest attrition rate among the analyzed income groups.

---

## 2. Early-tenure employees represent a major retention risk

Employees with less than two years of tenure showed an attrition rate of approximately:

**34.88%**

This suggests that the early stages of the employee lifecycle deserve particular attention in retention strategies.

---

## 3. Job satisfaction is associated with employee retention

Employees with the lowest job satisfaction level showed approximately:

**22.84% attrition**

Employees with the highest job satisfaction level showed approximately:

**11.33% attrition**

This indicates an association between lower job satisfaction and higher employee turnover.

---

## 4. Work-life balance is an important attrition indicator

Employees reporting the lowest work-life balance level showed approximately:

**31.25% attrition**

This was considerably higher than several other work-life balance groups.

---

## 5. Overtime is associated with substantially higher attrition

Employees working overtime showed an attrition rate of approximately:

**30.53%**

compared with approximately:

**10.44%**

for employees who were not working overtime.

This makes overtime an important factor for HR teams to monitor.

---

# HR Recommendations

Based on the analytical findings, organizations could consider the following actions:

### 1. Review compensation for lower-income employees

Evaluate compensation competitiveness, benefits, and career-growth opportunities for employees in lower salary bands.

### 2. Strengthen early employee retention

Introduce stronger:

- Onboarding programs
- Mentorship
- Career planning
- Manager check-ins
- Early employee engagement initiatives

particularly during the first two years of employment.

### 3. Monitor employee satisfaction

Conduct regular employee-satisfaction surveys and targeted manager conversations to identify dissatisfaction earlier.

### 4. Improve work-life balance

Organizations should monitor excessive workload and consider initiatives such as:

- Better workload distribution
- Flexible working arrangements
- Employee well-being programs
- Improved leave management

### 5. Monitor overtime

Employees consistently working overtime may require workload reviews and additional management attention.

### 6. Use ML predictions as an early-warning tool

Machine-learning risk scores can help prioritize employees for proactive retention analysis.

However, these predictions should **not be used as automated employment decisions**.

Human judgment and organizational context remain essential.

---

# Technology Stack

### Programming & Data Analysis

- Python
- Pandas
- NumPy
- Jupyter Notebook

### Machine Learning

- Scikit-learn
- Classification Modeling
- Feature Preprocessing
- Probability Prediction
- ROC-AUC Evaluation

### Data Visualization & Business Intelligence

- Power BI
- DAX
- Interactive Slicers
- KPI Cards
- Conditional Formatting
- Business Insight Visualization

### Development & Version Control

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
│   └── Dashboard screenshots
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
│
├── src/
│
├── .gitignore
├── README.md
├── requirements.txt
└── LICENSE
```

---

# Dashboard Story

The three dashboard pages are intentionally designed to answer different business questions:

### Page 1 — What is happening?

Provides an executive overview of employee attrition.

### Page 2 — Who is at risk?

Uses machine-learning predictions to identify employees and workforce groups with elevated predicted attrition risk.

### Page 3 — What factors are associated with attrition?

Analyzes major workforce characteristics associated with higher employee attrition and translates them into HR recommendations.

Together, these pages create the following analytical flow:

**Descriptive Analytics → Predictive Analytics → Business Recommendations**

---

# How to Run the Project

## 1. Clone the repository

```bash
git clone <repository-url>
```

## 2. Navigate to the project

```bash
cd employee-attrition-prediction-analytics
```

## 3. Install dependencies

```bash
pip install -r requirements.txt
```

## 4. Open Jupyter Notebook

```bash
jupyter notebook
```

Run the notebooks in numerical order.

## 5. Open the Power BI dashboard

Open the `.pbix` file available inside the `dashboard/` directory using Power BI Desktop.

---

# Project Limitations

This project has several important limitations:

- The dataset is relatively small.
- The dataset represents a specific HR analytics scenario and may not generalize to every organization.
- Attrition is an imbalanced classification problem.
- Relationships identified through dashboard analysis represent **associations and not necessarily causal relationships**.
- Employee behavior can be influenced by factors not included in the dataset.
- Model predictions should not be used independently for employment-related decisions.

---

# Future Improvements

Future versions of the project could include:

- Hyperparameter optimization
- Additional classification algorithms
- Advanced class-imbalance techniques
- SHAP-based model explainability
- Feature-importance dashboard
- Model threshold optimization
- Automated ML prediction pipeline
- Deployment through a web application or API
- Integration with live HR databases
- Model monitoring and drift detection

---

# Conclusion

This project demonstrates an end-to-end data science workflow for employee attrition analysis.

It combines:

**Business Understanding → Data Preparation → Machine Learning → Predictive Risk Analysis → Power BI → Business Recommendations**

The project shows how machine learning predictions can be combined with business intelligence tools to transform HR data into interpretable insights that can support proactive employee-retention strategies.

---

## Author

**Abhinav Mohurle**

Data Science | Machine Learning | AI | Analytics