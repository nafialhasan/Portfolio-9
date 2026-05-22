# Portfolio: Predicting Listed Used Car Prices
This repository contains my work for the Group Assignment in the Applied Predictive Analytics course (BUSA8001). The project involved competing in a Kaggle forecasting competition to predict listed prices of used cars, placing **3rd out of all competing teams**.

## Overview
The goal was to build machine learning models that accurately predict the listed price of used cars based on vehicle specifications, dealer information, and listing details. Model performance was evaluated using **Mean Absolute Percentage Error (MAPE)**.

## Contents

### Task 1: Problem Description and Initial Data Analysis
- Defined the forecasting problem and its real-world applications for buyers, dealerships, and online platforms.
- Categorised all dataset variables by type (numerical, nominal, ordinal, boolean, date).
- Identified and documented missing values across training and test datasets.
- Explored univariate data characteristics including price distribution, seller ratings, and mileage patterns.

### Task 2: Data Cleaning, Feature Engineering and Data Preparation *(my responsibility)*
- **Cleaning Numeric Features:** Extracted numeric values from mixed-format fields such as `back_legroom`, `front_legroom`, `height`, `wheelbase`, `width`, and `maximum_seating` by removing unit strings.
- **Parsing Complex Fields:** Split `power` and `torque` into four new columns (`power_hp`, `power_rpm`, `torque_value`, `torque_rpm`). Extracted `engine_layout` and `engine_cylinders` from `engine_type`, and `transmission_type` and `num_gears` from `transmission_display`.
- **Feature Engineering:** Created 10+ new features including:
  - `hp_per_litre` – performance efficiency metric
  - `vehicle_age` – derived from listing year
  - `mileage_per_year` – usage intensity indicator
  - `overall_fuel_economy` – average of city and highway fuel economy
  - `distance_from_nearest_major_city_km` – geospatial distance using `geopy` and `geonamescache`
  - VIN-derived features: `vin_country`, `vin_info`, `vin_plant_code`
  - Date features: `listed_date_day`, `listed_date_month`, `listed_date_year`
- **Missing Value Imputation:** Applied median imputation for numerical features and mode imputation for categorical features across both training and test datasets.
- **Categorical Encoding:** Mapped high-cardinality features to top-5 most frequent values + "other", then applied one-hot encoding.
- **Scaling:** Applied StandardScaler to all numeric features for model compatibility.

### Task 3: Model Training, Tuning and Kaggle Submission
- Explored relationships between key features and the target variable using scatter plots and box plots.
- Trained and hypertuned three models via `RandomizedSearchCV` with cross-validated MAPE:
  - Ridge Regression
  - Decision Tree Regressor
  - Random Forest Regressor
- Selected the optimised Random Forest as the best performing model.
- Made 54 Kaggle submissions, iterating on hyperparameter tuning, ensemble methods, and feature selection.
- **Final Result: 3rd Place** on the competition leaderboard.

## Tools and Technologies
- Python
- Pandas
- Scikit-learn
- Geopy
- Geonamescache
- RandomizedSearchCV
- Kaggle

## Contact
For any queries or further information, feel free to contact me at [nafialhasan@gmail.com](mailto:nafialhasan@gmail.com). You can also connect with me on [LinkedIn](https://www.linkedin.com/in/nafialhasan/).
