# Project: BLEVE-ML – Predicting Blast Pressure with Explainable ML

## 🧠 Overview
This repository contains a complete end-to-end machine learning pipeline to predict **peak blast pressure** from **Boiling Liquid Expanding Vapour Explosions (BLEVEs)** in a complex 3D obstacle-rich environment. Developed for the **COMP6013: Explainable Approaches to Machine Learning** unit at Curtin University, the project integrates predictive modeling and interpretability using real-world physical simulation data.

---

## 🎯 Objective
Predict the **target pressure** at 27 sensor locations based on 3D environment features such as tank dimensions, vapor/liquid properties, and sensor coordinates. The goal is to optimize performance (MAPE, R²) while ensuring interpretability using SHAP.

---

## 🧩 Dataset Features
- **Physical Inputs**: Tank size, temperatures, pressures, obstacle specs, sensor locations
- **Target**: Peak pressure (bar)
- **Train/Test Format**: Provided CSVs with ground truth only in training set

---

## ⚙️ Pipeline
### 1. 🔧 Data Preprocessing
- Null and duplicate checks → No missing values
- Type conversion (One-Hot and Mean Encoding)
- Outlier detection using Z-scores
- Normalization (Log Transform, Winsorization)

### 2. 🛠️ Feature Engineering
- 15+ new features (ratios, volumes, scaled pressures, obstacle impact factor)
- Correlation + LASSO-based feature selection
- Feature count increased to 43

### 3. 🤖 Model Development & Tuning
Six models trained, validated, and tuned:
- **Linear Regression** (with Polynomial Features)
- **Decision Tree + Random Forest**
- **XGBoost**
- **Support Vector Regression (SVR)**
- **Neural Network (TensorFlow + Keras)**
- **CatBoost** – ✅ **Best Performing**

**📈 Top Model Results – CatBoost:**
- **MAPE**: 9.67%
- **R²**: 0.99
- **Kaggle Score (MAPE)**: 25.045 (Top-tier leaderboard rank)

---

## 📊 Results & Evaluation
### ✅ CatBoost (Best Performing Model)
- Delivered outstanding performance with a **MAPE of 9.67%** on training validation data and **R² score of 0.99**, reflecting high prediction accuracy and model fit.
- Outperformed other models in both generalization and interpretability.
- Demonstrated strong feature interaction capabilities, especially for spatial features (sensor coordinates) and vapor dynamics.

### 🔄 Cross-Validation Results
- **K-Fold CV** confirmed consistent model reliability across multiple data splits
- Minimal variance in fold performance validated the robustness of the feature-engineered dataset

### 📉 Comparative Summary
| Model            | MAPE (Train) | R² Score | Notes                          |
|------------------|--------------|----------|---------------------------------|
| CatBoost         | 9.67%        | 0.99     | Best performer                  |
| XGBoost          | ~10.2%       | 0.98     | Strong but less interpretable   |
| SVR              | ~11.5%       | 0.95     | Slower, sensitive to scale      |
| Random Forest    | ~14.3%       | 0.93     | Less effective with sparse data |
| Decision Tree    | ~15.1%       | 0.91     | Overfit tendency                |
| Neural Network   | ~10.8%       | 0.97     | Slightly underfit on minority cases |

These results highlight the strength of ensemble models like CatBoost and XGBoost for non-linear, high-dimensional data with strong interaction effects.

---

## 📁 Repository Contents
| File | Description |
|------|-------------|
| `main.ipynb` | Full model pipeline with SHAP interpretation (Google Colab compatible) |
| `20972008_Zaidi_Syed_report.pdf` | Comprehensive technical report with visualizations, rationale, and reflection |
| `prediction.csv` | Final prediction file submitted to Kaggle leaderboard |
| `COMP6013_Final-Report-Spec-2024.pdf` | Final assignment specification |
| `Project Requirement.pdf` | Initial assignment description and expectations |

---

## 🔍 Tools & Technologies
`Python`, `Pandas`, `NumPy`, `Scikit-learn`, `XGBoost`, `CatBoost`, `TensorFlow`, `SHAP`, `Matplotlib`, `Seaborn`

---

## 👤 Author
**Syed Muhammad Ahmed Zaidi**  
Curtin University | Student ID: 20972008  
Unit: COMP6013 – Explainable Approaches to Machine Learning

---

## 📄 License
This repository is for academic and educational use only. Commercial reproduction requires explicit permission.

---

## 🚀 Status
✅ Complete | 🎯 Achieved top leaderboard results | 🧠 Fully explainable and reproducible
