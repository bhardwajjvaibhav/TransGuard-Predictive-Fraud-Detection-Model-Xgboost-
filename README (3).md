# TransGuard- Fraud Prediction Model

1. Developing a model for predicting fraudulent transactions for a
financial company and use insights from the model to develop an actionable plan. 

2. Model is  estimated on the calibration data and tested on the validation data. 

# Data Description
Data for the case is available in CSV format:
    
    1. Rows: 6362620 
    2. Columns: 10

# Project Life Cycle
1. Data Ingestion
2. Data Preparation
    
    a. Data Wrangling
    
    b. Feature Engineering:
        
        i. Feature Selection
        ii. Feature Extraction
    
3. Model Selection
4. Model Training and Hyperparameter Tuning
5. Model Evaluation
6. Model Deployment


# Data Ingestion
Data for the case is available in CSV format:
    
    1. Rows: 6362620 
    2. Columns: 10
Data was imported as csv file.
# Data Preparation

## 1. Data Wrangling

Cleaning and transforming raw data into a usable format,    handling missing data, fixing inconsistencies, and ensuring data quality.

    Steps Followed:

    1. Data Completness:: Checking for missing/null values.Ensuring all required data is present. Missing values were imputed using mean or most frequent values(for categorical data) 

    2. Data Consistency : Using info() method to analyze data types of different features and ensuring features of same type have similar data types to maintain the Consistency.

    3. Data Uniqueness : Checking for the unique identifiers like nameorig i.e unique id is not repeated with the same set of values resulting in duplicate data.

    4. Outlier detection :: We will check for the outliers. But completly omitting the outliers wont be the great approach as during transactions. Some transactions can be of large values not necessarily identicating a fraud. For this we will try to select a model that is robust with the outliers.

## 2. Data Analysis : 
    
    Results:
    
    a. Fraudulent transaction occurs through 'Transfer' mode only.

    b. We detected some outliers values but we wont treat it rather we will be using a ml model that is more robust with outliers
    c. In order of transactions mode : 
    CASH_OUT> PAYMENT>CASH_IN> TRANSFER> DEBIT . CASH_IN have highest number of activities. No transaction were flagged as fraud when the mode was cash_out 

## 3. Feature Engineering : 
Further divided into:
    
#### i. Feature Selection:
    
    Feature Importance: Analyzed using Chi-square test and visualized with Extra Trees Classifier.
    
Pearson Correlation: Visualized with a heatmap to identify highly correlated features.

        Multicollinearity:
        Checked using correlation matrix and variance inflation factor (VIF).


#### ii. Feature Encoding:: 
Used label encoding for categorical features like type, nameOrig, and nameDest.

#### iii. Ranking Features: 

Ranked the features based on the score using Chi2.
Used Extra tree classifier to visualize the important feature
 


#### iv. Feature Extraction:

•	Applied Principal Component Analysis (PCA) to combine Org_Oldbalance, Org_Newbalance, Dest_Oldbalance, and Dest_newbalance into two principal components.



Compared Random Forest models with and without PCA.

Chose the model without PCA for better interpretability.

v. Dropping Features with less importance:: 

Based on feature importance we will drop the features with less importance and high collinearity i.e. Org_Newbalanceand and Dest_oldbalance.



## Model Selection
As we have to choose a model that is robust with outliers we will consider evaluating ensemble models
 1. Xgboost
 2. GradientBoost
 3. Adaboost
 4. RandomForest

 On evaluation we found that all the model except xgboost were overfitting.


## Model Evaluation

Before Evaluating the final modle metrics we first evaluated the two models : 
    1. One with PCA
    2. Without PCA (Dropped highly correlated features)

Result: One with PCA was overfitting. So we choose the one without PCA

## Model Evaluation Metrics:

Each Model was evaluated on following metrics:

    1.Accuracy
    2.Precision
    3.Recall
    4.F1 Score
    

## Conclusion
Conclusion:
•	XGBoost is the best choice because it:
1.	Has the highest accuracy, precision, recall, and F1 score on both validation and testing sets.
2.	Offers robust generalization and efficiency, crucial for real-world fraud detection

Classification Report of the Model:

Validation Set Metrics:

    Accuracy: 0.9986666666666667
    Precision: 0.9986684480071253
    Recall: 0.9986666666666667
    F1 Score: 0.9985004456327986

Testing Set Metrics:

    Accuracy: 0.999
    Precision: 0.99900100050025
    Recall: 0.999
    F1 Score: 0.9987502502502502

    ## Reasons to Choose XGBoost
#### 1.Performance:

XGBoost is known for its high performance in various machine learning tasks. It often provides competitive results, especially in large datasets.

#### 2.Handling Imbalanced Data:

XGBoost has built-in mechanisms to handle imbalanced datasets, which is often the case in fraud detection problems. It allows you to set weights for classes, helping the model focus on minority classes (e.g., fraudulent transactions).
Regularization:

XGBoost includes L1 (Lasso) and L2 (Ridge) regularization, which helps prevent overfitting and can lead to better generalization, especially in complex models.

#### 3.Feature Importance:

XGBoost provides insights into feature importance, which can help you understand which features contribute most to your model's predictions.

#### 4.Flexibility:

It supports different objective functions and allows for customization. You can also tweak hyperparameters to optimize the model's performance further.

#### 5.Speed:

XGBoost is designed to be efficient and fast. Its implementation is optimized for speed and performance, allowing for quicker training times compared to some other algorithms.
Community and Documentation:

There is a robust community around XGBoost, along with extensive documentation and tutorials available online, making it easier to learn and troubleshoot.