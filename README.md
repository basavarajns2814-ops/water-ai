# 💧 Water-AI

## AI-Powered Water Contamination Risk Prediction & Early Warning System

Water-AI is an **AI/ML-based environmental intelligence project** that explores whether routinely measured water-quality parameters can predict microbial contamination indicators and support early-warning decision making.

**Data Source:** Central Pollution Control Board (CPCB) via India's **National Water Data Portal (NWDP)**.

> 🚧 **Status:** Active Development — Baseline ML modeling in progress

---

## 🎯 Problem Statement

Microbial contamination of water poses serious public health risks. Traditional microbial testing is essential but is not always continuous.

Water-AI investigates whether parameters such as **pH, Dissolved Oxygen (DO), and Biochemical Oxygen Demand (BOD)** can provide predictive signals for **Fecal Coliform (MPN/100mL)** contamination.

The long-term goal is to develop an **AI-powered decision-support and early-warning system** for water-quality monitoring.

---

## 💡 Objectives

* Analyze real-world water-quality data from CPCB.
* Use physical, chemical, and biological water-quality parameters.
* Develop machine-learning models for microbial contamination prediction.
* Build an AI-powered contamination risk assessment system.
* Provide explainable predictions.
* Support early-warning decision making.

---

## 📊 Dataset

The project uses three categories of water-quality data.

### Physical Parameters

* Electrical Conductivity
* Turbidity
* Temperature
* Total Solids

### Chemical Parameters

* pH
* Dissolved Oxygen
* Ammonia
* Chloride
* Sulphate
* Metals
* Other chemical parameters

### Biological Parameters

* Biochemical Oxygen Demand (BOD)
* Chemical Oxygen Demand (COD)
* Fecal Coliform
* Total Coliform

### Dataset Validation

| Metric                                    |                Value |
| ----------------------------------------- | -------------------: |
| Total observations                        |                4,555 |
| Valid numeric Fecal Coliform observations |                3,300 |
| Physical & Chemical datasets              | Successfully aligned |
| Physical & Biological datasets            | Successfully aligned |
| Duplicate station/time records            |                    0 |

---

## 🧹 Data Cleaning

The Fecal Coliform column contained both numerical and non-numerical values.

Examples:

```text
300
360
730
910
1500
240000
Clear
Other
Light Brown
Brown
```

Non-numerical values were converted to missing values during preprocessing.

After cleaning:

```text
Total observations      : 4,555
Valid numeric FC values : 3,300
```

---

## 📈 Exploratory Data Analysis

Fecal Coliform was found to have a highly skewed distribution.

| Statistic       |    Value |
| --------------- | -------: |
| Count           |    3,300 |
| Mean            | 1,929.54 |
| Median          |      360 |
| 75th Percentile |      730 |
| Maximum         |  240,000 |

A logarithmic transformation was investigated:

```python
log1p(Fecal Coliform)
```

### Initial Correlations

| Feature          | Correlation |
| ---------------- | ----------: |
| pH               |      -0.049 |
| Dissolved Oxygen |      -0.119 |
| BOD              |      +0.155 |

The weak linear correlations indicate that **nonlinear machine-learning models** should also be investigated.

---

## 🧪 Baseline Modeling

### Features

```text
pH
Dissolved Oxygen
Biochemical Oxygen Demand (BOD)
```

### Target

```text
log(1 + Fecal Coliform)
```

### Dataset

```text
Complete samples : 2,852
Training samples : 2,281
Testing samples  : 571
```

### Baseline Model

**Random Forest Regressor**

Random Forest was selected as the initial baseline because it can capture nonlinear relationships and feature interactions in tabular datasets.

> Model evaluation is currently in progress. No performance claims are made yet.

---

## 🛠️ Tech Stack

### Current

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Scikit-learn**
* **Jupyter Notebook**
* **VS Code**
* **Git & GitHub**

### Planned

* Gradient Boosting
* XGBoost
* SHAP
* Streamlit
* FastAPI

---

## 🏗️ System Architecture

```text
Water Quality Data
        ↓
Data Processing
        ↓
Exploratory Data Analysis
        ↓
Feature Engineering
        ↓
Machine Learning
        ↓
Fecal Coliform Prediction
        ↓
Risk Assessment
        ↓
Explainable AI
        ↓
Early Warning Application
```

---

## 🗺️ Roadmap

- [x] Data Understanding
- [x] Dataset Validation
- [x] Data Cleaning
- [x] Exploratory Data Analysis
- [x] Feature Selection
- [x] Train/Test Split
- [ ] Baseline Model Evaluation
- [ ] Model Comparison
- [ ] Feature Engineering
- [ ] Temporal Analysis
- [ ] Spatial Analysis
- [ ] Risk Classification
- [ ] Explainable AI
- [ ] Prediction API
- [ ] Interactive Dashboard
- [ ] Deployment

---

## 📁 Project Structure

```text
Water-AI/
│
├── app/
│   └── app.py
│
├── notebooks/
│   ├── 01_data_understanding.ipynb
│   ├── 02_data_cleaning.ipynb
│   ├── 03_eda.ipynb
│   ├── 04_feature_engineering.ipynb
│   └── 05_modeling.ipynb
│
├── src/
│   ├── data_processing.py
│   ├── features.py
│   └── prediction.py
│
├── data/
│   └── README.md
│
├── requirements.txt
├── .gitignore
└── README.md
```

---

## 🚀 Future Work

* Compare multiple machine-learning algorithms.
* Add additional water-quality features.
* Investigate temporal contamination patterns.
* Investigate geographic contamination patterns.
* Develop contamination risk classification.
* Add Explainable AI using SHAP and feature importance.
* Build a prediction API.
* Develop an interactive monitoring dashboard.
* Investigate integration with real-time sensor data.
* Perform robust model validation and monitoring.

---

## ⚠️ Limitations

* The project is currently a research prototype.
* The dataset contains missing values across several parameters.
* Fecal Coliform has a highly skewed distribution.
* Historical monitoring data is not the same as continuous sensor data.
* Model generalization has not yet been validated.
* Laboratory testing remains essential for confirming actual contamination.

---

## 📖 Data Source

Publicly available water-quality monitoring data from the **Central Pollution Control Board (CPCB)** via the **National Water Data Portal (NWDP)**.

Raw datasets are **not included** in this repository.

---

## ⚖️ Disclaimer

Water-AI is an **experimental AI/ML research and decision-support project**.

Predictions should not be treated as definitive evidence of water safety or contamination without appropriate laboratory testing and expert validation.
>>>>>>> 18a9083 (docs: update Water-AI README)
