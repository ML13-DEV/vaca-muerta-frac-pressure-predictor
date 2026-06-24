# 🛢️ Vaca Muerta Frac Pressure Predictor

![Python](https://img.shields.io/badge/Python-3.10%2B-3776AB?style=flat&logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?style=flat&logo=jupyter&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-Model-0066CC?style=flat)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Wrangling-150458?style=flat&logo=pandas&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-Client--Side%20Inference-F7DF1E?style=flat&logo=javascript&logoColor=black)
![CRISP--DM](https://img.shields.io/badge/Methodology-CRISP--DM-2E7D32?style=flat)
![No Backend](https://img.shields.io/badge/Backend-None%20%E2%80%94%20Static%20Site-success?style=flat)

## 📌 Overview

This project predicts the peak pressure reached during hydraulic fracturing operations in Vaca Muerta and other Argentine oil wells, based on key operational variables. The trained model is exported and deployed as a fully static, client-side web app — no server, no Python backend, just HTML/CSS/JS.

## 🔑 Key Features

Built end-to-end following the **CRISP-DM** methodology:

- **Business & Data Understanding** — Framed around estimating frac cost and pressure to support well-planning decisions, using historical data from Vaca Muerta and other fields.
- **EDA & Feature Selection** — Identified the most influential variables: horizontal lateral length, number of fracturing stages, injected water volume, total sand/proppant, and equipment power (HP).
- **Modeling** — Trained an XGBoost regression model in Python (`caso_frackeos.ipynb`).
- **Client-Side Deployment (the highlight)** — The trained XGBoost ensemble was exported as a JSON tree structure and re-implemented in plain JavaScript, so every prediction runs **entirely in the browser** — no Flask, no Streamlit, no server round-trip.
- **Interactive Dashboard** (`index.html`) — A two-tab static web app:
  - **Dashboard tab**: EDA panels covering exploratory analysis & model performance, correlations & key findings, and distribution analysis.
  - **Simulador tab**: Sliders for each input variable feed live into the embedded model, returning an instant PSI prediction with a gauge visualization, a percentile estimate against the historical distribution, and automatic operational alerts (e.g. a warning when predicted pressure approaches standard casing resistance limits).

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| Modeling (notebook) | Python, Pandas, NumPy, Scikit-learn, XGBoost, Matplotlib/Seaborn |
| Deployment (web app) | HTML5, CSS3, vanilla JavaScript — no framework, no backend |
| Methodology | CRISP-DM |

## ⚙️ How to Run / Installation

This repo has two independent pieces — the analysis notebook and the deployed app.

**1. Notebook (model training & EDA):**
```bash
git clone https://github.com/ML13-DEV/vaca-muerta-frac-pressure-predictor.git
cd vaca-muerta-frac-pressure-predictor
python -m venv venv
source venv/bin/activate      # On Windows: venv\Scripts\activate
pip install pandas numpy scikit-learn xgboost matplotlib seaborn jupyter
jupyter notebook caso_frackeos.ipynb
```

**2. Web app (interactive simulator):**
No installation needed — it's a static page with the model already embedded.
```bash
# Just open it directly in a browser
open index.html        # macOS
# or double-click index.html on Windows/Linux

# Or serve it locally (optional, avoids any local-file browser restrictions):
python -m http.server 8000
# then visit http://localhost:8000/index.html
```

## 📂 Repository Structure

```
vaca-muerta-frac-pressure-predictor/
├── caso_frackeos.ipynb   # CRISP-DM pipeline: EDA, feature selection, XGBoost training, model export
├── index.html            # Static dashboard + simulator (model runs client-side in JS)
└── README.md
```

## 📈 Notes

Originally an academic case study; the XGBoost-to-JavaScript export turns it into a zero-dependency, instantly shareable demo — anyone can open `index.html` and get live predictions with nothing installed.
