\# 🚕 NYC Taxi Tip Generosity Prediction — Random Forest Version



\## 📌 Project Overview

This project predicts whether a taxi passenger will be a \*\*"generous tipper"\*\* (tip ≥ 20% of the fare) using the 2017 NYC Yellow Taxi Trip dataset merged with additional prediction features. It follows a complete data science workflow: data loading, target engineering, exploratory data analysis, preprocessing, feature selection, model training, and evaluation.



> ℹ️ \*\*Note\*\*: This repository contains several versions of the same project, each using a \*\*different machine learning model\*\* to solve the same classification problem. This file (`Projet\_Transversal\_Last\_Version.ipynb`) is the \*\*Random Forest\*\* version. Check the other notebooks in this repository for alternative approaches (different algorithms) applied to the exact same dataset and target.



\## 📊 Dataset

\- \*\*Source\*\*: 2017 Yellow Taxi Trip Data (NYC), merged with `nyc\_preds\_means.csv`

\- \*\*Target\*\*: `client\_genereux` (binary) — engineered from the tip amount vs. fare amount (1 if tip ≥ 20% of the fare, 0 otherwise)

\- \*\*Note\*\*: raw tip and fare columns are dropped after target creation to prevent data leakage



\## 🔍 Project Workflow



\### 1. Data Loading \& Target Engineering

\- Merge of the two source datasets

\- Column translation (English → French) for readability

\- Creation of the binary target `client\_genereux`, with removal of the source columns used to build it



\### 2. Exploratory Data Analysis (EDA)

\- Target balance check, missing values, data types overview

\- Univariate analysis: distributions of numerical and categorical features

\- Outlier detection using the IQR method

\- Correlation matrix between features and target

\- Bivariate analysis: trip distance, payment type, and deferred data vs. target



\### 3. Preprocessing

\- Outlier handling (replacing extreme values with the column mean)

\- Encoding of the remaining categorical feature (`données\_différé`)

\- Feature engineering: trip duration computed from pickup/dropoff timestamps

\- Feature selection based on Random Forest feature importances → final feature set: `type\_paie`, `montant\_total`, `duree\_trajet`, `dist\_trajet`



\### 4. Model Training \& Validation

\- \*\*Random Forest Classifier\*\*, tuned via `GridSearchCV` (number of trees, max depth, and more) with cross-validation

\- Test set preprocessed with the exact same pipeline as train (outlier handling, feature engineering, encoding, feature selection) to ensure consistency



\## 🛠️ Technologies Used

Python 3.x with Pandas, NumPy, Matplotlib, Seaborn, Scikit-learn, and Joblib.



\## 📈 Results Summary



Performance on the test set:



| Metric | Class 0 (Not Generous) | Class 1 (Generous) |

|--------|------------------------|---------------------|

| Precision | 96% | 89% |

| Recall | 89% | 96% |

| F1-Score | 92% | 93% |



\*\*Overall Accuracy: 92%\*\*



Best cross-validation score during hyperparameter tuning: \*\*92.9%\*\*



The model shows strong, well-balanced performance across both classes, with no significant bias toward either generous or non-generous tippers.



\## 🚀 How to Run

```bash

git clone https://github.com/billydassi101-ship-it/NYC-Taxi-Tip-Prediction.git

cd NYC-Taxi-Tip-Prediction

pip install -r requirements.txt

jupyter notebook "Projet\_Transversal\_Last\_Version.ipynb"

```



\## 📁 Repository Structure

```

NYC-Taxi-Tip-Prediction/

├── Projet\_Transversal\_Last\_Version.ipynb   # This notebook — Random Forest version

├── \[other notebooks]                        # Same project, different ML models

├── README.md                                # Project documentation

├── requirements.txt                         # Python dependencies

├── 2017\_Yellow\_Taxi\_Trip\_Data.csv           # Dataset (trip data)

└── nyc\_preds\_means.csv                      # Additional prediction features

```



\## 📦 Requirements

```

pandas

numpy

matplotlib

seaborn

scikit-learn

joblib

jupyter

```



\## 🤝 Contributing

Contributions, issues, and feature requests are welcome!



\## 📝 License

This project is open-source and available under the MIT License.



Made with ❤️ by Samuel DASSI



