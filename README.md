# Pump it Up: ML Model to Predict Water Pump Status in Tanzania
Machine learning model to predict the operational status of waterpoints in Tanzania. Includes data cleaning, feature engineering, EDA, and classification techniques to support infrastructure decision-making.
Pump It Up - ML Model

Predicting the functionality status of waterpoints in Tanzania using machine learning.


🚀 **Project Overview**

This repository includes all the preprocessing steps, feature engineering, model training, evaluation, and interpretability analysis necessary to build a robust predictive model.

📂 **Dataset Description**

The dataset contains information on over 59,000 waterpoints, including:

Geographic location (latitude, longitude, region, district, etc.)

Technical attributes (installer, funder, construction year, water quality, etc.)

Operational information (permit status, extraction type, management type)

Target variable: status_group

## 🔁 Workflow Overview

✅ **Data Cleaning**

Removed duplicate and irrelevant columns

Imputed missing values using mode or placeholder values (e.g. "Unknown")

Grouped rare categories in high-cardinality categorical variables (funder, installer, ward) using Top-N + "Other" approach.

Converted date_recorded into an antiguedad feature measuring days since earliest record.

Binary encoded boolean variables (permit, public_meeting).

🔧 **Feature Engineering**

Log-transformed skewed numerical variables: population, amount_tsh, gps_height.

Created binary flags for potentially informative values:

is_amount_tsh_zero

is_gps_height_zero

has_valid_coords

has_valid_year

Handled construction_year anomalies and binned year quality.

Reduced dimensionality by selecting top 27 features covering 99% cumulative importance.

📊**Model Training & Evaluation**

Models Tried:

Decision Tree

Random Forest ✅ (best performer)

XGBoost

Naive Bayes

**Final Model:**

RandomForestClassifier with tuned hyperparameters:

max_depth=21

min_samples_leaf=2

max_features='log2'

n_estimators=100

Accuracy on validation set: ~0.8189

Final submission format matched DrivenData requirements (id, status_group).

📈 **Model Tuning**

Used both GridSearchCV and RandomizedSearchCV.

Optimized for accuracy with 3-fold CV.

Selected best hyperparameter combo using entire training set.

🧠 **Interpretability**

Integrated LIME for local explainability.

Built an interactive Gradio interface to explore feature impact on predictions.

![image](https://github.com/user-attachments/assets/5614bea5-4aca-47cc-b9a1-d50a3f049e10)



📤 **Submission**

Final submission file: submission_rf_tuned.csv

Prediction labels: functional, non functional, functional needs repair

📌 **Next Steps** (Suggestions)

Feature interaction modeling (e.g. polynomial features).

Try stacking or voting ensembles.

Apply Optimal Binning to continuous variables.

Explore spatial clustering with K-Means or DBSCAN.




---
Made with ❤️ by **Diana Tovar Reolon**.

For any questions, suggestions, or contributions, feel free to open an issue or fork this repo!

