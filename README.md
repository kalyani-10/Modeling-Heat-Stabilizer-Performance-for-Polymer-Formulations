# Modeling Heat Stabilizer Performance for Polymer Formulations

**Arkema (Cheminformatics Project)**

## Overview

This project focuses on predicting the antioxidant performance of heat stabilizers used in polymer formulations. The objective was to model kinetic rate constants associated with radical scavenging activity using machine learning and cheminformatics techniques.

A dataset of **343 unique antioxidant molecules** collected from literature sources was used to develop predictive models capable of estimating stabilizer reactivity and identifying key molecular properties influencing performance.

---

## Objectives

* Predict antioxidant kinetic rate constants for radical scavenging reactions.
* Develop robust machine learning models for molecular property prediction.
* Explore structure–activity relationships affecting antioxidant performance.
* Provide interpretable insights into molecular features driving reactivity.

---

## Dataset

### Source

* Literature-derived dataset of antioxidant compounds.
* 343 unique chemical structures.

### Molecular Representation

Molecules were represented using multiple complementary feature sets:

#### 1. ChemBERTa Embeddings

* SMILES-based molecular representations.
* Context-aware transformer embeddings generated using ChemBERTa.

#### 2. RDKit Descriptors

Physicochemical properties including:

* Molecular Weight
* LogP
* Topological Polar Surface Area (TPSA)
* Hydrogen Bond Donors/Acceptors
* Rotatable Bonds
* Ring Counts

#### 3. Fragment-Based Features

* Functional group counts
* Aromatic fragment counts
* Structural motif indicators

#### 4. Quantum Mechanical Features

DFT-level properties estimated using machine learning surrogate models:

* HOMO Energy
* LUMO Energy
* HOMO-LUMO Band Gap

---

## Methodology

### Pipeline 1: Supervised Regression Modeling

#### Models Evaluated

* Linear Regression
* Ridge Regression
* Lasso Regression
* Random Forest Regressor
* Gradient Boosting Regressor
* XGBoost Regressor
* Support Vector Regression (SVR)

#### Validation Strategy

* 5-Fold Cross Validation
* Hyperparameter Optimization

#### Best Performing Model

**Support Vector Regression (SVR) with RBF Kernel**

---

### Pipeline 2: Cluster-Based KNN Modeling

A complementary modeling strategy was developed to capture local chemical similarity.

#### Clustering Features

* Molecular Weight
* Aromaticity

#### Workflow

1. Partition molecules into chemically similar clusters.
2. Train cluster-specific K-Nearest Neighbors models.
3. Generate localized predictions based on molecular neighborhood similarity.

---

### Ensemble Framework

Predictions from:

* SVR Model
* Cluster-Based KNN Model

were combined to improve robustness and predictive performance for commercial antioxidant candidates.

---

## Model Explainability

### SHAP Analysis

SHAP (SHapley Additive exPlanations) was applied to interpret model predictions and identify key drivers of antioxidant activity.

#### Insights Obtained

* Electronic properties strongly influenced reactivity.
* HOMO energy contributed significantly to radical scavenging performance.
* Aromaticity and structural fragments affected stabilization mechanisms.
* Molecular size and physicochemical properties impacted kinetic behavior.

---

## Technology Stack

### Machine Learning

* Python
* Scikit-Learn
* XGBoost

### Cheminformatics

* RDKit
* ChemBERTa

### Explainability

* SHAP

### Data Processing

* Pandas
* NumPy

### Visualization

* Matplotlib
* Seaborn

---

## Project Workflow

```text
Chemical Structures (SMILES)
           │
           ▼
Feature Engineering
 ├── ChemBERTa Embeddings
 ├── RDKit Descriptors
 ├── Fragment Counts
 └── Quantum Features
           │
           ▼
Model Development
 ├── SVR Pipeline
 └── Cluster-Based KNN Pipeline
           │
           ▼
Ensemble Prediction
           │
           ▼
SHAP Explainability
           │
           ▼
Structure–Activity Insights
```

## Key Outcomes

* Developed dual machine learning pipelines for antioxidant reactivity prediction.
* Identified SVR with RBF kernel as the strongest global predictive model.
* Improved prediction robustness through ensemble learning.
* Extracted interpretable structure–activity relationships using SHAP.
* Enabled rapid screening of commercial heat stabilizers for polymer applications.
