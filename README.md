# Predictive Analytics & Machine Learning for Bike‑Sharing Demand

**Master’s thesis project (TU Chemnitz, M.Sc. Web Engineering)** — a reproducible ML workflow for forecasting hourly bike rental demand using the Kaggle *Bike Sharing Demand* dataset.

> **Thesis title:** *Predictive Analytics and Machine Learning For Bike Sharing Demand in Heterogeneous Urban Environments*  
> **Author:** Diwakar Dangal  
> **Date:** May 2024

## Project summary
Public bike-sharing operators need accurate demand forecasts to reduce rebalancing issues (empty/full stations) and improve customer experience. This project benchmarks multiple models and shows how feature engineering and preprocessing improve performance.

**Models evaluated**
- Random Forest Regressor
- Gradient Boosting Regressor
- LightGBM Regressor (**best overall**)
- Neural Network baseline

**Key results (from the thesis)**
- Stepwise improvements reduced Kaggle RMSLE from **0.6878 → 0.38576** (top ~4% on the Kaggle leaderboard at the time of submission).
- Feature engineering (e.g., `peak`, `sticky`) and log-transforming the target were particularly impactful.

## Repository structure
```
.
├── notebooks/                # Jupyter notebooks (clean + original backup)
├── src/                      # Minimal reproducible training pipeline (Python scripts)
├── scripts/                  # Helper scripts (e.g., Kaggle download)
├── thesis/                   # Thesis PDF (full + public version)
├── data/                     # (empty) place dataset here locally (ignored by git)
├── models/                   # (empty) saved models (ignored by git)
└── reports/                  # optional exports (figures, tables, etc.)
```

## Data (Kaggle)
This project uses the Kaggle competition dataset **Bike Sharing Demand**.

**Recommended approach:** do **not** commit the dataset to GitHub. Instead, download it locally.

### Option A — Kaggle API
1. Install Kaggle CLI and set up your API token (Kaggle docs).
2. Run:
```bash
kaggle competitions download -c bike-sharing-demand -p data/raw
unzip -o data/raw/bike-sharing-demand.zip -d data/raw
```
You should have:
- `data/raw/train.csv`
- `data/raw/test.csv`

### Option B — Manual download
Download from Kaggle and place the CSVs in `data/raw/`.

## Quickstart (local)
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install -r requirements.txt

python -m src.train_lightgbm --train data/raw/train.csv --test data/raw/test.csv
```

## Reproducing the thesis notebooks
- Clean notebook (no outputs): `notebooks/Appendix_modelling.ipynb`
- Original notebook backup: `notebooks/Appendix_modelling_original.ipynb`

![Cover image](assets/Data%20analysis%20gitter%20plot.png)

## Thesis PDF
- `thesis/thesis_public.pdf` — recommended for GitHub (last “statement of authorship” page removed).
- `thesis/thesis_full.pdf` — full export.

## Citation
If you use this work, please cite the thesis. See `CITATION.cff`.

## License
- Code: MIT (see `LICENSE`)
- Thesis PDF: please choose a license you are comfortable with (e.g., CC BY 4.0) and update the repo accordingly.
