# Battery Aging — State of Health (SOH) Estimation using Machine Learning

This repository contains an independent research-style project on **data-driven State-of-Health (SOH) estimation for lithium-ion batteries** using the NASA battery aging dataset.  
The project was developed as a self-study and academic research exercise to demonstrate readiness for graduate-level study in **Computer Science / Artificial Intelligence**, with a focus on **machine learning for real-world engineering systems**.

---

## Project Overview

Lithium-ion batteries degrade over time due to complex electrochemical and mechanical processes.  
Accurate estimation of **State-of-Health (SOH)** is critical for:

- Predictive maintenance  
- Safety monitoring  
- Lifetime estimation  
- Sustainable energy systems (EVs, storage)

This project investigates whether **machine learning models** can generalize across **different battery cells** and predict SOH using only **measurable discharge signals**.

---

## Dataset

**Source:**  
NASA Open Data Portal — Li-ion Battery Aging Datasets  
https://data.nasa.gov/dataset/li-ion-battery-aging-datasets
or you can download it from my own github repository


The dataset contains controlled aging experiments on multiple lithium-ion cells.  
This project uses a single CSV file (`discharge.csv`) containing discharge-cycle measurements.

### Raw signals used
- Voltage  
- Current  
- Temperature  
- Time  
- Discharge capacity  

---

## Problem Formulation

Given discharge-cycle measurements, the goal is to predict battery **State-of-Health (SOH)** defined as:

