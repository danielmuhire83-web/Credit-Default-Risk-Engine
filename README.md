# Credit Default Risk Engine & Decision Pipeline

An end-to-end, leakage-free credit scoring and economic optimization pipeline built on the PKDD'99 Czech retail banking dataset. Designed for portfolio demonstration and high-performance data science roles (such as the JPMorganChase Data & AI internship).

---

## 1. Project Overview
Financial institutions face significant credit risk when issuing unsecured loans. Evaluating whether an applicant is likely to default requires analyzing historical account behavior, cash-flow stability, and debt obligations.

This project upgrades a standard exploratory analysis into an enterprise-grade risk engine by implementing rigorous data governance, point-in-time feature engineering, multi-model benchmarking, SHAP interpretability, and expected-loss monetary optimization.

---

## 2. Key Technical & Engineering Highlights

* **Leakage-Free Temporal Windowing:** Enforces a strict point-in-time boundary (`trans_date` < `loan_date`) across all transaction histories to completely eliminate lookahead bias.
* **Solvency & Debt Burden Ratios:** Engineered critical banking risk indicators including **Payment-to-Income (PTI)** ratios, **Total Debt Service Ratios (DSR)**, and balance volatility coefficients.
* **Model Benchmarking & Class Imbalance Handling:** Addressed severe class imbalance (~11.19% default rate) across a Logistic Regression Scorecard, Random Forest, and LightGBM/Gradient Boosting classifiers using PR-AUC and ROC-AUC evaluation.
* **Regulatory Compliance via SHAP:** Implemented global feature importance beeswarm plots and local individual waterfall risk breakdowns to satisfy regulatory standards (FCRA / ECOA).
* **Economic Threshold Optimization:** Replaced arbitrary $0.50$ classification cutoffs with a custom monetary cost-benefit payoff matrix, locating the optimal decision threshold ($\tau^*$) that maximizes net portfolio profitability.

---

## 3. Repository Architecture

```text
credit-default-risk-engine/
│
├── data/                       # Local raw Berka tables (.asc files)
├── notebooks/                  # Step-by-step modeling notebook
├── README.md                   # Project documentation
└── requirements.txt            # Python dependencies
```
## 4. Getting Started & Installation

1. Clone the repository:
   `git clone https://github.com/danielmuhire83-web/Credit-Default-Risk-Engine.git`
   `cd Credit-Default-Risk-Engine`

2. Install dependencies:
   `pip install -r requirements.txt`

3. Run the pipeline:
   Open your Jupyter notebook environment and execute the structured cells sequentially from data ingestion to economic threshold optimization.

## 5. Dataset Attribution & References

* **Dataset Name:** PKDD'99 Financial Dataset (Czech retail banking data)
* **Authors / Contributors:** Prepared by Petr Berka et al. for the Principles of Data Mining and Knowledge Discovery (PKDD'99) discovery challenge.
* **Access Source:** Available via public financial data repositories and local raw .asc table archives.

## 6. Engineering Decisions & Challenges
* **Why Point-in-Time Windowing Matters:** Standard tutorials aggregate all customer data at once, which introduces lookahead bias. Enforcing strict date cutoffs (`trans_date < loan_date`) dropped baseline accuracy metrics on paper, but ensured the model would not fail catastrophically on unseen future data.
* **Handling Class Imbalance:** With an 11.19% default rate, accuracy was completely useless. Optimizing for PR-AUC and tuning the economic threshold shifted the model from guessing random cutoffs to actually maximizing bank net interest margins.
