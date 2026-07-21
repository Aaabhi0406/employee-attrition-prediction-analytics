# Machine Learning Model Comparison & Selection

## Employee Attrition Prediction

This document explains the machine-learning experimentation, model comparison, evaluation strategy, and final model selection used in the Employee Attrition Prediction & Analytics project.

---

# 1. Machine Learning Problem

The objective of the machine-learning component was to predict whether an employee is likely to leave the organization.

The target variable was:

`Attrition`

with two classes:

- `No` — Employee remains with the organization
- `Yes` — Employee leaves the organization

Therefore, the problem was formulated as a **binary classification problem**.

---

# 2. The Class Imbalance Problem

One of the most important characteristics of the dataset was that employee attrition was imbalanced.

There were considerably more employees belonging to:

`Attrition = No`

than:

`Attrition = Yes`

This creates an important machine-learning challenge.

A model could achieve high overall accuracy simply by predicting the majority class correctly while failing to identify employees who actually leave.

For this reason, **accuracy alone was not considered sufficient for model selection**.

Greater attention was given to:

- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC-AUC

with particular attention to **Recall for the Attrition = Yes class**.

---

# 3. Why Recall Matters

From an HR retention perspective, a False Negative means:

> An employee who actually leaves is predicted as unlikely to leave.

For an early-warning attrition system, missing a large percentage of employees who eventually leave reduces the usefulness of the model.

Therefore, the modeling objective was not simply:

> "Which model gives the highest accuracy?"

Instead, the question became:

> "Which model provides the most useful ability to detect employees belonging to the minority attrition class?"

---

# 4. Models Evaluated

Multiple classification approaches were evaluated:

1. Logistic Regression
2. Balanced Logistic Regression
3. Decision Tree
4. Random Forest

Each model was evaluated using the same overall classification objective.

---

# 5. Model Comparison

| Model | Accuracy | Attrition Precision | Attrition Recall | Attrition F1 |
|---|---:|---:|---:|---:|
| Logistic Regression | 0.88 | 0.87 | 0.28 | 0.42 |
| **Balanced Logistic Regression** | **0.70** | **0.30** | **0.66** | **0.41** |
| Decision Tree | 0.83 | 0.44 | 0.17 | 0.25 |
| Random Forest | 0.84 | 0.44 | 0.09 | 0.14 |

---

# 6. Standard Logistic Regression

Standard Logistic Regression achieved approximately:

- Accuracy: **88%**
- Attrition Precision: **87%**
- Attrition Recall: **28%**
- Attrition F1: **42%**

At first glance, the 88% accuracy appears very strong.

However, the model detected only approximately **28% of actual attrition cases**.

This demonstrates why accuracy can be misleading when working with imbalanced classification datasets.

The model performed strongly on the majority class but missed a large proportion of employees belonging to the minority attrition class.

---

# 7. Balanced Logistic Regression

To address the class imbalance, Logistic Regression was trained using class balancing.

The balanced model produced approximately:

- Accuracy: **70%**
- Attrition Precision: **30%**
- Attrition Recall: **66%**
- Attrition F1: **41%**

The overall accuracy decreased significantly compared with standard Logistic Regression.

However, recall for the Attrition class increased from:

**28% → 66%**

This was a major improvement for the project's business objective.

The balanced model correctly identified **31 out of 47 actual attrition cases** in the evaluated test data.

Although the model generated more false positives, it detected substantially more employees who actually belonged to the attrition class.

---

# 8. Decision Tree

The Decision Tree produced approximately:

- Accuracy: **83%**
- Attrition Precision: **44%**
- Attrition Recall: **17%**
- Attrition F1: **25%**

Confusion Matrix:

| | Predicted No | Predicted Yes |
|---|---:|---:|
| Actual No | 237 | 10 |
| Actual Yes | 39 | 8 |

Only **8 out of 47 actual attrition cases** were correctly identified.

Despite reasonable overall accuracy, the extremely low minority-class recall made the model unsuitable for the project's primary objective.

---

# 9. Random Forest

Random Forest produced approximately:

- Accuracy: **84%**
- Attrition Precision: **44%**
- Attrition Recall: **9%**
- Attrition F1: **14%**

Confusion Matrix:

| | Predicted No | Predicted Yes |
|---|---:|---:|
| Actual No | 242 | 5 |
| Actual Yes | 43 | 4 |

The model correctly detected only:

**4 out of 47 actual attrition cases**

Despite achieving 84% accuracy, its ability to identify employees belonging to the minority attrition class was extremely limited.

Therefore, Random Forest was not selected as the final model.

---

# 10. Final Model Selection

## Balanced Logistic Regression

Balanced Logistic Regression was selected as the final model.

The decision was NOT based on having the highest overall accuracy.

In fact, its approximately 70% accuracy was lower than the other evaluated models.

It was selected because it provided the strongest recall for the Attrition class:

**Recall ≈ 66%**

compared with:

- Standard Logistic Regression — 28%
- Decision Tree — 17%
- Random Forest — 9%

For this project, identifying a larger proportion of potentially at-risk employees was considered more valuable than maximizing overall accuracy.

---

# 11. Accuracy vs Business Objective

This experiment demonstrates an important machine-learning principle:

> The model with the highest accuracy is not automatically the best model.

Standard Logistic Regression achieved approximately 88% accuracy, while Balanced Logistic Regression achieved approximately 70%.

If model selection had been based only on accuracy, standard Logistic Regression would have been selected.

However, its minority-class recall was only approximately 28%.

Balanced Logistic Regression increased that recall to approximately 66%.

Therefore, model selection was aligned with the **business objective rather than a single headline metric**.

---

# 12. ROC-AUC

The final model achieved an ROC-AUC of approximately:

**0.76**

ROC-AUC provides an additional view of the model's ability to distinguish between employees with relatively higher and lower attrition risk across classification thresholds.

---

# 13. Probability-Based Prediction

Instead of using only binary predictions, the final pipeline generated:

`Attrition_Probability`

for individual employees.

These probabilities were subsequently used for:

- Predicted Attrition
- Employee risk segmentation
- High-risk employee identification
- Power BI risk analysis

---

# 14. Risk Segmentation

Predicted probabilities were transformed into interpretable employee risk categories:

- Low Risk
- Medium Risk
- High Risk

This allowed the machine-learning output to be integrated into the Power BI dashboard in a format that is easier for business users to interpret.

---

# 15. Integration with Power BI

The prediction pipeline generated the final dashboard dataset containing:

- Original employee attributes
- Attrition Probability
- Predicted Attrition
- Risk Category

This dataset was then imported into Power BI.

The ML Risk Analysis dashboard provides:

- Predicted Leavers
- High-Risk Employees
- Average Attrition Probability
- Model ROC-AUC
- Predicted Leavers by Department
- Average Attrition Risk by Job Role
- High-Risk Employee Profiles

---

# 16. Key Learning

The most important lesson from the modeling process was that **model evaluation must reflect the actual problem being solved**.

For an imbalanced employee attrition problem:

**High accuracy ≠ Strong attrition detection**

Balanced Logistic Regression sacrificed some overall accuracy but substantially improved the ability to detect the minority attrition class.

This trade-off made it more appropriate for the objective of building an employee attrition early-warning analysis system.

---

# 17. Responsible Interpretation

The model should be treated as a **decision-support tool rather than an automated employment decision system**.

Predicted attrition probabilities indicate statistical risk based on patterns in the available dataset.

They do not prove that an individual employee will leave.

Predictions should therefore be combined with:

- Human judgment
- Employee feedback
- Organizational context
- Responsible HR practices

The model should not independently determine employment-related actions.