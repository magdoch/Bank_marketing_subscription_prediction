### Information
The data is related to direct marketing campaign direct marketing campaigns of a Portuguese banking institution. The marketing campaigns were based on phone calls. Often, more than one contact to the same client was required, in order to access if the product (bank term deposit) would be ('yes') or not ('no') subscribed.
bank-additional-full.csv with all examples (41188) and 20 inputs, ordered by date (from May 2008 to November 2010), very close to the data analyzed in [Moro et al., 2014]
The smallest datasets are provided to test more computationally demanding machine learning algorithms (e.g., SVM). 

### Main Task

The task is to build a model to predict whether a customer will open a term deposit at a bank. We encounter similar tasks in various companies and domains when we want to understand whether a customer will buy a certain product, use our service/website next month, or purchase a subscription.
Therefore, it is not enough to simply build a model; we must also explain how this model works and why it produces these specific results. Without this understanding, the client will not be able to proceed to deploying the model in production.

The classification goal is to predict if the client will subscribe a term deposit (variable y).

For this task, I am using a dataset that was originally published on the [UCI Machine Learning Repository] website; however, since that site provides an inaccurate description of the data and contains many different subsets, I decided to use the dataset from Kaggle: https://www.kaggle.com/datasets/sahistapatel96/bankadditionalfullcsv.

## 📊 Results

A comparison of the performance of different machine learning models based on key evaluation metrics.
## 📊 Model Comparison

| 🤖 Model                      | 📈 Train ROC-AUC | 📉 Test ROC-AUC | 🔁 Train F1 | 🔁 Test F1 | 🎯 Train Recall | 🎯 Test Recall | 🎯 Train Precision | 🎯 Test Precision | ⚠️ Overfitting |
|-----------------------------|------------------|-----------------|-------------|------------|----------------|----------------|-------------------|------------------|----------------|
| XGBoost                     | 0.84             | 0.81            | 0.43        | 0.38       | 0.31           | 0.27           | 0.76              | 0.68             | 0.03           |
| Logistic Regression         | 0.79             | 0.80            | 0.45        | 0.47       | 0.62           | 0.65           | 0.35              | 0.36             | -0.01          |
| Decision Tree               | 0.84             | 0.77            | 0.51        | 0.48       | 0.66           | 0.61           | 0.42              | 0.40             | 0.06           |
| kNN                         | 0.93             | 0.74            | 0.49        | 0.38       | 0.38           | 0.29           | 0.70              | 0.56             | 0.18           |
| Logistic Regression (Tuned) | 0.79             | 0.80            | 0.45        | 0.47       | 0.63           | 0.65           | 0.35              | 0.36             | -0.01          |
| XGBoost (RandomizedSearch)  | 0.82             | 0.81            | 0.47        | 0.49       | 0.65           | 0.66           | 0.37              | 0.39             | 0.01           |
| XGBoost (Hyperopt)          | 0.81             | 0.81            | 0.46        | 0.47       | 0.64           | 0.66           | 0.36              | 0.37             | 0.00           |



##  Key Insights

-  XGBoost (tuned) achieved the best overall ROC-AUC and balanced performance.
-  Logistic Regression showed stable results and good generalization.
-  kNN suffers from strong overfitting and is not recommended.
-  Decision Tree shows moderate performance with slight overfitting.
-  Hyperparameter tuning improved XGBoost performance and stability.
## CONCLUSION
In this project, a full machine learning pipeline for binary classification was developed, including exploratory data analysis, feature engineering, model training, evaluation, and interpretation.

The exploratory data analysis revealed several important patterns. Customer behavior is strongly influenced by both individual characteristics and external economic conditions. Features such as previous campaign outcome, number of contacts, and macroeconomic indicators showed a clear relationship with the target variable.

Several machine learning models were trained and evaluated, including Logistic Regression, k-Nearest Neighbors, Decision Tree, and XGBoost. Among them, XGBoost demonstrated the best performance in terms of ROC-AUC, while Logistic Regression provided more interpretable results.

Hyperparameter tuning using Randomized Search and Bayesian Optimization (Hyperopt) further improved the performance of the boosting model. Both approaches produced similar results, confirming the robustness of the solution.

Feature importance and SHAP analysis showed that macroeconomic variables (such as nr.employed, emp.var.rate, and euribor3m) have the strongest impact on predictions. Additionally, customer interaction features, such as previous campaign success and number of contacts, also play a significant role. 

Error analysis revealed that the model struggles with borderline cases, particularly when there is limited historical information about the customer. It was also observed that excessive contact may negatively affect predictions, indicating potential customer fatigue.


Overall, the developed model provides a reliable and interpretable solution for predicting customer subscription behavior and can be effectively used in real-world applications.

