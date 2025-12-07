# Stroke Prediction: Machine Learning Analysis

A comprehensive machine learning pipeline for predicting patient stroke risk using healthcare data.

## Project Overview

This project implements a robust machine learning pipeline to predict stroke risk, addressing the challenge of severe class imbalance (95% Healthy vs 5% Stroke). The analysis demonstrates deep clinical understanding, model interpretability, and rigorous evaluation.

## Features

- **Advanced Preprocessing**: KNNImputer for missing values, Winsorization for outliers
- **5 ML Models**: Logistic Regression, SVM, Random Forest, XGBoost, LightGBM
- **Comprehensive Evaluation**: ROC-AUC, Precision-Recall curves, MCC, Brier Score
- **Explainability**: Feature importance and SHAP analysis
- **Statistical Analysis**: Hypothesis testing (Chi-Square, T-Test)

## Dataset

- **File**: `healthcare-dataset-stroke-data.csv`
- **Target**: `stroke` (0 = Healthy, 1 = Stroke)
- **Challenge**: Severe class imbalance

## Results

All visualizations are automatically saved as high-resolution PNG files (300 DPI):
- Target distribution
- Correlation heatmap
- Violin plots
- ROC-AUC curves
- Precision-Recall curves
- Confusion matrices
- Calibration curve
- Feature importance
- SHAP plots