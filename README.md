# Predicting Completion of Clinical Studies with Explainability

## 🚀 Overview

This project is a submission for **Problem Statement 3** of the **Novartis AI Challenge**. The goal is to **predict the completion status of clinical trials**—whether they are *Completed* or *Not Completed* (*Suspended*, *Withdrawn*, or *Terminated*)—using both structured and unstructured data. The model also provides **explainability** using SHAP and LIME to identify key contributing factors.

---


## 📊 Dataset & Assumptions

- Total Columns: 16 features + 1 target
- 5 key **textual** columns (processed using **Bio-BERT**)
- 10 significant **categorical** features (selected via Chi-Square test)
- 1 **numerical** feature: `Enrollment`

> Special Handling:
- Imbalanced target classes handled with **SMOTE** and downsampling.
- Outliers in numerical data treated using **IQR method**.

---

## 🧠 Methodology

### 1. Data Preprocessing

- **EDA** to understand distributions, handle missing values, detect outliers.
- Feature correlation and class balance assessment.
- **Outlier Treatment** on `Enrollment`.
- Feature Selection using **Chi-Square** and correlation analysis.

### 2. Feature Engineering

- **One-hot/Ordinal encoding** for categorical variables.
- **Normalization** of numerical features.
- **Bio-BERT** embeddings for unstructured text (5 columns).
- Derived but discarded features like `Completion Days` due to metric drop.

### 3. Model Development

- **Random Forest** for structured data  
- **Bio-BERT Transformer** for unstructured data  
- **Ensemble Model** using soft voting of both models

### 4. Evaluation Metrics

- **F1-Score** (primary metric)
- Accuracy, Precision, Recall, AUC-ROC
- **Explainability**: SHAP & LIME

---

## 📈 Results

### 🔹 Random Forest
- **F1-Score**: 0.8584  
- **Precision**: 0.8859  
- **Recall**: 0.9698  
- **AUC-ROC**: 0.9121  

### 🔹 Bio-BERT
- **Validation F1-Score**: 0.7371  
- **AUC-ROC**: 0.6182  

### 🔹 Ensemble Model
- **F1-Score**: 0.8207  
- **Precision**: 0.9137  
- **Recall**: 0.8500  
- **AUC-ROC**: 0.8214  

---

## 💡 Explainability

To enhance interpretability, we used:
- **SHAP** (SHapley Additive exPlanations)
- **LIME** (Local Interpretable Model-agnostic Explanations)

These methods allowed us to pinpoint features—like `Phases`, `Conditions`, and specific outcomes—that influence prediction outcomes the most.

---

## 🛠️ Tech Stack

- Python, Pandas, Sklearn, Matplotlib
- **Bio-BERT**
- Random Forest Classifier
- SHAP, LIME
- SMOTE for class balancing

---

## 📌 Conclusion

This project demonstrates how machine learning and deep learning can be combined to provide not only accurate predictions on clinical trial outcomes but also interpretable insights. It has the potential to **minimize clinical trial failures**, **optimize R&D efforts**, and **enhance medical decision-making**.

