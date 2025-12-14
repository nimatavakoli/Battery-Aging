Battery Aging Prediction using Machine Learning
Overview

This repository contains a machine learning pipeline for battery aging prediction using the NASA Li-ion Battery Aging Dataset.
The goal of this project is to model and predict battery degradation behavior by extracting cycle-level features from raw discharge measurements and evaluating different regression models.

The project is designed to demonstrate:

Proper data preprocessing for real-world, uncleaned industrial datasets

Feature engineering from time-series sensor data

Model evaluation with strict data leakage prevention

Interpretable performance analysis per battery cell

This work is intended as an academic project for applications to M.Sc. programs in Computer Science / Artificial Intelligence.

Dataset

Source: NASA Ames Prognostics Center of Excellence
Link: https://data.nasa.gov/dataset/li-ion-battery-aging-datasets
or you can download it from my Repository

File used:

discharge.csv

Description:
The dataset contains time-series measurements collected during battery discharge cycles, including voltage, current, temperature, and time.

Each battery is tested over many charge–discharge cycles until degradation.

Problem Definition

Battery aging is reflected in the gradual degradation of battery capacity and performance over charge–discharge cycles.

In this project:

Raw discharge measurements are aggregated into cycle-level statistical features

Machine learning models are trained to predict aging-related targets

Model generalization is evaluated by holding out entire batteries

This simulates a realistic industrial scenario:
predicting aging behavior for unseen battery cells.

Methodology
1. Data Preprocessing

Filter only discharge cycles

Remove invalid or non-relevant rows

Group data by Battery and id_cycle

2. Feature Engineering

Raw time-series signals are aggregated per cycle using:

Mean

Standard deviation

Minimum / maximum values

This transforms high-frequency sensor data into a compact and informative feature set.

3. Modeling

The following regression models are used:

Linear Regression (baseline)

ElasticNet (regularized linear model)

Random Forest Regressor

Gradient Boosting Regressor

Extra Trees Regressor

4. Evaluation Strategy

To prevent data leakage, evaluation is performed using:

Leave-One-Group-Out Cross-Validation (LOGO)

Group = Battery ID

Each fold tests on a completely unseen battery

5. Metrics

Model performance is reported using:

MAE (Mean Absolute Error)

RMSE (Root Mean Squared Error)

R² Score

Results are shown:

Per battery

Overall across all batteries

Repository Structure
Battery-Aging/
│
├── batteryAging.py        # Main ML pipeline script
├── README.md               # Project documentation
├── requirements.txt        # Python dependencies (optional)

How to Run
Requirements

Python 3.9+

pandas

numpy

scikit-learn

Install dependencies:

pip install pandas numpy scikit-learn

Run the script

Edit the dataset path inside the script if needed, then:

python batteryAging.py


The script will:

Load the dataset

Train multiple models

Print evaluation metrics per battery and overall

Key Technical Highlights

Real-world uncleaned dataset handling

Cycle-level aggregation from time-series data

Strict leakage-safe validation strategy

Comparison of linear vs ensemble models

Industry-relevant battery degradation modeling

Academic Relevance

This project demonstrates practical skills in:

Machine learning for time-series data

Feature engineering

Model evaluation and validation

Applied data science in energy systems

It is suitable as:

A portfolio project

A research-style ML project

Supporting material for graduate program applications

Author

Nima Tavakoli Banizi
B.Sc. Computer Science
Focus: Machine Learning, Battery Aging, EV Systems
