# Data Instructions

The raw survey data is **not included** in this repository due to file size (~141 MB).

## How to Download

1. Visit the official Stack Overflow survey page:  
   👉 https://survey.stackoverflow.co/

2. Download the **2025 Developer Survey** results package (ZIP file).

3. Extract the ZIP and place the following two files in the **root of this repository**:

```
survey_results_public.csv     ← Main survey responses (~49,000 rows, 172 columns)
survey_results_schema.csv     ← Column descriptions and question text
```

4. Your directory should look like this before running the notebook:

```
so-survey-2025-analysis/
├── README.md
├── requirements.txt
├── .gitignore
├── DATA.md                        ← This file
├── so_survey_analysis.ipynb
├── survey_results_public.csv      ← ✅ Place here after download
└── survey_results_schema.csv      ← ✅ Place here after download
```

## Dataset Overview

| Property | Value |
|----------|-------|
| Source | Stack Overflow Annual Developer Survey 2025 |
| Rows | 49,191 respondents |
| Columns | 172 features |
| License | [Open Database License (ODbL)](https://opendatacommons.org/licenses/odbl/1-0/) |
| Target variable | `JobSat` — self-reported job satisfaction (0–10 scale) |

## Key Features Used in This Analysis

| Column | Description |
|--------|-------------|
| `JobSat` | Job satisfaction score (0 = most dissatisfied, 10 = most satisfied) |
| `ConvertedCompYearly` | Annual compensation converted to USD |
| `YearsCode` | Total years writing code |
| `WorkExp` | Years of professional work experience |
| `AISelect` | Frequency of AI tool usage (daily / weekly / monthly / no) |
| `AIThreat` | Whether respondent believes AI threatens their job |
| `RemoteWork` | Work arrangement (remote / hybrid / in-person) |
| `EdLevel` | Highest level of education attained |
| `Age` | Age bracket |
| `OrgSize` | Size of employing organisation |
| `ICorPM` | Individual contributor vs people manager |
| `ToolCountWork` | Number of tools used at work |
| `ToolCountPersonal` | Number of tools used on personal projects |
