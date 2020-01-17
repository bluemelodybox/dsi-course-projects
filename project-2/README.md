# Project 2 - Ames Housing Data and Kaggle Challenge

### Problem Statement

The intend of this project is to create and select the best regression model for predicting housing sales price.

### Data Source

[Train](./data/train.csv) | [Test](./data/test.csv) | [Data Documentation](./data/DataDocumentation.txt)

### Approach

1. Data Imputation
   - Finding out columns with missing values and remove rows less than 0.1% of data
   - Some of the columns have missing data because the house does not come with it such as basement and garage. Hence, it is safe to fill them with 0.
   - Lot frontage data seems to be missing at random. Using neighbourhood median to determine might help.
2. Separating variable types to nominal, ordinal, discrete and continuous
3. Within each types, filter out columns that are not relevant
   - For categorical variables, columns that have high frequency of same category are filtered out based on a certain threshold
   - For continuous variables, correlation with sales prices is used as a gauge to narrow down features
4. EDA filtered features with with scatter plots and histograms
5. Dropping outliers
   - From the scatter plots of category vs sales price, it is easy to identify and drop outliers
6. Label encoding for ordinal categorical variables
7. One hot encoding for nominal variables
   - Filter and remove out features that have low variance mean price per category
   - Perform one hot encoding
8. Increase features by using polynomial feature for filtered continuous variables
9. Perform train-test split and standard scaling
10. Perform cross validation for Linear Regression, Lasso Regression and Ridge regression
11. Model Scoring and Selection
12. Cleaning test data
13. Fitting test data to selected model
14. Visualize top coefficients
15. Output predicted sales price to csv for Kaggle submission



### Kaggle RMSE Score

| Data & Model                                                 | Score difference | Kaggle Score (RMSE) |
| ------------------------------------------------------------ | ---------------- | ------------------- |
| Using top 5 continuous variables that are the most correlated with sales price without any cleaning | First Submission | 43013               |
| After cleaning most of the data mentioned from point 1 to 12 and performing RidgeCV with binning years | Improved         | 29537               |
| Same as point 2 but using LassoCV and not binning years      | Not much changes | 29410               |
| Same as point 3, and in addition dropping low variance nominal features which includes (Lot Config Roof Style, MS Sub Class and Exterior 2nd) with LassoCV | Improved         | 28066               |
| Same as point 4 and dropping features with 0 lasso coefficient from training model | Improved         | 23272               |
| Same as point 5 and applying polynomial features with LassoCV | Deproved         | 22542               |

Tried tweaking different hyperparameters such as skew threshold value and n_alpha score but the RMSE and adjusted r squared score difference is negligable and hence not in the table above.



### Conclusion

Final model is selected based on highest adjusted r squared score on test and lowest rmse score on kaggle. 

The final selected model is to use lasso regression to reduce model complexity and uses about 113 features including dummies variables to achieve 22542 RMSE score. It might however be overfitted due to the addition of polynomial features as we can see a sharp decrease in bias (low rmse score) and an increase between the difference the public and private score. (~8k difference)

Using top 30 lasso coefficient features increases the RMSE score as compared to using 113 features. (Bias and Variance trade-off)

To have a more generalized model, it is better to not use polynomial features for training as it has low difference between public and private score. (less than 1k difference)