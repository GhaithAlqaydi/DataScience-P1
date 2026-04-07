# DataScience-P1
# 🧑‍💻 Stack Overflow Developer Survey 2025 — ML Analysis

> *What makes a developer happy in the age of AI?*  
> A machine-learning deep-dive into the 2025 Stack Overflow Developer Survey.

---

## 📌 Motivation

The Stack Overflow Developer Survey is one of the largest annual studies of software professionals in the world. In 2025, it captures a pivotal moment: AI tools have gone from niche experiment to daily workflow staple for millions of developers. This project asks:

1. **What structural factors best predict a developer's job satisfaction?**
2. **Does embracing AI tools correlate with being happier at work?**
3. **Does fearing AI as a job threat correlate with lower satisfaction?**
4. **Can we predict satisfaction for a hypothetical developer profile?**

The goal is to answer these questions with data — using exploratory analysis, correlation, and a trained machine learning model — and to translate findings into insights accessible to non-technical readers.

---

## 📚 Libraries Used

| Library | Purpose |
|---------|---------|
| `pandas` | Data loading, cleaning, and manipulation |
| `numpy` | Numerical operations and transformations |
| `matplotlib` | Base plotting and figure layout |
| `seaborn` | Statistical visualisations (heatmaps, distributions) |
| `scikit-learn` | PCA, label encoding, train/test split, GradientBoostingRegressor, metrics |
| `warnings` | Suppressing non-critical warnings during execution |

---

## 📁 Repository Structure

```
.
├── README.md                    ← You are here
├── so_survey_analysis.ipynb     ← Full analysis notebook (EDA → cleaning → model → scenario)
├── survey_results_public.csv    ← Raw survey data (download separately — see Data section)
└── survey_results_schema.csv    ← Column schema and question descriptions
```

> **Note:** The raw CSV files are not committed to this repository due to file size (~141 MB). Download the data from the [Stack Overflow Annual Developer Survey page](https://survey.stackoverflow.co/) and place both CSV files in the root of this repository before running the notebook.

---

## 📓 Notebook Overview (`so_survey_analysis.ipynb`)

The notebook is divided into four sequential steps:

### Step 1 — Exploratory Data Analysis
- Null-rate audit across key features
- Distribution plots: JobSat target, compensation (raw + log), age, education, remote work, coding experience
- PCA on numeric features, coloured by satisfaction score
- **Correlation matrix and bar chart** — Pearson r between all numeric features and `JobSat`

### Step 2 — Data Cleaning & Feature Engineering
- Drop rows with missing target (`JobSat`)
- Log-transform and winsorise compensation (99th percentile cap)
- Median imputation for numeric features; `'Unknown'` fill for categoricals
- Label-encode 7 categorical variables
- Engineer binary flags: `UsesAI`, `IsRemote`, `AIFearsJob`
- Final feature matrix: **14 features**, **~26,000 samples**

### Step 3 — Model Training & Evaluation
- **Model:** `GradientBoostingRegressor` (300 estimators, lr=0.05, max_depth=4)
- 80/20 train-test split + 5-fold cross-validation
- Metrics: MAE, RMSE, R²
- Plots: predicted vs actual, residuals, feature importances, MAE by satisfaction bucket

### Step 4 — Creative Predictive Scenario
- Three fictional developer profiles (Alex, Jordan, Morgan) constructed with varying AI attitudes, pay, and work mode
- Model predicts satisfaction for each
- Findings interpreted for HR/recruiting audience

---

## 📊 Summary of Results

### Key Correlation Findings

| Feature | r with JobSat | Direction |
|---------|:------------:|-----------|
| Fears AI will take job | −0.125 | ↓ Strong negative |
| Work experience (years) | +0.106 | ↑ Positive |
| Years coding | +0.094 | ↑ Positive |
| Log compensation | +0.080 | ↑ Positive |
| Works remotely | +0.040 | ↑ Slight positive |
| Uses AI tools | +0.024 | ↑ Slight positive |
| Tool count (work) | ≈ 0 | Neutral |

### Model Performance

| Metric | Value | Interpretation |
|--------|-------|---------------|
| **MAE** | ~1.25 | Predictions off by ~1.25 points (0–10 scale) |
| **RMSE** | ~1.65 | Penalises large errors more heavily |
| **R²** | ~0.18 | Model explains ~18% of satisfaction variance |

An R² of ~0.18 is expected for human-attitude prediction — much of satisfaction is driven by unmeasured factors (manager quality, team culture, personal life). The model captures the *structural* signal reliably.

### Creative Scenario Result

> Among three hypothetical developer profiles, the **senior developer who uses AI daily, works fully remote, and does not fear AI** is predicted to have the highest job satisfaction — even compared to a higher-seniority people manager who avoids AI and works in-office.

**Takeaway:** In 2025, *AI adoption mindset* and *remote flexibility* are as powerful as seniority in shaping developer satisfaction.

---

## 🙏 Acknowledgments

- **Stack Overflow** for making the annual developer survey publicly available: https://survey.stackoverflow.co/
- **scikit-learn** contributors for the open-source ML ecosystem
- **Seaborn / Matplotlib** teams for the visualisation libraries
- Inspired by Josh Bernhard's sample project: *How Do YOU Become A Developer?*

---

## 🚀 How to Run

```bash
# 1. Clone the repo
git clone https://github.com/YOUR_USERNAME/so-survey-2025-analysis.git
cd so-survey-2025-analysis

# 2. Download data from https://survey.stackoverflow.co/
#    Place survey_results_public.csv and survey_results_schema.csv in root

# 3. Install dependencies
pip install pandas numpy matplotlib seaborn scikit-learn notebook

# 4. Launch Jupyter
jupyter notebook so_survey_analysis.ipynb
```

---

*Analysis conducted using Stack Overflow Developer Survey 2025 data (49,191 respondents).*
