<div align="center">
  
# 🎯 Predictive Threat Intelligence Engine

**A full-lifecycle Machine Learning pipeline for modeling, classifying, and forecasting global security incidents.**

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg?style=flat-square&logo=python&logoColor=white)]()
[![Machine Learning](https://img.shields.io/badge/ML-Random_Forest-FF9900.svg?style=flat-square)]()
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit_Learn-150458.svg?style=flat-square)]()

</div>

---

## 🔬 Project Focus: Applied Machine Learning

While this project includes an interactive front-end, its core lies in **data science and predictive modeling**. The goal of this system is to handle the highly categorical, imbalanced, and complex nature of the Global Terrorism Database (GTD) and extract reliable predictions using ensemble methods and regression techniques.

Rather than just serving as a data visualization tool, this project demonstrates a complete ML lifecycle: **Data Ingestion ➔ Feature Encoding ➔ Model Training ➔ Inference ➔ Evaluation.**

---

## 🧠 Machine Learning Architecture

The predictive engine relies on Scikit-Learn algorithms, chosen specifically for the shape and distribution of the GTD dataset:

### 1. Attack Typology Classification
*   **Algorithm:** `Random Forest Classifier`
*   **Preprocessing:** `LabelEncoder` is utilized to transform highly categorical text features (Country, Region, Target Type, Weapon Type) into machine-readable numeric matrices.
*   **Why Random Forest?** The GTD dataset contains highly non-linear relationships. Random Forest builds an ensemble of decision trees and averages their predictions, which significantly reduces the risk of overfitting on historical anomalies while maintaining high accuracy.
*   **Evaluation Metrics:** The model's performance is validated using `accuracy_score`, `confusion_matrix`, and comprehensive `classification_report` outputs.

### 2. Threat Severity Assessment
*   **Algorithm:** `Extra Trees (Extremely Randomized Trees) Classifier`
*   **Why Extra Trees?** Given the noisy nature of global incident reporting, Extra Trees provides high variance reduction by randomizing both the feature subset and the split thresholds. 
*   **Target Variable:** Categorical Risk Level (`Low`, `Medium`, `High`).

### 3. Temporal Frequency Forecasting
*   **Algorithm:** `Polynomial Regression`
*   **Why Polynomial?** Security incidents do not follow a strictly linear progression over time. Polynomial regression allows the model to fit non-linear curves to historical attack frequencies, providing more realistic future projections.

---

## ⚠️ Model Deployment & Storage Notice

> **Note on `.pkl` files:** 
> Pre-trained models and encoders are **not included** in this repository due to GitHub's file size constraints and best practices for ML repositories. 
> 
> **You must generate the models locally by running the training pipeline before initializing the dashboard.**

---
## 📊 Dataset Acquisition (Global Terrorism Database)

Due to GitHub's file size restrictions, the raw dataset is not included in this repository. You must download it manually before running the training pipeline.

* **1. Download the Data:** Go to Kaggle and download the [Global Terrorism Database (GTD)](https://www.kaggle.com/datasets/START-UMD/gtd).
* **2. Extract the Archive:** Unzip the downloaded folder.
* **3. Check the Filename:** Ensure the main dataset file is named `globalterrorism.csv`.
* **4. Place in Directory:** Move the `globalterrorism.csv` file directly into the `data/` folder in your project root. 

## 📂 Repository Structure

Once you have added the dataset, your full project directory should look like this before running any scripts:

```text
Predictive-Threat-Engine/
│
├── data/
│   └── globalterrorism.csv           # <-- Place the downloaded Kaggle dataset here
│
├── models/                           
│   └── (Empty - models will be generated here during training)
│
├── views/                            # Dashboard UI & inference modules
│   ├── index.py
│   ├── map_visualization.py
│   ├── predictive_engine.py
│   └── forecasting.py
│
├── scripts/
│   └── data_preprocessing.py         # Label Encoding & feature engineering
│
├── train_models.py                   # ML training pipeline script
├── main_dashboard.py                 # Main Streamlit UI script
└── requirements.txt

```
## ⚙️ How to Run the ML Pipeline

> ⚠️ **Note:** Pre-trained `.pkl` models are excluded to save space. You must generate them locally first.

* **1. Clone & Navigate:** `git clone https://github.com/yourusername/Predictive-Threat-Engine.git` then `cd Predictive-Threat-Engine`
* **2. Create Virtual Environment:** `python -m venv venv`
* **3. Activate Environment:** `venv\Scripts\activate` (Windows) OR `source venv/bin/activate` (Mac/Linux)
* **4. Install Dependencies:** `pip install -r requirements.txt`
* **5. Train the Models (Crucial):** `python train_models.py` 
* **6. Launch the Dashboard:** `streamlit run main_dashboard.py`
