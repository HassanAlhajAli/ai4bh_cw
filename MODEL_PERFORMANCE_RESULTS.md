# Stroke Prediction - Model Performance Results

## 📊 Complete Model Comparison

### Performance Metrics Summary

| Model | Specificity | MCC | Brier Score | ROC-AUC | PR-AUC |
|-------|-------------|-----|-------------|---------|--------|
| **Logistic Regression** | 0.7088 | **0.2452** | 0.1722 | **0.8491** | **0.2748** |
| **SVM** | 0.8498 | 0.1687 | 0.0996 | 0.7661 | 0.1278 |
| **Random Forest** | 0.9794 | 0.1842 | 0.0545 | 0.7706 | 0.1629 |
| **XGBoost** | 0.9691 | 0.1043 | 0.0571 | 0.7635 | 0.1619 |
| **LightGBM** | 0.9774 | 0.2197 | **0.0489** | 0.7934 | 0.2197 |

---

## 🏆 Best Model Analysis

### Best Model by MCC (Matthews Correlation Coefficient)
**Logistic Regression** with MCC = **0.2452**

- **MCC**: 0.2452 (Best overall balance)
- **ROC-AUC**: 0.8491 (Highest)
- **PR-AUC**: 0.2748 (Highest)
- **Specificity**: 0.7088
- **Brier Score**: 0.1722

### Top 2 Models by MCC
1. **Logistic Regression** (MCC: 0.2452)
2. **LightGBM** (MCC: 0.2197)

### Best Model by Brier Score (Calibration)
**LightGBM** with Brier Score = **0.0489** (Best probability calibration)

---

## 📈 Detailed Model Performance

### 1. Logistic Regression (Baseline)
- **Specificity**: 0.7088 (70.88% - correctly identifies healthy patients)
- **MCC**: 0.2452 ⭐ (Best - balanced metric)
- **Brier Score**: 0.1722
- **ROC-AUC**: 0.8491 ⭐ (Highest)
- **PR-AUC**: 0.2748 ⭐ (Highest)

**Interpretation**: Best overall model with highest MCC, ROC-AUC, and PR-AUC. Good balance between sensitivity and specificity.

---

### 2. Support Vector Machine (SVM)
- **Specificity**: 0.8498 (84.98% - highest specificity)
- **MCC**: 0.1687
- **Brier Score**: 0.0996
- **ROC-AUC**: 0.7661
- **PR-AUC**: 0.1278

**Interpretation**: Highest specificity (best at avoiding false positives), but lower overall performance.

---

### 3. Random Forest
- **Specificity**: 0.9794 (97.94% - very high)
- **MCC**: 0.1842
- **Brier Score**: 0.0545
- **ROC-AUC**: 0.7706
- **PR-AUC**: 0.1629

**Interpretation**: Very high specificity, good at avoiding false alarms, but lower sensitivity.

---

### 4. XGBoost
- **Specificity**: 0.9691 (96.91%)
- **MCC**: 0.1043 (Lowest)
- **Brier Score**: 0.0571
- **ROC-AUC**: 0.7635
- **PR-AUC**: 0.1619

**Interpretation**: Good specificity but lowest MCC, indicating less balanced performance.

---

### 5. LightGBM
- **Specificity**: 0.9774 (97.74%)
- **MCC**: 0.2197 (Second best)
- **Brier Score**: 0.0489 ⭐ (Best calibration)
- **ROC-AUC**: 0.7934
- **PR-AUC**: 0.2197

**Interpretation**: Second-best overall (MCC), best probability calibration (Brier Score), good balance.

---

## 🔬 Statistical Test Results

### Chi-Square Test: Gender vs Stroke
- **Chi-Square statistic**: 0.4726
- **P-value**: 0.7895
- **Interpretation**: ❌ **NO statistically significant relationship** between gender and stroke (p > 0.05)

### T-Test: Age Difference
- **Mean age (Stroke)**: 67.73 years
- **Mean age (Healthy)**: 41.97 years
- **Difference**: 25.76 years
- **P-value**: 0.0000
- **Interpretation**: ✅ **Statistically significant difference** in age between stroke and non-stroke patients (p < 0.05)
- **Finding**: Stroke patients are significantly older (by ~26 years on average) than healthy patients

---

## 📊 Feature Importance (Top 15 - LightGBM)

Based on the best tree-based model (LightGBM):

| Rank | Feature | Importance |
|------|---------|------------|
| 1 | **age** | 636 |
| 2 | **avg_glucose_level** | 525 |
| 3 | **bmi** | 458 |
| 4 | Residence_type_Urban | 173 |
| 5 | gender_Male | 142 |
| 6 | smoking_status_never smoked | 131 |
| 7 | work_type_Private | 125 |
| 8 | BMI_Category_Overweight | 117 |
| 9 | smoking_status_formerly smoked | 115 |
| 10 | work_type_Self-employed | 92 |
| 11 | ever_married_Yes | 78 |
| 12 | BMI_Category_Obese | 74 |
| 13 | hypertension | 64 |
| 14 | smoking_status_smokes | 64 |
| 15 | Age_Group_Young | 61 |

**Key Findings**:
- **Age** is the most important predictor (636)
- **Average glucose level** is second (525)
- **BMI** is third (458)
- These three features dominate the model's predictions

---

## 📈 Correlation Analysis (Top Correlations with Stroke)

Top features correlated with stroke:
1. Age_Group_Senior: 0.247136
2. age: 0.245257
3. Risk_Factor_Count: 0.174616
4. heart_disease: 0.134914
5. avg_glucose_level: 0.131139
6. hypertension: 0.127904
7. ever_married_Yes: 0.108340

---

## ⏱️ Training Efficiency

| Model | Training Time |
|-------|---------------|
| **Logistic Regression** | 0.09 seconds (Fastest) |
| **LightGBM** | 0.44 seconds |
| **XGBoost** | 0.49 seconds |
| **Random Forest** | 0.70 seconds |
| **SVM** | 13.94 seconds (Slowest) |

**Note**: SVM is significantly slower due to kernel computation, while tree-based models are very efficient.

---

## 🎯 Clinical Interpretation

### For Stroke Detection (High Sensitivity Priority):
- **Logistic Regression** is recommended (best MCC and ROC-AUC)
- Good balance between detecting strokes and avoiding false alarms

### For Avoiding False Alarms (High Specificity Priority):
- **Random Forest** or **LightGBM** (both >97% specificity)
- Better at correctly identifying healthy patients

### For Probability Reliability:
- **LightGBM** has the best calibration (lowest Brier Score: 0.0489)
- Most reliable probability estimates for clinical decision-making

---

## 📝 Key Takeaways

1. **Best Overall Model**: Logistic Regression (MCC: 0.2452, ROC-AUC: 0.8491)
2. **Best Calibration**: LightGBM (Brier Score: 0.0489)
3. **Highest Specificity**: Random Forest (97.94%)
4. **Top Predictors**: Age, Average Glucose Level, BMI
5. **Age is Significant**: Statistically significant difference in age between stroke/non-stroke patients
6. **Gender Not Significant**: No statistically significant relationship between gender and stroke

---

**Note**: These results are from a single train-test split. For production use, consider cross-validation for more robust estimates.

