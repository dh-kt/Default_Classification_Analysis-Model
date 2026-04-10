#Default Classification - Credit Card Default Prediction

### Problem Statement
Predict whether a customer will default on their credit card payment using balance and income.

### Dataset
- **Source:** ISLP package (Default dataset)
- **Observations:** 10,000 customers
- **Features:** 2 (balance, income)
- **Target:** `default` (Yes/No) - **Imbalanced** (3.3% Yes, 96.7% No)

### Class Distribution

| Class | Count | Percentage |
| :--- | :--- | :--- |
| No Default | 9,667 | 96.7% |
| Default | 333 | 3.3% |

### Methods Implemented

| Method | Type | Assumptions |
| :--- | :--- | :--- |
| Logistic Regression | Parametric | Linear log-odds |
| LDA | Parametric | Normal data, equal variances |
| QDA | Parametric | Normal data, different variances |
| Naive Bayes | Parametric | Independent predictors |
| KNN | Non-parametric | No assumptions (distance-based) |

### Model Performance (Default Threshold = 0.5)

| Method | Accuracy | AUC |
| :--- | :--- | :--- |
| Logistic Regression | 0.9695 | 0.9425 |
| LDA | 0.9680 | 0.9426 |
| QDA | 0.9695 | 0.9420 |
| Naive Bayes | 0.9665 | 0.9400 |
| KNN (k=5) | 0.9655 | 0.5000 |

### Key Insight: Accuracy is Misleading

A model predicting "No" for everyone achieves 96.7% accuracy. Therefore, we use:

- **Sensitivity (Recall):** Of actual defaults, how many caught?
- **Precision:** Of predicted defaults, how many correct?
- **AUC:** Threshold-independent performance measure

### Threshold Tuning Results

| Threshold | Sensitivity | Precision | Predicted Yes |
| :--- | :--- | :--- | :--- |
| 0.1 | 0.62 | 0.08 | 256 |
| **0.2** | **0.46** | **0.36** | **88** |
| 0.5 | 0.25 | 0.60 | 28 |
| 0.8 | 0.07 | 0.80 | 6 |

### Final Recommendation

| Setting | Value |
| :--- | :--- |
| **Model** | Logistic Regression |
| **Threshold** | 0.2 |
| **Sensitivity** | 46% (catch 46 out of 100 defaulters) |
| **Precision** | 36% (1 in 3 flagged is correct) |

**Business Impact:** Lower threshold catches more defaulters at the cost of more false alarms. For credit default, catching a defaulter is more valuable than avoiding a false alarm.

### Visualizations
- Sensitivity vs Precision trade-off curve
- Defaulters caught at different thresholds

---

## How to Run This Project

### 1. Clone the repository
```bash
git clone https://github.com/YOUR_USERNAME/default_classification_analysis.git
