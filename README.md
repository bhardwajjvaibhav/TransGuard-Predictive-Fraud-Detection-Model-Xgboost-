# TransGuard-Predictive-Fraud-Detection (Xgboost)
Fraudulent Transaction Predicting Model
1. Data cleaning including missing values, outliers and multi-collinearity.
2. Describe your fraud detection model in elaboration.
Flow of the Model:
1.	Loading the Dataset
2.	Data Cleaning
3.	Data Analysis (Focusing on Outliers and Correlation)
4.	Feature Engineering
5.	Feature Selection
6.	Feature Extraction
7.	Evaluating Different Models
8.	Training and Evaluating the Final Model
1. Data Cleaning
•	The dataset had no missing or null values.
2. Data Analysis

Outliers:
•	Visualized using boxplots.
•	Not removed because XGBoost can handle them well.
•	Outliers in fraud cases can be significant and should be retained.

Multicollinearity:
•	Checked using correlation matrix and variance inflation factor (VIF).
3. Feature Encoding
•	Used label encoding for categorical features like type, nameOrig, and nameDest.

3. How did you select variables to be included in the model?
4. Feature Selection and Extraction

Feature Selection:
•	Feature Importance: Analyzed using Chi-square test and visualized with Extra Trees Classifier.
•	Pearson Correlation: Visualized with a heatmap to identify highly correlated features.
•	Dropped less important features like newbalanceOrig and oldbalanceDest.

Feature Extraction:
•	Applied Principal Component Analysis (PCA) to combine oldbalanceOrg, newbalanceOrig, oldbalanceDest, and newbalanceDest into two principal components.

5. Model Evaluation
•	Compared Random Forest models with and without PCA.
•	Chose the model without PCA for better interpretability.

6. Model Selection
•	Evaluated different models: Random Forest, AdaBoost, XGBoost, and Gradient Boosting.
•	Trained and evaluated each model on testing and validation data.

Result:
•	XGBoost and Gradient Boosting performed similarly well.
•	Random Forest showed high metrics but also signs of overfitting.
•	AdaBoost performed well but slightly less effectively.

Conclusion:
•	XGBoost is the best choice because it:
1.	Has the highest accuracy, precision, recall, and F1 score on both validation and testing sets.
2.	Offers robust generalization and efficiency, crucial for real-world fraud detection.
Summary
XGBoost is selected for its balanced performance and efficiency, making it suitable for detecting fraudulent transactions in banking.
