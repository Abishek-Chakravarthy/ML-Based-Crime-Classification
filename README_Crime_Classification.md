# 📊 Crime Classification using Machine Learning

This project involves predicting the category of crime incidents using a real-world dataset. The dataset includes various features such as time, location, demographic attributes of the victim, and details about the incident. Through extensive preprocessing, feature engineering, and model evaluation, this project aims to build an accurate classifier capable of categorizing crimes effectively.

## 📁 Project Structure

```
crime-classification/
├── data/
│   ├── train.csv
│   └── test.csv
├── notebooks/
│   └── crime_classification_analysis.ipynb
├── models/
│   └── trained_model.pkl
├── submissions/
│   └── submission.csv
├── requirements.txt
└── README.md
```

## 📌 Problem Statement

Given a dataset of historical crime incidents with attributes such as date, time, location, weapon used, and victim details, the task is to classify the type of crime committed. The crime categories include:

- Property Crimes  
- Violent Crimes  
- Crimes Against Public Order  
- Fraud and White-Collar Crimes  
- Crimes Against Persons  
- Other Crimes

## 🧾 Dataset Description

The dataset contains 20,000 training entries and 5,000 test entries with 22 columns in the train set and 21 in the test set.

### Key Features:

- `Latitude`, `Longitude` – Geolocation of the crime  
- `Time_Occurred`, `Date_Occurred` – Time and date of the incident  
- `Area_ID`, `Reporting_District_no` – Identifiers of crime jurisdiction  
- `Victim_Age`, `Victim_Sex`, `Victim_Descent` – Demographics  
- `Weapon_Used_Code`, `Modus_Operandi` – Crime method details  
- `Premise_Code` – Type of place where crime occurred  
- `Crime_Category` – **Target variable (Train set only)**

## 🔍 Exploratory Data Analysis (EDA)

- Missing values in several columns like `Weapon_Used_Code`, `Modus_Operandi`, `Cross_Street`
- Geolocation columns (`Latitude`, `Longitude`) had anomalies (e.g., 0 values)
- Target class imbalance observed; handled using `StratifiedShuffleSplit`
- Correlation insights showed high redundancy in columns like `Area_ID` and `Reporting_District_no`

## ⚙️ Data Preprocessing

- Imputation of missing values using KNNImputer and SimpleImputer
- Encoding categorical variables using Label Encoding
- Feature extraction from datetime columns (Day, Month, Hour, etc.)
- Outlier handling for age and time columns
- Dropped redundant columns: `Area_Name`, `Weapon_Description`, `Status_Description`, etc.

## 🧠 Models Implemented

| Model                   | Accuracy |
|------------------------|----------|
| Logistic Regression     | 93.6%    |
| Random Forest           | 95.2%    |
| K-Nearest Neighbors     | 89.0%    |
| Support Vector Machine  | 93.4%    |
| Bagging Classifier      | 95.3%    |
| Gradient Boosting       | 95.1%    |
| XGBoost                 | 95.3%    |
| LightGBM                | **95.5%** 🔥

- Feature selection using **RFECV**
- Hyperparameter tuning via **GridSearchCV** and **RandomizedSearchCV**

## 🏆 Best Model

**LightGBM** outperformed other models with the highest accuracy (95.5%) and excellent class-wise precision and recall. Final predictions were generated and saved in `submission.csv`.

## 📈 Evaluation Metrics

- **Accuracy**  
- **Precision, Recall, F1-Score** (macro and weighted)  
- **Confusion Matrix**  
- Addressed class imbalance through proper stratification

## 📤 Output

Final predictions on test data:
```
submission.csv
┌─────┬────────────────────┐
│ ID  │ Crime_Category     │
├─────┼────────────────────┤
│ 1   │ Property Crimes    │
│ 2   │ Violent Crimes     │
│ ... │ ...                │
└─────┴────────────────────┘
```

## 💻 Tech Stack

- Python (Pandas, NumPy, Matplotlib, Seaborn)
- Scikit-learn
- XGBoost, LightGBM
- Jupyter Notebooks
- Kaggle environment for training

## 🚧 Future Improvements

- Implement deep learning models (e.g., RNNs with time-based data)
- Use geospatial analysis for clustering crimes
- Integrate with real-time crime feeds for live predictions
- Deploy the model via a web interface or REST API

## 📜 License

This project is licensed under the MIT License.
