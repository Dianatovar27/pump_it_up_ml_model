# pump_it_up_ml_model
Machine learning model to predict the operational status of waterpoints in Tanzania. Includes data cleaning, feature engineering, EDA, and classification techniques to support infrastructure decision-making.
Pump It Up - ML Model

Predicting the functionality status of waterpoints in Tanzania using machine learning.

📌 Project Overview

This project addresses the challenge of identifying which waterpoints in Tanzania are functional, non-functional, or in need of repair. The model is built using historical data and aims to support better decision-making in infrastructure maintenance.

📂 Dataset Description

The dataset contains information on over 59,000 waterpoints, including:

Geographic location (latitude, longitude, region, district, etc.)

Technical attributes (installer, funder, construction year, water quality, etc.)

Operational information (permit status, extraction type, management type)

Target variable: status_group

✅ Workflow

1. Data Cleaning

Removed duplicate and irrelevant columns

Imputed missing values using mode or placeholder values (e.g. "Unknown")

Simplified high-cardinality categorical variables using Top N + "Other"

2. Feature Engineering (in progress)

Creating derived features like antiguedad, has_valid_coords, log_population

Handling outliers in gps_height, amount_tsh, and population

Transforming construction_year to improve model interpretability

3. Exploratory Data Analysis (EDA)

Visualized distributions and correlations

Explored class imbalance in status_group

Boxplots and countplots to identify potential data issues

4. Modeling (upcoming)

Will use classification models such as:

Random Forest

Decision Tree

XGBoost

Will evaluate using metrics: Accuracy, F1-Score, Confusion Matrix

📊 Example Visuals

(to be added)

Status group by quantity

Boxplots for population and gps_height

Countplots for categorical distributions

📁 Files Structure

├── data/                 # Raw and cleaned datasets

├── notebooks/            # Jupyter notebooks (EDA, modeling, feature engineering)

├── scripts/              # Python scripts for preprocessing and training

├── visuals/              # Graphs and plots for presentation

└── README.md             # Project summary and guide


🚀 Goal

To build a robust, interpretable model that helps prioritize which waterpoints need maintenance or replacement, ultimately improving access to clean water.

📌 Status

Still in progress. Currently wrapping up feature engineering phase before model selection and tuning.

Stay tuned!

👩🏽‍💻 Author

DIANA TOVAR REOLON
