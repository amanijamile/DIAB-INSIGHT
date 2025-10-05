# DIAB-INSIGHT
An ensemble learning-based system for early diabetes prediction using clinical data and feature importance analysis.

🩺 DIAB-INSIGHT: Ensemble Learning for Early Diabetes Prediction
📘 Overview

DIAB-INSIGHT is a machine learning project designed to predict diabetes using clinical and demographic data from NHANES 2017–March 2020.
It applies advanced ensemble learning techniques to improve early detection and interpret key biomarkers associated with diabetes.

📊 NHANES Dataset

The dataset was obtained from the National Health and Nutrition Examination Survey (NHANES) and spans 2017–March 2020.
Since NHANES data comes in multiple .XPT files, they were downloaded, merged, and preprocessed to form a single dataset named merged_data.csv.

NHANES Files Used

P_ALQ.xpt – Alcohol Questionnaire

P_BMX.xpt – Body Measures (height, weight, BMI, waist circumference)

P_BPXO.xpt – Blood Pressure & Oximetry

P_DEMO.xpt – Demographics (age, gender, race, income, etc.)

P_DIQ.xpt – Diabetes Questionnaire

P_DR1TOT.xpt – Dietary Interview (Day 1)

P_DR2TOT.xpt – Dietary Interview (Day 2)

P_GLU.xpt – Glucose Laboratory Data

P_HDL.xpt – HDL Cholesterol

P_MCQ.xpt – Medical Conditions Questionnaire

P_PAQ.xpt – Physical Activity Questionnaire

P_SMQ.xpt – Smoking Questionnaire

P_TRIGLY.xpt – Triglycerides Laboratory Data

🧩 Data Preparation
1️⃣ Merging NHANES Files

Run the script mergednhanes.py to combine the downloaded .XPT files into one dataset:

python mergednhanes.py


This script:

Reads all uploaded NHANES .xpt files

Merges them on the participant ID (SEQN)

Removes duplicates and standardizes column names

Produces the final merged_data.csv file

2️⃣ Preprocessing & Feature Engineering

The diab_insgith.py script handles:

Removing columns with >50% missing data

Median imputation for missing numeric values

Standardization of continuous variables

One-hot encoding for categorical variables

Feature selection using Recursive Feature Elimination (RFE)

Handling class imbalance with SMOTE (since only ~9.8% of participants were diabetic)

🧠 Model Training

After preprocessing, the script:

Trains individual models:

Random Forest

AdaBoost

XGBoost

Builds and evaluates Voting and Stacking Ensemble models

Tunes model thresholds for better recall on diabetic cases

Saves all trained models as .pkl files

To run the training pipeline:

python diab_insgith.py

💾 Output Files

After training, the following files will be generated:

merged_data.csv
best_rf.pkl
best_ada.pkl
best_xgb.pkl
calibrated_rf.pkl
calibrated_ada.pkl
voting_clf.pkl

📈 Evaluation Metrics

Each model is evaluated using:

Accuracy

Precision

Recall

F1-score

Confusion Matrix

Optimized thresholds (0.467 for Voting, 0.25 for Stacking) significantly improved diabetic recall while keeping false positives low.

☁️ Environment

All experiments were conducted in Google Colab Pro with GPU acceleration for efficient model training and tuning.
