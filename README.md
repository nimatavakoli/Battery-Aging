# 🔋 Battery Aging Prediction using Machine Learning

## Overview
This repository contains a **Jupyter Notebook (`BatteryAging.ipynb`)** that implements a complete machine learning workflow for **battery aging prediction** using the **NASA Li-ion Battery Aging Dataset**.

The notebook demonstrates how raw, uncleaned discharge measurements can be transformed into meaningful **cycle-level features**, followed by robust model training and evaluation.  
The project is designed as an **academic portfolio project** for **M.Sc. applications in Computer Science / Artificial Intelligence**.

---

## Dataset
**Source:** NASA Ames Prognostics Center of Excellence  
🔗 https://data.nasa.gov/dataset/li-ion-battery-aging-datasets
or you can Download it from my own Repository

**File used:**
- `discharge.csv`

**Description:**  
The dataset consists of time-series measurements collected during battery discharge cycles, including voltage, current, temperature, and time.  
Each battery is tested across many cycles until performance degradation occurs.

---

## Notebook Structure (`BatteryAging.ipynb`)

The notebook is organized into clearly separated sections:

1. **Data Loading & Cleaning**
   - Load raw CSV data
   - Filter discharge cycles
   - Handle missing or invalid entries

2. **Feature Engineering**
   - Group data by `Battery` and `id_cycle`
   - Aggregate time-series signals into cycle-level statistical features

3. **Modeling**
   - Train multiple regression models:
     - Linear Regression
     - ElasticNet
     - Random Forest
     - Gradient Boosting
     - Extra Trees

4. **Evaluation**
   - Use **Leave-One-Group-Out Cross-Validation**
   - Ensure leakage-free evaluation by holding out entire batteries
   - Report MAE, RMSE, and R² scores

5. **Results & Analysis**
   - Compare model performance per battery
   - Analyze generalization behavior on unseen cells

---

## Validation Strategy
To ensure realistic and unbiased results, the notebook uses:

**Leave-One-Group-Out Cross-Validation (LOGO)**  
- Group definition: Battery ID  
- Each fold evaluates the model on a completely unseen battery

This reflects real-world scenarios where models must generalize to new battery cells.

---

## How to Run the Notebook

### Requirements
- Python 3.9+
- Jupyter Notebook / JupyterLab
- pandas
- numpy
- scikit-learn


## Author

- Nima Tavakoli Banizi
- B.Sc. Computer Science
- Focus: Machine Learning, Battery Aging, EV Systems
