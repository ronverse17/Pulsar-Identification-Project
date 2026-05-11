# Pulsar Identification Project

Identification and verification of gamma-ray pulsar candidates in the Fermi-LAT 4FGL-DR4 catalog using supervised machine learning techniques.

---

## Project Overview

This project reproduces and extends the methodology presented in the paper:

> *“Identification of Gamma Ray Pulsar Candidates in the Fermi-LAT 4FGL-DR4 Unassociated Sources Using Supervised Machine Learning”*

The work focuses on distinguishing gamma-ray pulsars from Active Galactic Nuclei (AGN) using observational parameters from the Fermi-LAT 4FGL-DR4 catalog. Machine learning models are trained using known AGN and pulsar sources and then applied to classify previously unassociated gamma-ray sources.

The project also includes astrophysical verification of the predicted pulsar candidates through positional cross-matching with the ATNF pulsar catalog.

---

## Objectives

- Preprocess the Fermi-LAT 4FGL-DR4 catalog
- Engineer physically meaningful astrophysical features
- Perform feature selection using Recursive Feature Elimination (RFE)
- Train and evaluate Random Forest and XGBoost classifiers
- Address class imbalance using SMOTE
- Classify unassociated gamma-ray sources
- Verify pulsar candidates using the ATNF pulsar catalog

---

## Dataset

### Fermi-LAT 4FGL-DR4 Catalog

The primary dataset used in this work is the Fourth Fermi-LAT Source Catalog Data Release 4 (4FGL-DR4), containing observational parameters for gamma-ray sources detected by the Fermi Large Area Telescope (LAT).

### Dataset Composition

| Source Class | Number of Sources |
|---|---|
| AGN | 4014 |
| Pulsars | 320 |
| Unassociated Sources | 2423 |

---

## Machine Learning Models

The following supervised learning algorithms were used:

- Random Forest (RF)
- XGBoost (XGB)

To address severe class imbalance between AGN and pulsars, the following balancing method was applied:

- SMOTE (Synthetic Minority Over-sampling Technique)

---

## Feature Engineering

Several astrophysically motivated features were engineered and analyzed, including:

- Spectral curvature parameters
- Variability parameters
- Hardness ratios
- Spectral cutoff energy

Feature selection was performed using Recursive Feature Elimination (RFE).

### Important Features Identified

- `LP_beta`
- `LP_SigCurv`
- `log10_Ecut_PLEC`
- `Variability_Index`

---

## Workflow

```text
4FGL-DR4 Catalog
        ↓
Data Preprocessing
        ↓
Feature Engineering
        ↓
Feature Selection (RFE)
        ↓
Train-Test Split
        ↓
SMOTE Balancing
        ↓
RF / XGBoost Training
        ↓
Model Evaluation
        ↓
Prediction of Unassociated Sources
        ↓
ATNF Catalog Verification
```

---

## Model Evaluation

The models were evaluated using:

- Balanced Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC

The SMOTE-balanced models demonstrated significantly improved pulsar recovery sensitivity.

---

## ATNF Verification

Predicted pulsar candidates were verified using positional cross-matching with the ATNF pulsar catalog.

### Verification Procedure

```text
Predicted Pulsar Candidates
        ↓
Galactic Coordinate Cross-matching
(GLON, GLAT) with ATNF Catalog
        ↓
Angular Separation Analysis
        ↓
Threshold-based Verification
        ↓
Confirmed / Probable Pulsars
```

### Angular Separation Thresholds

- 0.1°
- 0.2°
- 0.3°

---

## Repository Structure

```text
├── notebooks/
│   └── Pulsar_Identification_Project.ipynb
│
├── dataset/
│   └── 4FGL-DR4 dataset files
│
└── README.md
```

---

## Technologies and Libraries

### Programming Language
- Python

### Machine Learning
- scikit-learn
- XGBoost
- imbalanced-learn

### Astronomy and Scientific Computing
- Astropy
- psrqpy
- NumPy
- pandas
- SciPy

### Visualization
- matplotlib
- seaborn

---

## Key Results

- Machine learning models successfully distinguish pulsars from AGN
- Spectral curvature features are the strongest discriminating parameters
- SMOTE balancing significantly improves pulsar recovery sensitivity
- RF-SMOTE achieved the strongest ATNF verification performance
- XGB-SMOTE identified the largest pulsar candidate population
- ATNF cross-matching validates the astrophysical relevance of the predicted pulsar candidates

---

## References

### Original Paper
A. Pathania et al.  
*Identification of Gamma Ray Pulsar Candidates in the Fermi-LAT 4FGL-DR4 Unassociated Sources Using Supervised Machine Learning*  
https://arxiv.org/abs/2510.08654

### Fermi-LAT 4FGL-DR4 Catalog
J. Ballet et al.  
https://arxiv.org/abs/2307.12546

Data Available At: https://fermi.gsfc.nasa.gov/ssc/data/access/lat/14yr_catalog/

### ATNF Pulsar Catalog
R. N. Manchester et al.  
https://www.atnf.csiro.au/research/pulsar/psrcat
