# Credit Default Risk Engine

An end-to-end, leakage-free credit risk and economic optimization pipeline built on the PKDD'99 Berka dataset (`danielmuhire83-web/Credit-Default-Risk-Engine`).

## 1. Project Overview
Predicts retail banking loan defaults using strict point-in-time feature engineering, multi-model machine learning, SHAP explainability, and economic threshold optimization.

## 2. Key Highlights
- **Leakage-Free Windowing:** Enforces `trans_date < loan_date` temporal boundaries.
- **Solvency Ratios:** Engineered Payment-to-Income (PTI) and Debt Service Ratios.
- **Model Benchmarking:** Evaluated Logistic Scorecard, Random Forest, and LightGBM using PR-AUC.
- **Economic Optimization:** Replaced arbitrary 0.50 cutoffs with a monetary cost-benefit payoff matrix.

## 3. Repository Architecture

```text
credit-default-risk-engine/
│
├── data/                       # Local raw Berka tables (.asc files)
├── notebooks/                  # Step-by-step modeling notebook
├── README.md                   # Project documentation
└── requirements.txt            # Python dependencies
```

## 4. Installation & Usage
git clone https://github.com/danielmuhire83-web/Credit-Default-Risk-Engine.git
cd Credit-Default-Risk-Engine
pip install -r requirements.txt

## 5. Dataset Attribution
PKDD'99 Financial Dataset (Czech retail banking data) prepared by Petr Berka et al.

## 6. Engineering Decisions & Visuals
- **Why Point-in-Time?** Prevents lookahead bias to ensure robust production reliability.
- **Global Explainability (SHAP):** Prioritizes short-term liquidity stress over demographics.

![SHAP Beeswarm Plot](assets/shap_beeswarm.png)
