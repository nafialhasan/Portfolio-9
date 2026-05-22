{
 "cells": [
  {
   "cell_type": "markdown",
   "id": "83ca6a07-5a15-455a-98d0-5bfdefd75394",
   "metadata": {},
   "source": [
    "# Portfolio: Predicting Listed Used Car Prices\r\n",
    "This repository contains my work for the Group Assignment in the Applied Predictive Analytics course (BUSA8001). The project involved competing in a Kaggle forecasting competition to predict listed prices of used cars, placing **3rd out of all competing teams**.\r\n",
    "\r\n",
    "## Overview\r\n",
    "The goal was to build machine learning models that accurately predict the listed price of used cars based on vehicle specifications, dealer information, and listing details. Model performance was evaluated using **Mean Absolute Percentage Error (MAPE)**.\r\n",
    "\r\n",
    "## Contents\r\n",
    "\r\n",
    "### Task 1: Problem Description and Initial Data Analysis\r\n",
    "- Defined the forecasting problem and its real-world applications for buyers, dealerships, and online platforms.\r\n",
    "- Categorised all dataset variables by type (numerical, nominal, ordinal, boolean, date).\r\n",
    "- Identified and documented missing values across training and test datasets.\r\n",
    "- Explored univariate data characteristics including price distribution, seller ratings, and mileage patterns.\r\n",
    "\r\n",
    "### Task 2: Data Cleaning, Feature Engineering and Data Preparation *(my responsibility)*\r\n",
    "- **Cleaning Numeric Features:** Extracted numeric values from mixed-format fields such as `back_legroom`, `front_legroom`, `height`, `wheelbase`, `width`, and `maximum_seating` by removing unit strings.\r\n",
    "- **Parsing Complex Fields:** Split `power` and `torque` into four new columns (`power_hp`, `power_rpm`, `torque_value`, `torque_rpm`). Extracted `engine_layout` and `engine_cylinders` from `engine_type`, and `transmission_type` and `num_gears` from `transmission_display`.\r\n",
    "- **Feature Engineering:** Created 10+ new features including:\r\n",
    "  - `hp_per_litre` – performance efficiency metric\r\n",
    "  - `vehicle_age` – derived from listing year\r\n",
    "  - `mileage_per_year` – usage intensity indicator\r\n",
    "  - `overall_fuel_economy` – average of city and highway fuel economy\r\n",
    "  - `distance_from_nearest_major_city_km` – geospatial distance using `geopy` and `geonamescache`\r\n",
    "  - VIN-derived features: `vin_country`, `vin_info`, `vin_plant_code`\r\n",
    "  - Date features: `listed_date_day`, `listed_date_month`, `listed_date_year`\r\n",
    "- **Missing Value Imputation:** Applied median imputation for numerical features and mode imputation for categorical features across both training and test datasets.\r\n",
    "- **Categorical Encoding:** Mapped high-cardinality features to top-5 most frequent values + \"other\", then applied one-hot encoding.\r\n",
    "- **Scaling:** Applied StandardScaler to all numeric features for model compatibility.\r\n",
    "\r\n",
    "### Task 3: Model Training, Tuning and Kaggle Submission\r\n",
    "- Explored relationships between key features and the target variable using scatter plots and box plots.\r\n",
    "- Trained and hypertuned three models via `RandomizedSearchCV` with cross-validated MAPE:\r\n",
    "  - Ridge Regression\r\n",
    "  - Decision Tree Regressor\r\n",
    "  - Random Forest Regressor\r\n",
    "- Selected the optimised Random Forest as the best performing model.\r\n",
    "- Made 54 Kaggle submissions, iterating on hyperparameter tuning, ensemble methods, and feature selection.\r\n",
    "- **Final Result: 3rd Place** on the competition leaderboard.\r\n",
    "\r\n",
    "## Tools and Technologies\r\n",
    "- Python\r\n",
    "- Pandas\r\n",
    "- Scikit-learn\r\n",
    "- Geopy\r\n",
    "- Geonamescache\r\n",
    "- RandomizedSearchCV\r\n",
    "- Kaggle\r\n",
    "\r\n",
    "## Contact\r\n",
    "For any queries or further information, feel free to contact me at [nafialhasan@gmail.com](mailto:nafialhasan@gmail.com). You can also connect with me on [LinkedIn](https://www.linkedin.com/in/nafialhasan/)."
   ]
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.11.7"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 5
}
