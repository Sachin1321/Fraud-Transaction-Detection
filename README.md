# Fraud-Transaction-Detection
This is a Fraud Transaction Detection project. The fraud detection model described in the code is a machine learning pipeline designed to identify fraudulent activities in sales call data. Here’s a detailed overview of your project, including key steps, methodologies, findings, and evaluations:

Project Overview <br>
* Objective: To build predictive models for detecting fraudulent transactions using a dataset containing transaction details, including attributes such as transaction type, amount, and balances. <br>
* Dataset: The dataset consists of 6,362,620 entries and 11 columns, with a significant class imbalance (99.87% legitimate transactions and 0.13% fraudulent transactions). <br>

Data Pre-Processing <br>
1. Data Loading: The dataset is read into a pandas DataFrame for analysis. <br>
2. Shape and Sample: The shape of the dataset (6,362,620 rows and 11 columns) is checked, and both the first and last 100 records are displayed to understand the data structure. <br>
3. Missing Values: Checked for null values, confirming that there are no missing entries. <br>
4. Data Types: Information about data types is gathered to prepare for encoding categorical features. <br>

Data Imbalance Analysis <br>
* Legitimate vs. Fraudulent Transactions: <br>
  * Legitimate transactions: 6,354,407 <br>
  * Fraudulent transactions: 8,213 <br>
  * This highlights a significant imbalance, prompting the selection of suitable models like Decision Trees and Random Forests. <br>
  
Data Visualization <br>
* Correlation Heatmap: A correlation matrix is generated to identify relationships between numerical features, helping to understand feature interactions. <br>
* Transaction Counts: A bar plot visualizes the distribution of legitimate vs. fraudulent transactions. <br>

Feature Engineering <br>
1. Identifying Merchants: Transactions involving merchants (identified by names starting with 'M') are filtered out for further analysis. <br>
2. Label Encoding: Categorical features (type, nameOrig, nameDest) are encoded into numerical values to facilitate model training. <br>
3. Multicollinearity Check: Variance Inflation Factor (VIF) is calculated to identify multicollinearity among features, leading to the creation of new features: <br>
   * Actual_amount_orig: Difference between old and new balances for the origin. <br>
   * Actual_amount_dest: Difference for the destination. <br>
   * TransactionPath: Sum of nameOrig and nameDest. <br>
   
Model Building <br>
1. Normalization: The 'amount' feature is scaled using StandardScaler, while other features remain unnormalized to retain model accuracy. <br>
2. Train-Test Split: The data is split into training (70%) and testing (30%) datasets. <br>

Model Training <br>
1. Decision Tree Classifier: A Decision Tree model is trained and evaluated. <br>
2. Random Forest Classifier: A Random Forest model is also trained with 100 estimators. <br>

Model Evaluation <br>
* Accuracy: <br>
  * Decision Tree Score: 99.92% <br>
  * Random Forest Score: 99.96% <br>
* Confusion Matrices: The confusion matrices reveal: <br>
  * True Positives (TP), False Positives (FP), True Negatives (TN), and False Negatives (FN) for both models. <br>
  * Random Forest shows lower false positives and higher true negatives compared to the Decision Tree. <br>
* Classification Reports: Precision, recall, and F1-scores indicate Random Forest performs better in terms of fraud detection metrics. <br>
* AUC-ROC Curves: ROC curves for both models are plotted, illustrating the trade-off between true positive rates and false positive rates. <br>

Conclusion <br>
* The Random Forest model demonstrates superior performance in identifying fraudulent transactions compared to the Decision Tree, primarily due to its ability to handle imbalanced classes more effectively and minimize false positives. <br>
* The project highlights the importance of feature engineering, model selection, and evaluation in building an effective fraud detection system. <br>
