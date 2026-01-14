# 🍷 Wine Quality Prediction

---

## 📌 Project Overview

This project is a **Classification model**. By segmenting wines into five distinct quality categories from "Low" to "Very High" this model provides actionable insights for inventory pricing and quality control.

---

## 📊 The Data

- **Source:** [UCI Machine Learning Repository - Wine Quality Dataset](https://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/)
- **Composition:** 6,497 observations of Red and White wine.
- **Features:** 11 physicochemical inputs (pH, Alcohol, Citric Acid, etc.).
- **Target:** Quality category (Engineered from raw scores).

---

## 🛠️ Technical Workflow

### 1. Strategic Split

- Split the master dataframe into two distinct data pipelines (`df_red` and `df_white`). This allows the models to learn the unique chemical benchmarks for each color (e.g., higher Volatile Acidity tolerance in Reds vs. Whites).

### 2. Feature & Target Engineering

- **Cardinality Reduction:** Transformed the 0-10 scale into 5 meaningful business bins using `pd.cut`:
  - `Low` (0-4), `Medium Low` (4-5), `Medium High` (5-6), `High` (6-7), `Very High` (7-10).
- **Label Encoding:** Applied `LabelEncoder` to transform categorical quality tiers into numerical vectors.

### 3. Data Preprocessing

- **Normalization:** Applied **MinMaxScaler** separately to each pipeline. This ensures that the feature scales are optimized based on the specific ranges of each wine type.

---

## 🔬 Modeling & Performance

### Algorithm: K-Nearest Neighbors (KNN)

We deployed separate KNN instances for Red and White wines, optimizing the $K$ factor for each to achieve maximum precision.

| Model                     | Accuracy    | Strategy                             |
| :------------------------ | :---------- | :----------------------------------- |
| **White Wine Classifier** | **94.69%**  | Optimized for acidity/sugar balance. |
| **Red Wine Classifier**   | **93.12%%** | Optimized for tannin/pH stability.   |
