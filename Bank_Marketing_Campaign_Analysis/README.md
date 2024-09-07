# Portuguese Bank Marketing Campaign Analysis

## Business Understanding
The goal of this analysis was to predict whether a client would subscribe to a term deposit based on data collected from a Portuguese bank's marketing campaigns. The data consists of personal, financial, and campaign-related features, which are used to model and predict customer behavior. The aim is to improve the bank’s marketing strategy by understanding key factors influencing customer decisions, thus optimizing future campaigns.

## Data Understanding & Preparation
**Data Description:** The dataset contains information from multiple telemarketing campaigns, including features such as age, job, education, duration of the call, and other personal and campaign-specific attributes.

**Cleaning & Transformation:** 
- No cleaning was required as none was needed.
- Categorical variables were handled through one-hot encoding.
- Numerical variables were standardized to ensure better model performance.

## Modeling Approach
We implemented four different classification models to predict customer subscriptions:

1. **Logistic Regression**
2. **K-Nearest Neighbors (KNN)**
3. **Decision Tree**
4. **Support Vector Machine (SVM)**

Each model was trained and evaluated on the cleaned dataset, and hyperparameter tuning was performed (especially for KNN and Decision Tree) to optimize their performance.

### Model Comparison and Performance (No Tuning Parameters)

| Model                  | Train Time (s) | Train Accuracy | Test Accuracy |
|------------------------|----------------|----------------|---------------|
| Logistic Regression     | 0.2467         | 0.9119         | 0.9114        |
| K-Nearest Neighbors     | 0.0157         | 0.9286         | 0.9030        |
| Decision Tree           | 0.1822         | 1.0000         | 0.8866        |
| Support Vector Machine  | 12.6516        | 0.9217         | 0.9111        |

### Interpretation of the Findings:
- **Logistic Regression** and **SVM** are the best-performing models, with strong generalization and consistent accuracy on both training and test data.
- **SVM** performs excellently but has a significantly longer training time (12.65 seconds), making it the slowest model.
- **Logistic Regression** offers similar accuracy with much faster training time (0.25 seconds).
- **KNN** is the fastest to train but has a slight drop in test accuracy.
- **Decision Tree** overfits the training data, with 100% accuracy but a drop in test accuracy (88.66%).

## Model Performance Improvement Efforts

### 1. Feature Selection: Logistic Regression
We attempted to remove irrelevant features based on feature importance values. Despite this effort, there was minimal improvement.

- **Accuracy:** 0.9097
- **Precision:** 0.6702
- **Recall:** 0.4021
- **F1-Score:** 0.5027

**Observation:** Removing less relevant features did not lead to significant performance improvements. Recall remained low, indicating difficulty in identifying true positives.

### 2. Hyperparameter Tuning: K-Nearest Neighbors (KNN)
We improved the KNN model by adjusting the number of neighbors. The best result was achieved with 19 neighbors.

- **Best KNN Parameters:** `{'n_neighbors': 19}`
- **Best Cross-Validated Accuracy:** 0.9106
- **Tuned KNN Test Accuracy:** 0.9088

**Comparison with Pre-Tuning:**
- Pre-Tuning Test Accuracy: 0.9030
- Post-Tuning Test Accuracy: 0.9088

**Observation:** Tuning led to a slight improvement in test accuracy. KNN remains competitive, though overall improvement is modest.

### 3. Hyperparameter Tuning: Decision Tree
We optimized parameters such as the criterion, max depth, min samples split, and min samples leaf.

- **Best Decision Tree Parameters:** `{'criterion': 'gini', 'max_depth': 5, 'min_samples_leaf': 3, 'min_samples_split': 2}`
- **Best Cross-Validated Accuracy:** 0.9131
- **Tuned Decision Tree Test Accuracy:** 0.9148

**Comparison with Pre-Tuning:**
- Pre-Tuning Test Accuracy: 0.8866
- Post-Tuning Test Accuracy: 0.9148

**Observation:** Hyperparameter tuning significantly improved the Decision Tree's test accuracy, making it more generalizable and competitive.

## Summary of Efforts

- **Feature Selection for Logistic Regression:** Minimal improvement observed, with accuracy around 90.97% and recall particularly low at 40.21%.
- **Hyperparameter Tuning for KNN:** Improved test accuracy slightly from 90.30% to 90.88%.
- **Hyperparameter Tuning for Decision Tree:** Significant improvement in test accuracy from 88.66% to 91.48%.

## Findings and Insights

### Key Predictors:
- **Duration**, **age**, **nr.employed**, and **euribor3m** were the most impactful features on customer behavior.
- Less relevant features (e.g., day of the week) were removed, but minimal performance improvements were observed for Logistic Regression.

### Actionable Insights:
- **Call Duration:** Longer calls significantly increase the likelihood of subscription, suggesting that meaningful conversations positively influence customer decisions.
- **Economic Indicators:** Features like nr.employed and euribor3m reflect broader market conditions that affect customer behavior, highlighting the importance of economic factors in decision-making.

## Recommendations and Next Steps

- **Targeted Marketing:** Focus on customers who engage in longer conversations as they have a higher likelihood of subscribing. Tailor interactions based on age, employment status, and financial indicators.
- **Refining Campaigns:** Optimize future marketing campaigns by tailoring strategies to individuals more likely to respond positively, using attributes like job type, education level, and financial standing to improve conversion rates and customer engagement.
