# Digital-currency-adoption-Intensity_factor_analyzer_
# PhD Appendix Analysis Pipeline  
## Digital Financial Inclusion, digital finance adoption intensity, Regulatory Trust, Innovation Adoption, and Digital Payment Adoption in the South Esthern Nigeria

This repository contains the reproducible statistical and machine-learning analysis workflow used to generate the quantitative appendix outputs for a PhD thesis on **digital financial inclusion and digital payment adoption among Nigerian businesses**.

The workflow was designed to produce publication-ready outputs for **Appendices C–J**, covering reliability and validity testing, descriptive statistics, correlation and multicollinearity diagnostics, probit/fractional probit modelling, marginal effects, moderation analysis, XGBoost prediction, and SHAP-based explainability.

---

## Repository Purpose

The purpose of this repository is to provide a transparent and reproducible analysis pipeline for generating the statistical evidence required to support the thesis appendices.

Specifically, the code generates outputs for:

| Appendix | Analysis component |
|---|---|
| Appendix C | Reliability and validity tests |
| Appendix D | Descriptive statistics and frequency distributions |
| Appendix E | Correlation matrix and VIF diagnostics |
| Appendix F | Probit / fractional probit regression results |
| Appendix G | Average marginal effects |
| Appendix H | Moderation analysis |
| Appendix I | XGBoost model specification and performance |
| Appendix J | SHAP feature importance |

---

## Research Context

The analysis supports a PhD study examining the drivers of digital financial inclusion and high digital adoption among Nigerian businesses.

The empirical framework includes constructs such as:

- **Regulatory Trust**
- **Innovation Adoption Strategy**
- **Digital Literacy**
- **Perceived Usefulness**
- **Perceived Ease of Use**
- **Firm size**
- **Education level**
- **Sector**
- **Gender**
- **Owner age category**

The main dependent variable used in the modelling workflow is:

```text
high_adoption
```

This variable is coded as a bounded outcome with values of 0 and 1.

---

## Dataset

The analysis expects a cleaned primary survey dataset with approximately:

```text
N = 850
```

The dataset should include the construct items, model variables, demographic controls, and categorical variables required for the appendices.

Example variables include:

```text
REG_TRUST_NORM
IAS_INDEX
DIGLIT
PU
PEOU
owner_age_cat
gender
education_level
staff_size_cat
sector
high_adoption
```

Reliability and factor-analysis items include examples such as:

```text
trust_money_safe
trust_dispute_resolution
trust_regulator
trust_digital_over_manual
ias_experience
ias_network_support
ias_advice_reliance
ias_trust_network
diglit_app_use
diglit_security
diglit_records
diglit_teach
use_pos
use_mobile_app
use_digital_credit
use_digital_savings
useful_payment_speed
useful_records
useful_efficiency
useful_market_access
ease_learn
ease_daily_use
ease_train_staff
ease_correct_mistakes
```

---

## What the Code Produces

The workflow exports a single Excel workbook containing all major appendix tables:

```text
Appendices_C_to_J_Statistical_Outputs.xlsx
```

The workbook includes sheets such as:

```text
C_Alpha
C_KMO_Bartlett
C_Factor_Loadings
C_Eigenvalues
C_Variance_Explained
C_CR_AVE
D_Descriptive_Stats
D_Missing_Data
D_Freq_state
D_Freq_cluster
D_Freq_sector
D_Freq_gender
D_Freq_education_level
D_Freq_staff_size_cat
E_Correlation
E_Correlation_Pvalues
E_VIF
F_Frac_Probit
F_Model_Diagnostics
G_AME
H_Moderation
H_Simple_Slopes
I_XGB_Hyperparameters
I_XGB_Performance
I_XGB_Importance
J_SHAP_Importance
```

---

## Main Methods Included

### 1. Reliability Analysis

Cronbach’s alpha is computed for each construct to assess internal consistency.

Constructs include:

- Regulatory Trust
- Innovation Adoption Strategy
- Digital Financial Inclusion
- Digital Literacy
- Perceived Usefulness
- Perceived Ease of Use

---

### 2. Validity and Factor Analysis

The workflow computes:

- Kaiser-Meyer-Olkin measure of sampling adequacy
- Bartlett’s test of sphericity
- rotated factor loadings
- eigenvalues
- variance explained
- composite reliability
- average variance extracted

These outputs support the assessment of construct validity.

---

### 3. Descriptive Statistics

The code generates:

- sample size
- mean
- standard deviation
- minimum
- maximum
- skewness
- kurtosis
- missing-data summary
- frequency tables for categorical variables

---

### 4. Correlation and Multicollinearity Diagnostics

The workflow produces:

- Pearson correlation matrix
- correlation p-value matrix
- variance inflation factor table
- tolerance values
- mean VIF

These outputs are used to assess bivariate relationships and multicollinearity.

---

### 5. Probit / Fractional Probit Regression

The code estimates a probit GLM model suitable for a bounded dependent variable.

The output includes:

- coefficients
- robust standard errors
- z-statistics
- p-values
- 95% confidence intervals
- log pseudo-likelihood
- pseudo R-squared
- AIC
- BIC

---

### 6. Average Marginal Effects

Average marginal effects are computed to support substantive interpretation of the probit-type model.

The output includes:

- marginal effect
- standard error
- z-statistic
- p-value
- 95% confidence interval

---

### 7. Moderation Analysis

The moderation model tests whether **Innovation Adoption Strategy** moderates the relationship between **Regulatory Trust** and high digital adoption.

The interaction term is:

```text
REG_TRUST_NORM × IAS_INDEX
```

The output includes:

- interaction model coefficients
- robust standard errors
- simple slopes
- conditional effects at low, mean, and high levels of IAS

---

### 8. XGBoost Predictive Model

The workflow trains an XGBoost regression model as a supplementary predictive robustness check.

The model outputs:

- hyperparameter table
- training performance
- test performance
- cross-validation R-squared
- feature importance ranking

---

### 9. SHAP Explainability

SHAP values are computed to provide interpretable machine-learning explanations.

The output includes:

- mean absolute SHAP value ranking
- top predictors of high adoption
- SHAP summary plot
- SHAP bar plot

---

## Key Python Packages

The analysis uses the following Python packages:

```python
pandas
numpy
scipy
factor_analyzer
statsmodels
scikit-learn
xgboost
shap
matplotlib
seaborn
openpyxl
```

Install them in Google Colab using:

```python
!pip install factor_analyzer xgboost shap openpyxl statsmodels scikit-learn --quiet
```

---

## How to Run the Analysis

### Step 1: Open Google Colab

Create a new Google Colab notebook.

### Step 2: Install the required packages

Run the installation cell included in the notebook.

### Step 3: Upload the cleaned dataset

The script uses:

```python
from google.colab import files
uploaded = files.upload()
```

Upload your cleaned `.csv` or `.xlsx` dataset.

### Step 4: Update the variable configuration section

Before running the full analysis, confirm that the variable names in the script match the column names in your dataset.

### Step 5: Run all cells

The notebook will generate tables for Appendices C–J.

### Step 6: Download the Excel output

At the end of the workflow, download:

```text
Appendices_C_to_J_Statistical_Outputs.xlsx
```

---

## Important Notes

### Dependent Variable

The dependent variable should be bounded between 0 and 1.

In the current thesis workflow, the main outcome is:

```text
high_adoption
```

coded as:

```text
0 = lower adoption
1 = high adoption
```

Because the outcome is binary, the GLM probit specification should be interpreted as a probit-type model.

---

### Digital Financial Inclusion Reliability

If digital financial inclusion is measured using multiple behavioural usage indicators, Cronbach’s alpha may be low because the items may not represent a reflective psychometric scale.

In such cases, the index should be interpreted cautiously as a behavioural or formative usage index rather than as a purely reflective construct.

---

### Machine-Learning Results

The XGBoost and SHAP outputs are intended as supplementary predictive and explanatory checks. They should not replace the main inferential regression model.

---

## Suggested Repository Structure

```text
.
├── README.md
├── notebooks/
│   └── appendix_analysis_colab.ipynb
├── data/
│   └── README.md
├── outputs/
│   └── Appendices_C_to_J_Statistical_Outputs.xlsx
├── figures/
│   └── shap_summary_plot.png
└── requirements.txt
```

---

## Example requirements.txt

```text
pandas
numpy
scipy
factor_analyzer
statsmodels
scikit-learn
xgboost
shap
matplotlib
seaborn
openpyxl
```

---

## Research Transparency Statement

This repository is intended to support transparency, reproducibility, and auditability of the quantitative appendix outputs used in the thesis. The workflow does not alter the thesis document itself. It generates statistical tables and model outputs that can be reviewed, interpreted, and incorporated into the appendices.

---

## Ethical and Data-Protection Note

The dataset used for this analysis may contain survey responses from human participants. Users should not upload personally identifiable data to public repositories.

Before sharing this repository publicly:

- remove respondent identifiers;
- anonymise or aggregate sensitive data;
- exclude raw survey data unless appropriate permissions exist;
- follow institutional ethics and data-protection requirements.

Recommended practice is to share only:

```text
code
synthetic data
variable dictionary
non-sensitive outputs
```

---

## Citation

If this repository is cited in the thesis or related publications, use a format similar to:

```text
Author. (2026). PhD Appendix Analysis Pipeline: Digital Financial Inclusion and Digital Adoption in Nigeria. GitHub repository.
```

---

## License

Choose a license according to your institution’s policy.

Recommended options:

- MIT License for open code sharing
- CC BY 4.0 for documentation
- Private repository if the project contains sensitive or unpublished thesis materials

---

## Author

```text
[Anthony Chidi Nzomiwu]
PhD Researcher
[Department Digital Currency / Faculty Computer Science]

```

---

## Acknowledgement

This analysis pipeline was developed to support a doctoral research project on digital financial inclusion, regulatory trust, innovation adoption, and digital payment behaviour in Nigeria. The workflow promotes transparent, reproducible, and appendix-ready empirical reporting.
