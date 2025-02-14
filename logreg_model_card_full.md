
# Logistic Regression Model Card

## Model Overview
- **Model Type**: Logistic Regression (LogReg)
- **Objective**: Predict whether an individual will default on a loan. The target variable is binary, where:
  - **Class 0**: No Default
  - **Class 1**: Default
- **Training Data**: The model was trained on the **German Credit Dataset** from the UCI Machine Learning Repository.
- **Features**:
  - **Numerical Features**: Age, Duration of credit, Credit amount, Number of existing credits, etc.
  - **Categorical Features**: Checking account status, Employment type, Housing situation, etc.
  - **All features**: 'checking_account', 'duration', 'history', 'purpose', 'credit_amount', 'savings_account', 'employment',
    'location', 'personal_status', 'other_parties', 'residence_since', 'property_magnitude', 'age', 'other_payment_plans',
    'housing', 'existing_credits', 'job', 'num_dependents', 'own_telephone', 'foreign_worker'
- **Target Variable**:  'class' Binary classification of whether a person defaults (1) or not (0).


## Final Model Parameters
The final model was tuned using **GridSearchCV** to find the best hyperparameters. The best combination found during the grid search was:

- **C (Regularization strength)**: 100 (A higher value of C means less regularization, allowing the model to fit the training data more closely)
- **Penalty**: 'l1' ('L1' regularization encourages sparsity, meaning it can drive some coefficients to zero, which can lead to a simpler model with fewer features.)
- **Solver**: 'saga' ('SAGA' is suitable for large datasets and can handle L1 regularization effectively.)
- **Max_iter**: 100 (Maximum number of iterations for the solver)

## Model Performance

### Evaluation Metrics (Test Set)
After applying a threshold of 0.4, the model's performance metrics were as follows:

- **Accuracy**: 79.00% (With adjusted threshold)
- **Precision**:
  - **Class 0 (No Default)**: 0.87
  - **Class 1 (Default)**: 0.63
- **Recall**:
  - **Class 0 (No Default)**: 0.82
  - **Class 1 (Default)**: 0.71
- **F1-Score**:
  - **Class 0 (No Default)**: 0.85
  - **Class 1 (Default)**: 0.67
- **ROC AUC**: 0.82

### Confusion Matrix (Threshold: 0.4)
[[116 25] [ 17 42]]


### Threshold Adjustment:
- **Decision Threshold**: 0.4 (Lowered from the default of 0.5 to increase recall for the Default class)
- The threshold adjustment was made to prioritize the detection of more **default cases (Class 1)**, which is often more critical in risk assessment scenarios like credit scoring. However, this change comes at the cost of reduced precision for Class 1 (Default), as we are now classifying more instances as Default.

## Intended Use
This model is designed for **credit risk assessment**, specifically to predict the likelihood of a customer defaulting on a loan. By using this model, banks or financial institutions can assess the risk level of granting loans to customers and take appropriate actions such as setting credit limits, offering tailored loan terms, or declining loan applications based on predicted risk.

### Important Considerations:
- **Imbalanced Data**: The dataset has an imbalance in the classes, with more non-defaults (Class 0) than defaults (Class 1). This imbalance may affect the model's performance, particularly with precision and recall for Class 1 (Default).
- **Threshold Tuning**: As observed, adjusting the decision threshold has a direct impact on the precision and recall balance. A threshold of 0.4 prioritizes recall for Class 1, reducing false negatives but increasing false positives.
- **Model Interpretability**: Logistic Regression is interpretable, meaning it can provide insights into which features contribute the most to predicting defaults, making it easier to explain decisions to stakeholders.

## Limitations
- **Bias in the Data**: The performance of the model is heavily reliant on the quality and representativeness of the data. If the training data is biased or not representative of the real-world distribution of credit applicants, the model may fail to generalize well.
- **Imbalanced Data**: As mentioned earlier, the class imbalance could impact the model's ability to accurately predict the minority class (defaults).
- **Interpretability**: While Logistic Regression is interpretable, its simplicity may limit its ability to capture more complex patterns present in the data. Alternative models like Random Forest or XGBoost might perform better in such cases.

## Future Work
- **Model Enhancement**: 
  - Explore alternative models such as **Random Forest**, **XGBoost**, or **Gradient Boosting** to see if they can capture more complex patterns in the data.
  - Experiment with ensemble methods, such as combining Logistic Regression with Random Forest or boosting models to improve overall performance.
- **Feature Engineering**: 
  - Create additional features (e.g., interaction terms) to enhance model performance.
  - Evaluate the impact of adding new features or reducing features through feature selection.
- **Cross-validation**: Use **cross-validation** to validate model performance and ensure robustness against overfitting.

## Recommendations
- **Threshold Selection**: In situations where the goal is to minimize the number of defaults overlooked (false negatives), adjusting the threshold to 0.4 can be beneficial, as it increases recall for Class 1 (Default). However, it's important to balance this with the precision of Class 0 (No Default), as a lower threshold increases false positives.
- **Consider Rebalancing**: Since the dataset is imbalanced, you may want to try resampling techniques (e.g., SMOTE) or use model-based approaches like **balanced class weights** to address the imbalance and improve the model's performance on the minority class.
- **Regular Monitoring and Updates**: The model should be regularly monitored and updated with new data to ensure it stays relevant and accurate over time. It's also important to retrain the model periodically with fresh data to avoid drift.

## Model Deployment
The final model can be deployed into a production environment for real-time credit scoring. However, it is essential to continuously evaluate its performance and update it with new data to ensure it maintains its predictive accuracy.

### Deployment Considerations:
- **Real-Time Inference**: The model can be used in a web service that takes new customer information as input and returns the predicted likelihood of default.
- **Model Drift**: Over time, the distribution of the features in the incoming data may change. Continuous monitoring of the model's performance is essential to detect any drift in predictions.

## Authors
- **Developed by**: [Chirayu_Kushalkar]
- **Date**: [20th November 2024]
