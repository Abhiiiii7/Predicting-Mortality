# Predicting Mortality in Sepsis-Associated ARDS (MIMIC-III)

This repository contains an end-to-end analytics workflow to **predict in-hospital mortality** for **sepsis-associated Acute Respiratory Distress Syndrome (ARDS)** patients using the **MIMIC-III** clinical database.

It includes:
- **SQL (BigQuery)** to define the ICU cohort and engineer features from MIMIC-III
- **Python** to clean data, train baseline ML models, and evaluate performance
- A full **report (PDF)** and **slides (PPTX)** used to present results

## Tech stack
- SQL (CTEs, joins, aggregation) – BigQuery on `physionet-data.mimiciii_clinical` tables
- Python: pandas, numpy, scikit-learn, xgboost

## Repository structure
```
.
├── sql/
│   └── mimic_sepsis_ards_extraction.sql
├── src/
│   └── train_models.py
├── notebooks/
│   └── SepsisARDS_Python_code.html
├── reports/
│   └── REPORT-BANA650.pdf
├── slides/
│   └── Sepsis_ARDS_Final.pptx
├── data/
│   ├── README.md
│   └── sample_ards_dataset.csv
├── requirements.txt
└── .gitignore
```

## Data
The **full dataset is not included** by default.

If your dataset was created from **MIMIC-III**, do **not** upload patient-level exports to a public repository unless you are sure it complies with the relevant data use terms.

See `data/README.md` for how to organize data locally.

## How to run (quick start)
1) Create and activate a virtual environment (recommended)

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
# macOS/Linux:
source .venv/bin/activate
```

2) Install dependencies

```bash
pip install -r requirements.txt
```

3) Run baseline model training

```bash
python src/train_models.py --data data/sample_ards_dataset.csv
```

If you have the full dataset locally:

```bash
python src/train_models.py --data data/ARDS-Final_Dataset.csv
```

Model metrics will print to the console and save to:
- `outputs/model_metrics.csv`

## Results (from the accompanying report)
The report documents the following test-set performance snapshot:
- Logistic Regression: **AUC ≈ 0.7488**, **Recall ≈ 0.8056**
- Random Forest: **AUC ≈ 0.7416**
- XGBoost: **AUC ≈ 0.7415**
- Naive Bayes: **Recall ≈ 0.8963** (higher sensitivity, lower precision)

See `reports/REPORT-BANA650.pdf` for full details (cohort definition, features, metrics, and feature importance).

## What to highlight on a resume
- Cohort definition + extraction from a relational clinical database (SQL)
- Feature engineering (labs, vitals, comorbidity flags, severity scores)
- Reproducible analysis pipeline (Python)
- Model comparison with evaluation metrics (AUC, recall, accuracy)
- Stakeholder-friendly communication (report + slides)

## Notes
- The included dataset in `data/sample_ards_dataset.csv` is **synthetic** (for demo/testing only).
- The HTML notebook export is provided for transparency; converting to an `.ipynb` notebook is recommended if you have the original.
