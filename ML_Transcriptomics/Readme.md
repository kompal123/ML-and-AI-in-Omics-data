##  ML Transcriptomics: Cancer Classification Using Platelet RNA Sequencing
````markdown

## Overview

This project applies machine learning techniques to tumour-educated platelet (TEP) RNA sequencing data for cancer detection and classification.

The objective was to develop predictive models capable of distinguishing healthy individuals from cancer patients (binary classification) and identifying specific cancer types (multi-class classification) using high-dimensional transcriptomic data.

---

## Project Objectives

The project aimed to:

- preprocess platelet RNA sequencing transcriptomic data
- develop leakage-safe machine learning pipelines
- compare multiple classification algorithms
- optimise model performance using cross-validation
- evaluate binary and multi-class cancer classification performance
- identify biologically important transcriptomic biomarkers
- compare findings with the benchmark study by Best et al. (2015)

---

## Dataset

The dataset consists of platelet RNA sequencing gene expression profiles derived from tumour-educated platelets.

### Cancer classes included:

- Healthy
- Breast Cancer
- Colorectal Cancer
- Glioblastoma
- Liver Cancer
- NSCLC
- Pancreatic Cancer

Rare cancer classes with insufficient sample size were excluded to improve model stability.

---

## Methodology

### 1. Data Preprocessing

The following preprocessing steps were applied:

- loading transcriptomic gene expression matrix
- transposing the dataset so rows represent samples and columns represent genes
- extracting sample labels from metadata
- mapping samples to cancer categories
- creating binary labels (Healthy vs Cancer)
- filtering out rare cancer classes
- train/test split using stratified sampling
- balancing training data only (undersampling)
- preventing data leakage

---

### 2. Feature Selection

Due to the extremely high dimensionality of transcriptomic data, feature reduction was required.

Feature selection was performed using:

- **ANOVA F-test (SelectKBest)**

Top informative genes were retained for model training.

---

## Models Implemented

### Binary Classification

Binary classification task:

**Healthy vs Any Cancer**

Models:

- Logistic Regression
- Random Forest

---

### Multi-class Classification

Multi-class classification task:

**Healthy vs Specific Cancer Types**

Models:

- Gradient Boosting Classifier
- XGBoost Classifier

---

## Hyperparameter Optimisation

Hyperparameter tuning was performed using:

- **GridSearchCV**
- **5-fold Stratified Cross Validation**

### Logistic Regression
Optimised parameter:

- `C` (regularisation strength)

### Random Forest
Optimised parameters:

- `n_estimators`
- `max_depth`
- `min_samples_split`

### XGBoost
Configured parameters:

- `n_estimators`
- `max_depth`
- `learning_rate`
- `objective = multi:softprob`

---

## Evaluation Metrics

Model performance was assessed using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix
- ROC Curve
- Area Under Curve (AUC)

For multi-class classification:

- One-vs-Rest ROC analysis
- Macro-average AUC

---

## Results

### Binary Classification Performance

| Model | Accuracy | AUC |
|------|----------|------|
| Logistic Regression | 0.88 | 0.92 |
| Random Forest | 0.90 | 0.95 |

**Best binary model:** Random Forest

Binary classification showed strong predictive performance, demonstrating that platelet transcriptomic profiles effectively distinguish healthy controls from cancer patients.

---

### Multi-class Classification Performance

| Model | Accuracy |
|------|----------|
| Gradient Boosting | 0.34 |
| XGBoost | 0.35 |

Multi-class ROC analysis showed varying performance across cancer types.

XGBoost achieved stronger discrimination for:

- Liver Cancer
- Healthy controls
- Pancreatic Cancer

Performance remained weaker for biologically overlapping cancers such as:

- Glioblastoma
- NSCLC

---

## Feature Importance Analysis

Feature importance analysis was conducted to identify predictive biomarkers.

Approaches used:

- Logistic Regression coefficient magnitude
- Random Forest feature importance
- XGBoost feature importance
- Gradient Boosting feature importance

These analyses revealed differences in gene prioritisation across algorithms, highlighting how model structure influences biomarker discovery.

---

## Benchmark Comparison

The results were compared with **Best et al. (2015)**, which used Support Vector Machine (SVM) models for platelet RNA cancer classification.

### Binary Comparison

Best et al. reported:

- AUC = **0.96**

Current study:

- Random Forest AUC = **0.95**

This indicates highly comparable binary cancer detection performance.

---

### Multi-class Comparison

Best et al. reported:

- Accuracy = **0.69**

Current study:

- XGBoost Accuracy = **0.35**
- Gradient Boosting Accuracy = **0.34**

Multi-class performance was substantially lower, likely due to:

- class imbalance
- transcriptomic complexity
- biological similarity between cancers
- limited subtype sample sizes

---

## Key Learning Outcomes

This project demonstrated:

- the importance of leakage-safe preprocessing
- why balancing should only be applied to training data
- how cross-validation improves model robustness
- the impact of feature selection in high-dimensional omics data
- differences between linear and ensemble models
- challenges of multi-class cancer classification
- interpretation of ROC and AUC in biomedical classification

---

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Matplotlib
- Jupyter Notebook

---

## Repository Structure

```bash
ML_Transcriptomics/
│
├── data/
│   └── transcriptomic datasets
│
├── Sourcecode/
│   └── preprocessing, training, evaluation scripts
│
├── Results/
│   └── figures, ROC curves, confusion matrices, feature importance plots
│
└── Readme.md
````

---

## Future Improvements

Potential enhancements include:

* SMOTE instead of undersampling
* nested cross-validation
* hyperparameter tuning for multi-class models
* external dataset validation
* SHAP explainability analysis
* pathway enrichment analysis
* deep learning comparison

---

## Reference

Best, M.G. et al. (2015).
RNA-Seq of tumour-educated platelets enables blood-based pan-cancer, multiclass, and molecular pathway cancer diagnostics.

---

## Author

**Kompal**

Machine Learning for Biomedical Transcriptomics

```

This is tailored specifically to your **transcriptomics cancer classification repository**.
```

