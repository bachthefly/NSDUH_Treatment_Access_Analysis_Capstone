# Access, Attitudes, and Need

### A Behavioral-Model Analysis of Mental Health and Substance Use Treatment Access in the United States

An applied data analytics study examining factors associated with access to **mental health and substance use treatment** among U.S. adults using the **2023 National Survey on Drug Use and Health (NSDUH)**.

The project combines interpretable statistical modeling with machine learning to identify important demographic, socioeconomic, behavioral, and clinical predictors of treatment access.

## Research Question

**What factors are associated with access to mental health and substance use treatment in the United States, and how do these relationships differ across treatment types?**

The analysis is grounded in:

- **Andersen's Behavioral Model of Health Services Use**
- **Ajzen's Theory of Planned Behavior**

These frameworks motivate the examination of demographic characteristics, structural enabling factors, clinical need, and behavioral/attitudinal indicators as potential predictors of treatment access.

## Data

The analysis uses the **2023 National Survey on Drug Use and Health (NSDUH)**, a nationally representative survey conducted by the **Substance Abuse and Mental Health Services Administration (SAMHSA)** -- An agency of the **United States Department of Health and Human Services**.

Two treatment-access outcomes are examined:

- **Mental health treatment** (`MHTRTPY`)
- **Substance use treatment** (`SUTRTPY`)

The analysis focuses on adults aged 18 and older.

> The public-use NSDUH data are not included in full in this repository. See the data documentation for information on obtaining the source dataset.

## Analytical Approach

The project uses a multi-stage modeling pipeline designed to balance **variable selection, interpretability, and predictive performance**.

### 1. Variable Selection

**Group LASSO** is used to select relevant predictors while preserving related variables as groups.

### 2. Statistical Modeling

Selected variables are evaluated using **survey-weighted logistic regression** to estimate associations with treatment access.

Results are reported as **odds ratios (ORs)** with confidence intervals to support interpretation.

### 3. Machine Learning

**Random Forest** models are used to evaluate nonlinear relationships and compare predictive performance against the statistical models.

### Modeling Pipeline

```text
NSDUH Data
    │
    ▼
Data Preparation
    │
    ▼
Group LASSO
    │
    ├──────────────► Variable Selection
    │
    ▼
Survey-Weighted Logistic Regression
    │
    ├──────────────► Interpretable Odds Ratios
    │
    ▼
Random Forest
    │
    └──────────────► Nonlinear Relationships & Prediction

```

## Key Findings
### Mental Health Treatment

Clinical need was among the strongest predictors of mental health treatment access, with past-year major depressive episode emerging as a particularly important predictor.

Other influential factors included:
- Race and ethnicity
- Sex
- Insurance coverage
- Illicit drug use
- Education
- Age
  
### Substance Use Treatment

Important predictor groups included:
- Education
- Age
- Alcohol-related problems
- Illicit drug use
- Marital status

The models suggest that treatment access is shaped by a combination of clinical need, structural resources, and demographic characteristics, rather than by any single factor.

## Results

### Model Performance
| Outcome                 | Model         | Weighted AUC | Weighted Accuracy |
| ----------------------- | ------------- | -----------: | ----------------: |
| Mental health treatment | Random Forest |        ~0.70 |             ~0.78 |
| Substance use treatment | Random Forest |        ~0.76 |             ~0.77 |

The predictive results indicate stronger discrimination for substance use treatment than for mental health treatment, while the statistical models provide additional interpretability into the factors associated with treatment access.

## Visualizations

The repository includes:

- Group LASSO coefficient and trace plots
- Model performance visualizations
- Logistic regression odds-ratio plots
- Descriptive distributions
- Predictor importance analyses

Selected figures are available in [`figures/`](figures/).

## Repository Structure
```text
├── notebooks/
│   ├── 01_treatment_access_modeling.ipynb
│   └── 02_treatment_access_visualization.ipynb
├── data/
│   └── README.md
├── results/
│   ├── MHTRTPY/
│   └── SUTRTPY/
├── figures/
│   ├── MHTRTPY/
│   └── SUTRTPY/
├── paper/
│   └── ...
├── .gitignore
├── requirements.txt
└── README.md
```
## Research Paper

The full written analysis and supporting materials are available in writing/.

## Tools
- Python
- pandas
- NumPy
- scikit-learn
- statsmodels
- matplotlib
- seaborn
- Jupyter Notebook

## Project Context

This project was completed as a senior capstone for DA401: Seminar in Data Analytics at Denison University.

The project was developed independently by Bach Nguyen.

## Citation

If referencing this work, please cite the accompanying research paper.

Author: Bach Nguyen

Denison University · 2026
