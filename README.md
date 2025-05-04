# Pump it Up: ML Model to Predict Water Pump Status in Tanzania
Machine learning model to predict the operational status of waterpoints in Tanzania. Includes data cleaning, feature engineering, EDA, and classification techniques to support infrastructure decision-making.
Pump It Up - ML Model

Predicting the functionality status of waterpoints in Tanzania using machine learning.


📌 **Objective**

Classify each water pump into one of three categories:

functional

non functional

functional needs repair


📂 **Dataset Description**

The dataset contains information on over 59,000 waterpoints, including:

Geographic location (latitude, longitude, region, district, etc.)

Technical attributes (installer, funder, construction year, water quality, etc.)

Operational information (permit status, extraction type, management type)

Target variable: status_group


## 🚰 Workflow Overview

🧹 **Data Cleaning**

Removed columns with only one value (recorded_by) or redundant information (payment_type, quantity_group, etc.).

Handled missing values using:

"Unknown" for categorical columns such as funder and installer.

Mode imputation by group for scheme_management, grouped by management.

Dropped columns that were too specific or had high cardinality (scheme_name, subvillage, wpt_name).


🧪**Feature Engineering**

Applied transformations:
Used np.log1p() on skewed numerical variables:

population

amount_tsh

gps_height

Created binary flags:

is_amount_tsh_zero

is_gps_height_zero

has_valid_coords (when longitude > 1)

has_valid_year (when construction_year >= 1960)

Grouped infrequent categories into "Rare" using tailored frequency thresholds per variable.

Reduced multicollinearity by removing raw variables like gps_height, population, and amount_tsh, while keeping only their log transformations and flags.

Tested K-Means clustering on geolocation (latitude, longitude) — did not improve the model.

Applied OptimalBinning on log_population — also did not improve results.


📊 **Modeling**

Models tested:

Decision Tree

Random Forest ✅ (best performer)

XGBoost

Tuning:
Performed hyperparameter tuning with RandomizedSearchCV (as GridSearchCV underperformed).

Removed features with very low importance (<1 %) based on cumulative feature importance.


📤 **Final Model**

RandomForestClassifier(

    max_depth=21,
    
    min_samples_leaf=2,
    
    max_features='log2',
    
    n_estimators=100,
    
    random_state=42
)

Trained on an optimized dataset (X_full_sin_dup) with only the top-performing features and no redundant columns.


📈 **Final Result**

Accuracy on validation: 0.8201

Significant improvement from previous versions (e.g., 0.7858, 0.8165, 0.8189)

Explained model predictions using LIME and multiclass ROC curves

Logged all experiments and metrics using MLflow


🧠 **Interpretability**

Integrated LIME for local explainability.

Built an interactive Gradio interface to explore feature impact on predictions.

![image](https://github.com/user-attachments/assets/5614bea5-4aca-47cc-b9a1-d50a3f049e10)


🚰 **Conclusion**

The strongest gains came from careful feature engineering — including logarithmic transformations, binary flags, rare-category grouping, and multicollinearity reduction.
Although some advanced techniques like OptimalBinning and KMeans didn’t improve performance, testing them helped validate the robustness of the final model.



---
Made with ❤️ by **Diana Tovar Reolon**.

For any questions, suggestions, or contributions, feel free to open an issue or fork this repo!

