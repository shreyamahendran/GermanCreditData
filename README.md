# GermanCreditData
Imperial College AI ML Course-Capstone-Project

Project Overview

This project focuses on building machine learning models to predict whether an individual will default on a loan using the German Credit Dataset from the UCI Machine Learning Repository. The dataset includes demographic, financial, and credit history features and poses a binary classification problem: • Class 0: No Default • Class 1: Default The goal is to develop a robust credit risk assessment model that can assist financial institutions in decision-making processes. After evaluating multiple models, Logistic Regression was finalized as the best-performing model, offering interpretability and strong performance.

Dataset Summary

The German Credit Dataset contains: • Instances: 1,000 • Features: 20 (both numerical and categorical) • Target Variable: Binary classification of credit risk: o 1 (Good Credit Risk) o 2 (Bad Credit Risk)

Key Features

• Numerical: Age, Duration of credit, Credit amount, Number of existing credits, etc. • Categorical: Checking account status, Employment type, Housing situation, etc.

How to use the Metadata?

The metadata provides valuable insights that will guide the preprocessing and modelling steps: Encoding Categorical Variables: We’ll need to encode categorical variables (e.g., credit_history, purpose, housing) into numerical values. For binary categorical variables (like telephone and foreign_worker), use binary encoding (0/1). For multiclass categorical variables (like status_of_existing_checking_account or credit_history), use one-hot encoding. Numerical Variables:

Scaling: Numerical features such as duration, credit_amount, and age will need to be scaled using a method like StandardScaler (to have a mean of 0 and standard deviation of 1). Cost Matrix: The cost matrix suggests that misclassifying a bad credit risk as good is more costly. This should be considered when tuning the model's parameters and during evaluation (e.g., using a weighted loss function or adjusting class weights). Feature Types: Based on the feature types (categorical and numerical), we can decide on the appropriate preprocessing steps: Categorical: One-hot encoding, label encoding, or ordinal encoding. Numerical: Scaling or normalization.

Models and Approach

Models Implemented

Logistic Regression (Finalized Model)
Random Forest
XGBoost
Optimization Technique

Bayesian Optimization was employed to fine-tune hyperparameters, ensuring efficient exploration of the search space while balancing performance and computational cost.

Future Work

Model Enhancements: o Explore ensemble approaches combining Logistic Regression with Random Forest or XGBoost. o Experiment with advanced boosting methods for potential performance gains.
Feature Engineering: o Create interaction terms or test alternate encodings to capture more complex relationships. o Perform feature selection to further refine the model.
Handle Class Imbalance: o Apply SMOTE or adjust class weights to better address minority class (defaults).
Cross-validation: o Use extensive cross-validation to validate robustness and guard against overfitting.
Summary This project demonstrates the application of machine learning to predict loan defaults using the German Credit Dataset. By evaluating multiple models and leveraging Bayesian Optimization, Logistic Regression was identified as the optimal solution. The final model balances performance and interpretability, making it well-suited for deployment in the financial sector.
