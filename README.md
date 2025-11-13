# MachinelEARNING
"🚰 Pump it Up: Data Mining the Water Table
📄 Project Overview
This repository contains a machine learning solution for the "Pump it Up: Data Mining the Water Table" competition hosted by DrivenData.

The goal of this project is to predict the operating condition of water points in Tanzania. Using data from the Tanzanian Ministry of Water, the model predicts which pumps are functional, which need repairs, and which are non-functional. This classification task helps improve the maintenance operations and access to clean water across the country.

🎯 The Objective
This is a ternary classification problem where the target variable, status_group, has three classes:

functional: The water point is operational and there are no repairs needed.

non functional: The water point is not operational.

functional needs repair: The water point is operational but needs maintenance.

🛠️ Methodology & Architecture
The solution is built using Python and Scikit-Learn, utilizing a robust Pipeline architecture to ensure reproducibility and prevent data leakage during cross-validation.

1. Feature Engineering
A custom FeatureEngineer class was implemented to transform raw data into meaningful predictors:

Temporal Features: Extracted recorded_year and recorded_month to capture seasonal or temporal trends.

Derived Features: Calculated pump_age (Recorded Year - Construction Year) to quantify wear and tear.

Data Cleaning: Handled outliers (e.g., negative ages) and dropped high-cardinality or redundant features (e.g., wpt_name, num_private) to reduce noise.

2. Preprocessing Pipeline
The data processing flow handles mixed data types automatically:

Numerical Data: Missing values are imputed using the Median strategy, followed by Standard Scaling.

Categorical Data: Missing values are filled with a constant placeholder, followed by Ordinal Encoding (handling unknown categories robustly).

Type Safety: Explicit conversion of object/boolean columns to strings to prevent mixed-type errors during encoding.

3. Model Selection
The core classifier used is a Random Forest Classifier.

Why Random Forest? It effectively handles the non-linear relationships in the data, is robust against overfitting, and performs well with a mix of numerical and categorical features without requiring strict normalization (though scaling was applied for best practices).

4. Hyperparameter Tuning
Instead of static parameters, the model uses RandomizedSearchCV with Stratified K-Fold Cross-Validation (3 splits). This optimizes the n_estimators and max_depth parameters while maintaining the class distribution across folds, optimizing for the F1 Macro score.

📊 Results
Metric: F1 Score (Macro)

Validation Score: ~0.68 (based on local CV)

Model Output: Generates a submission.csv file ready for the DrivenData leaderboard.

📂 Repository Structure
notebooks/: Contains the Jupyter Notebook with the full analysis and pipeline.

data/: (Gitignored) Folder for training and test datasets.

submission.csv: The final predictions file.

🚀 How to Run
Clone the repository.

Install dependencies:

Bash

pip install pandas numpy scikit-learn matplotlib seaborn
Place the competition datasets (TRAINING_SET_VALUES.csv, TRAINING_SET_LABELS.csv, TEST_VALUES.csv) in the root or data folder.

Run the notebook to train the model and generate predictions.

Author: Luis Rodrigo Del Rincon"
