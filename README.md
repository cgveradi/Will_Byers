# 🍷 Wine Quality Prediction

---

## 📌 Project Overview

This project is a **Classification model**. By segmenting wines into five distinct quality categories from "Low" to "Very High" this model provides actionable insights for inventory pricing and quality control.

---
The presentation is available [here](https://docs.google.com/presentation/d/17qJ-Mj6QyY_XEBmsvW4mLutr-CmPJlt_RGi0PgDfKW0/edit?usp=sharing).
---
Trello dashboard is available [here](https://trello.com/b/Ik4K4H4w/ml-project).
---

## 📊 The Data

- **Source:** [UCI Machine Learning Repository - Wine Quality Dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/)
- **Composition:** 6,497 observations of Red and White wine.
- **Features:** 11 physicochemical inputs (pH, Alcohol, Citric Acid, etc.).
- **Target:** Quality category (Engineered from raw scores).

---

## 🛠️ Technical Workflow

### 1. Data Cleaning & Feature Engineering

- **Strategic Binning:** Transformed raw 0-10 scores into 5 business-relevant tiers: `Low`, `Medium Low`, `Medium High`, `High`, and `Very High`.
- **Multicollinearity Management:** Dropped `Residual Sugar` to prevent redundancy with `Density`, ensuring a cleaner feature set.
- **Label Encoding:** Converted categorical tiers into numerical labels for model compatibility.

### 2. The "Leakage" Resolution

- **Critical Discovery:** Identified initial 100% accuracy as **Data Leakage** (the model was "cheating" by seeing the original quality score).
- **The Fix:** Stripped all target-related data, forcing the model to rely solely on **pure physicochemical benchmarks**.

### 3. Advanced Preprocessing

- **Normalization:** Applied `MinMaxScaler` and `StandardScaler` to handle varying feature magnitudes (e.g., Chlorides vs. Total Sulfur Dioxide).
- **Class Balancing (SMOTE):** Addressed the rarity of "Very High" quality wines (imbalanced classes) by synthetically oversampling minority classes using SMOTE (Synthetic Minority Over-sampling Technique). This expanded the training set from **1,279 to 2,970 samples**.

---

## 🔬 Modeling & Performance

We utilized an **Ensemble-first approach** to compare how different architectures handled the chemical complexity of each wine type.

### 🍷 Red Wine Final Results

| Model              | Result (Accuracy)            | Strategic Insight                                           |
| :----------------- | :---------------- | :---------------------------------------------------------- |
| **Random Forest (Tuned)**  | **68.2%** | **Top Performer:** Effectively mapped complex chemical variances. |
| **KNN Classifier** | **58.5%**  | **Stability:** Established a solid, low-variance baseline.        |
| **SMOTE Impact**   | **Balanced** | **Fairness:** Improved prediction on rare premium tiers.    |

### 🥂 White Wine Final Results

| Model              | Result (Accuracy)            | Strategic Insight                                                |
| :----------------- | :---------------- | :--------------------------------------------------------------- |
| **Random Forest (Tuned)**  | **70.4%** | **Top Performer:** High predictability in acidity/sugar balance. |
| **KNN Classifier** | **57.4%**  | **Reliable:** Effective for high-volume automated sorting.            |
| **SMOTE Impact**   | **Robust** | **Depth:** Handled massive sample increases without overfitting.    |

### Validation Strategy: 5-Fold Cross-Validation

To ensure the model works on unseen data, we implemented **Stratified K-Fold Cross-Validation**. 
- **Maintained Class Ratios:** Ensured each test "fold" had a fair representation of all wine qualities. 
- **Confirmed Stability:** Achieved a consistent performance margin (+/-5%), proving the system is robust enough for real-world manufacturing environments.

---

## 🚀 Tech Stack

### Languages & Libraries

- **Python 3.x**
- **Pandas & NumPy:** Data manipulation and matrix operations.
- **Scikit-Learn:** Core ML library for scaling, splitting, and modeling.
- **Imbalanced-Learn (SMOTE):** For handling minority class distribution.
- **Matplotlib & Seaborn:** For feature importance and correlation heatmaps.

### Machine Learning Techniques

- **Ensemble Methods:** Random Forest, AdaBoost, Gradient Boosting, Bagging.
- **Clustering/Proximity:** K-Nearest Neighbors (KNN).
- **Optimization:** Hyperparameter tuning (max_depth, n_estimators), Stratified K-Fold, and SMOTE.
