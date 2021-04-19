# Project 1: California Housing Prices

Credit: O'Reilly Hands-on ML Projects book, Chapter 2 

## **BLUF:**
The best performing model is the random forest using the top `8 features`, `30 trees`, `median` as imputer input

*Future Work:* Use ensemble method to improve the performance

## **Summary:**
**Assumptions:**
1. Data has labels (median housing prices) that can be used with supervised learning
2. Outputs will be numerical (prices) and not categorical

**Data:**

*Source:* from R.Kelley Pace and Ronald Barry, "Sparse Spatial Autoregressions," Statistics and Probability Letters 33, no. 3 (1997): 291-297

* There are 10 attributes, all but one are numerical data.
* There are 20,640 entries total, note that the total_bedrooms only has 20,433 non-null values
* The ocean_proximity attribute is categorical and has five categories.

| # |Column| Non-Nul Count| Values |
|---|------|--------------|------|
| 0 |longitude|20640|float64|
| 1 |latitude|20640|float64|
| 2 |housing_median_age|20640|float64|
| 3 |total_rooms|20640|float64|
| 4 |total_bedrooms|20433|float64|
| 5 |population|20640|float64|
| 6 |households|20640|float64|
| 7 |median_income|20640|float64|
| 8 |median_house_value|20640|float64|
| 9 |ocean_proximity|20640| [`"<1H OCEAN", "INLAND", "NEAR OCEAN", "NEAR BAY", "ISLAND"`]

**Methods/Results:**

1. Test set: used stratiefied sampling based on `median_income` and split the data 20/80
2. Data cleaning: 
  * filled in missing `total_bedrooms` values using the median
  * transformed `ocean_proximity` using a one-hot encoder
  * feature scaling using standardization
3. ML models:
  * Linear Regression with cross-validation
    ``` 
        Mean rmse:  69057.11157686297
        Standard deviation:   2741.1360125330416
    ```
  * Decision Tree with cross-validation
    ``` 
        Mean rmse:  71407.68766037929
        Standard deviation:  2439.4345041191004
    ```
  * Random Forest with cross-validation and hyperparameters grid search
    ``` 
        Mean rmse:  47730.22690385927
        Standard deviation:  2097.0810550985693
        Best params: 
          GridSearchCV: {'max_features': 8, 'n_estimators': 30}
          RandomizedSearchCV: {'max_features': 7, 'n_estimators': 180}
    ```
  * SVM with cross-validation and hyperparameters grid search
    ``` 
        Mean rmse:  70363.84006006805
        Standard deviation:  2097.0810550985693
        Best params: 
          GridSearchCV: {'max_features': 8, 'n_estimators': 30}
          RandomizedSearchCV: {'max_features': 7, 'n_estimators': 180}
    ```
4. Model Tuning:
  * GridSearch best params: `{'feature_selection__k': 8, 'preparation__nums__imputer__strategy': 'median'}`
