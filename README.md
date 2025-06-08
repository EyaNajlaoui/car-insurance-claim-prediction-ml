# car-insurance-claim-prediction-ml

## Car Insurance Claim Prediction
A machine learning project to predict whether a policyholder will file an insurance claim based on their profile and vehicle characteristics, with encoding applied according to Binary Features, Ordinal Features, and Nominal Features.

### 📊 Project Overview
This project tackles the challenge of predicting insurance claims using machine learning techniques. The main focus is on handling class imbalance and optimizing model performance for the minority class (claim predictions).

### 🔍 Dataset Analysis & Visualization
#### Key Insights from Exploratory Data Analysis:
- **Demographic Patterns:**
  - **Income Impact:** Explored income distribution patterns between claim filers and non-filers.
- **Vehicle Characteristics:**
  - **Vehicle Age:** Investigated claim frequency across different car ages.
  - **Vehicle Age Groups:** Created age bins (0-3, 4-5, 6-10, 11-20, 20+ years) to better understand patterns.
  - **Vehicle Type:** Analyzed claim rates by car type, ranking from highest to lowest claim probability.
- **Risk Factors:**
  - **Driving Record:** Examined Motor Vehicle Record (MVR) points distribution.
  - **License History:** Analyzed claim probability for drivers with revoked licenses.
  - **Location:** Compared urban vs rural claim distributions.
- **Claim Amount Analysis:**
  - Distribution of actual claim amounts.
  - Statistical measures including mean and median claim values.

### 🛠️ Data Preprocessing
#### Data Cleaning:
- Removed duplicate entries from the dataset.
- Handled missing values for: AGE, YOJ (Years on Job), INCOME, HOME_VAL,CAR_AGE and OCCUPATION.
- Converted monetary variables (INCOME, HOME_VAL, BLUEBOOK) to numeric format by removing $ and comma symbols.

#### Feature Engineering:
- **Column Removal:** Dropped OLDCLAIM, CLM_AMT, CLAIM_RATIO, HOME_VAL_IMPUTED to prevent data leakage.
- **Encoding:** Applied appropriate encoding techniques for categorical variables according to Binary Features, Ordinal Features, and Nominal Features.
- **Feature Selection:** Separated numerical and categorical encoded features for model training.

### ⚖️ Class Imbalance Challenge
The dataset exhibited a significant class imbalance, leading to poor performance of the initial models, potentially due to underfitting or overfitting. This issue was addressed through multiple resampling strategies.

### 🤖 Machine Learning Approaches
#### Models Tested:
- Random Forest Classifier
- XGBoost Classifier

#### Class Imbalance Solutions:
Implemented and compared 4 different approaches:
- **Class Weights:** Balanced class weights.
- **SMOTE:** Synthetic Minority Oversampling Technique.
- **Random Undersampling:** Reducing majority class samples.
- **Hybrid Approach:** SMOTE + Undersampling combination.

#### Optimization Strategy:
- **Primary Goal:** Achieve 70%+ precision for the minority class (claim prediction).
- **Threshold Optimization:** Fine-tuned decision thresholds to maximize F1-score while maintaining precision requirements.
- **Cross-Validation:** Used 5-fold cross-validation for robust model evaluation.

### 📈 Model Performance
#### Best Performing Model: XGBoost with Hybrid Sampling
- **Sampling Strategy:** SMOTE (60% oversampling) + Random Undersampling (100% ratio).
- **Key Hyperparameters:**
  - `n_estimators:` 400
  - `max_depth:` 4
  - `learning_rate:` 0.03
  - `scale_pos_weight:` 2.5

#### Evaluation Metrics:
- **Classification Report:** Precision, Recall, F1-score for both classes.
- **ROC AUC Score:** Area under the ROC curve.
- **PR AUC Score:** Precision-Recall area under curve.
- **Confusion Matrix:** Visual representation of prediction accuracy.

### 🎯 Key Results
- Successfully addressed the class imbalance problem.
- Achieved target precision of 70% for claim prediction.
- Achieved target precision of 80%+ for no claim prediction.
- Identified most important features for claim prediction.
- Provided actionable insights for insurance risk assessment.
