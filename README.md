# 🚕 NYC Taxi Tip Generosity Prediction — Random Forest Version

## 📌 Project Overview
This project predicts whether a taxi passenger will be a **"generous tipper"** (tip ≥ 20% of the fare) using the 2017 NYC Yellow Taxi Trip dataset. It follows a complete data science workflow: target engineering, exploratory analysis, preprocessing, feature selection, model training, and evaluation.

> ℹ️ **Note**: This repository contains several versions of this project, each using a **different machine learning model** on the same dataset and target. This notebook (`Projet_Transversal_Last_Version.ipynb`) is the **Random Forest** version. Check the other notebooks in this repository for alternative algorithms.

## 📊 Dataset
- **Source**: 2017 Yellow Taxi Trip Data (NYC), merged with `nyc_preds_means.csv`
- **Target**: `client_genereux` (binary) — 1 if tip ≥ 20% of the fare, 0 otherwise
- Raw tip and fare columns are dropped after target creation to prevent data leakage

## 🔍 Project Workflow

### 1. Data Loading & Target Engineering
Merge of source datasets, column translation, and creation of the binary target.

### 2. Exploratory Data Analysis
Missing values, distributions, outlier detection (IQR method), correlation analysis, and bivariate analysis vs. target.

### 3. Preprocessing
- Outlier handling (mean replacement)
- Encoding of categorical feature (`données_différé`)
- Feature engineering: trip duration from pickup/dropoff timestamps
- Feature selection via Random Forest importances → `type_paie`, `montant_total`, `duree_trajet`, `dist_trajet`

### 4. Model Training & Validation
**Random Forest Classifier**, tuned via `GridSearchCV` with cross-validation. Test set preprocessed with the same pipeline as train.

## 🛠️ Technologies Used
Python, Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, Joblib.

## 📈 Results Summary

| Metric | Class 0 (Not Generous) | Class 1 (Generous) |
|--------|------------------------|---------------------|
| Precision | 96% | 89% |
| Recall | 89% | 96% |
| F1-Score | 92% | 93% |

**Overall Accuracy: 92%** — Best CV score: **92.9%**

## 🚀 How to Run
```bash
git clone https://github.com/billydassi101-ship-it/NYC-Taxi-Tip-Prediction.git
cd NYC-Taxi-Tip-Prediction
pip install -r requirements.txt
jupyter notebook "Projet_Transversal_Last_Version.ipynb"
```

## 📁 Repository Structure
```
NYC-Taxi-Tip-Prediction/
├── Projet_Transversal_Last_Version.ipynb   # This notebook — Random Forest version
├── [other notebooks]                        # Same project, different ML models
├── README.md
├── requirements.txt
├── 2017_Yellow_Taxi_Trip_Data.csv
└── nyc_preds_means.csv
```

## 📦 Requirements
```
pandas
numpy
matplotlib
seaborn
scikit-learn
joblib
jupyter
```

## 🤝 Contributing
Contributions, issues, and feature requests are welcome!

## 📝 License
This project is open-source and available under the MIT License.

Made with ❤️ by Samuel DASSI
