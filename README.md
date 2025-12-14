# 🔋 Battery Aging Prediction using Machine Learning (NASA Dataset)

This repository contains a Jupyter Notebook **`BatteryAging.ipynb`** that implements an end-to-end machine learning workflow to predict **battery State of Health (SOH)** from discharge-cycle measurements using the **NASA Li-ion Battery Aging Dataset**.

The notebook demonstrates how raw, time-series discharge measurements can be transformed into **cycle-level features**, followed by **leakage-safe model training and evaluation**.  

---

## Key Objectives
- Convert raw discharge time-series into informative **cycle-level features**
- Define a robust SOH target using a stable initial capacity baseline
- Train and compare multiple regression models
- Evaluate generalization using **Leave-One-Battery-Out** validation (LOGO CV)

---

## Dataset
**Source:** NASA Ames Prognostics Center of Excellence (PCoE)  
Dataset portal:  
- https://data.nasa.gov/dataset/li-ion-battery-aging-datasets

**File used in this project**
- `discharge.csv`

**Description (high level)**  
The dataset contains time-series measurements recorded during discharge cycles, including:
- Voltage, current, temperature, ambient temperature
- Time index within the cycle
- Capacity-related measurement
- Identifiers: `Battery`, `id_cycle`

Each battery is cycled over time until significant performance degradation occurs.

> Note: You can download the original dataset from the NASA portal above.  
> If a copy is also provided in this repository for convenience, it is included only for reproducibility.

---

## Method Summary

### 1) Data Loading & Cleaning
- Load raw CSV data
- Filter discharge cycles (`type == "discharge"`)
- Remove missing/invalid entries for key measurement channels

### 2) Feature Engineering (Cycle-Level)
Raw time-series samples are grouped by **(Battery, id_cycle)** and transformed into one record per cycle, including:
- Statistical descriptors of voltage/current/temperature (mean/std/min/max)
- Cycle duration
- Curve-shape / physics-informed descriptors (e.g., delivered charge/energy or curve sampling, depending on notebook version)

### 3) Target Definition: SOH
SOH is computed from discharge capacity relative to a robust initial baseline:
- **C₀** = median of capacity over the first *N* cycles (e.g., first 10 cycles per battery)
- **SOH(%)** = (Capacity_cycle / C₀) × 100

### 4) Modeling
The notebook trains and evaluates multiple regressors, including:
- Linear Regression
- ElasticNet
- Random Forest
- Gradient Boosting
- Extra Trees
- (Optional) HistGradientBoosting / MLPRegressor (if enabled in the notebook)

### 5) Evaluation (Leakage-Safe)
**Leave-One-Group-Out Cross-Validation (LOGO)** is used with:
- **Group = Battery ID**
- Each fold tests on a completely unseen battery

Metrics reported:
- MAE, RMSE, R²
- Overall performance and per-battery performance

---

## Results
Results depend on:
- the feature set used (basic statistical features vs. enhanced curve features)
- whether cycle-index priors are included (`id_cycle`, `log_cycle`)
- the chosen models and hyperparameters

The notebook prints:
- Overall metrics (pooled across folds)
- Per-battery metrics
- Model ranking (optionally best model per battery)

If you want, you can add your final numbers here after running:

- **Best overall model:** _(fill after run)_
- **Best model for B0006:** _(fill after run)_

---

## Validation Strategy (Why LOGO CV?)
Random train/test splits can leak information because cycles from the same battery may appear in both training and testing.  
This repository uses **Leave-One-Battery-Out (LOGO)** evaluation to reflect real deployment scenarios where the model must generalize to **new, unseen batteries**.

---

## How to Run

### Requirements
- Python 3.9+
- Jupyter Notebook / JupyterLab

Install dependencies:
```bash
pip install numpy pandas scikit-learn matplotlib
