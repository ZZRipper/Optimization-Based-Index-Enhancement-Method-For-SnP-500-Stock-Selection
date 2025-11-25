# Optimization-Based Index Enhancement for the S&P 500

**TL;DR.** A linear-programming (LP) optimizer tilts portfolio weights toward a cross-sectional signal while controlling name/sector deviations, turnover, and trading costs. We rebalance monthly, run a small hyperparameter grid, and evaluate out-of-sample performance (IR/TE/turnover/costs). The full write-up is in the PDF report; the runnable pipeline is the notebook.

- 📓 Notebook: **[Optimization_final_project (1).ipynb](sandbox:/mnt/data/Optimization_final_project%20(1?_chatgptios_conversationID=6906d6e5-7028-8327-acc1-b00700ff0571&_chatgptios_messageID=cd2963a6-cb3d-4ea2-bb0f-29985d1f2359).ipynb)**
- 📄 Report: **[optimization_final_project_report (2).pdf](sandbox:/mnt/data/optimization_final_project_report%20(2?_chatgptios_conversationID=6906d6e5-7028-8327-acc1-b00700ff0571&_chatgptios_messageID=cd2963a6-cb3d-4ea2-bb0f-29985d1f2359).pdf)**

---

## 1) What is this?

This project implements an optimization-based index-enhancement strategy on the S&P 500 universe:

- **Objective.** Maximize signal-implied return net of linear trading costs.  
- **Constraints.** Full investment, single-name active-weight bands, sector neutrality/tolerance, turnover cap, and basic box bounds.  
- **Absolute-value linearization.** Turnover and active-weight |·| terms are modeled with auxiliary variables so the problem remains LP.

**Why this matters.** It cleanly separates *alpha view* (signal in the objective) from *risk & implementability* (constraints), producing a reproducible and explainable enhancement overlay to a benchmark portfolio.

---

## 2) Files in this repo

- `Optimization_final_project (1).ipynb` — end-to-end code: data prep → monthly LP solve → backtest → plots.
- `optimization_final_project_report (2).pdf` — the final paper with model details, grid set-up, and empirical results.
- (optional) `data/` — put your inputs here (not tracked by git; see `.gitignore` below).
- (optional) `results/` — generated figures/tables from the notebook.

---

## 3) Quick start

> **Option A — Minimal install**
```bash
# (optional) create a clean venv
# python -m venv .venv && source .venv/bin/activate

pip install -r requirements.txt
# If you don't have a requirements file yet, install the minimum:
# pip install pyomo highspy pandas numpy matplotlib jupyter

jupyter lab   # or: jupyter notebook
# Open  "Optimization_final_project (1).ipynb"  and run cells top-to-bottom.
