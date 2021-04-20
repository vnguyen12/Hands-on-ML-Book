# Project 2: Ames, Iowa Housing Prices

**Acknowledgement:** The Ames Housing dataset was compiled by Dean De Cock for use in data science education.

## **BLUF:**

TODO 

## **Summary:**
### **Assumptions:**
1. Target data has labels (housing prices) that can be used with supervised learning
2. Outputs will be numerical (prices) and not categorical

### **Data:**

*Source:* from Dean De Cock, "Ames, Iowa: Alternative to the Boston Housing Data as an End of Semester Regression Project," Journal of Statistics Education, Volume 19, Number 3(2011)

* There are 79 explanatory features, with a mix of categorical and numerical features
* Categorical features:
  * Nominal: simple labels with no ordering/implied sequence, ie. 'Neighborhood' has values ['CollgCr', 'OldTown', 'Gilbert', etc.]
  * Ordinal: categorical data that have ordering, ie. scale ['Excellent', 'Good', 'Fair' 'Poor']
* Numerical features:
  * Ordinal: numerical scales that has ordering, ie. 'OverallQual' has values ranging from 1-10
  * Continuous: continous numerical data, ie. 'LotFrontage' describes the square footage of the lot
  * Discrete: discrete numerical data, ie. 'FullBath' indicates the number of bathrooms
```
cat_feats_nominal = ['MSSubClass', 'MSZoning', 'Neighborhood', 'Condition1', 'Condition2', 'HouseStyle', 'CentralAir', 'MiscFeature', 'MoSold', 'YrSold', 'SaleType', 'SaleCondition', 'Electrical', 'MasVnrType', 'Exterior1st', 'Exterior2nd', 'Heating', 'Foundation']
cat_feats_ordinal = ['Alley', 'LotShape', 'LandContour', 'LotConfig', 'LandSlope', 'BldgType', 'RoofStyle', 'RoofMatl', 'ExterQual', 'ExterCond','BsmtQual', 'BsmtCond', 'BsmtExposure', 'BsmtFinType2', 'BsmtFinType1', 'HeatingQC', 'KitchenQual', 'Functional', 'FireplaceQu', 'GarageType', 'GarageFinish', 'GarageQual', 'GarageCond','PavedDrive', 'Fence']

numeric_feats_cont= ['LotFrontage', 'LotArea', 'YearBuilt', 'YearRemodAdd', 'MasVnrArea', 'BsmtFinSF1', 'BsmtFinSF2', 'BsmtUnfSF', 'TotalBsmtSF', '1stFlrSF', '2ndFlrSF', 'GrLivArea', 'GarageYrBlt', 'GarageArea', 'WoodDeckSF', 'OpenPorchSF', 'EnclosedPorch', '3SsnPorch', 'ScreenPorch', 'PoolArea', 'MiscVal', 'TotalSF', 'TotalSF1', 'YrBltAndRemod', 'TotalBathrooms', 'TotalPorchSF']
numeric_feats_ordinal= ['OverallQual', 'OverallCond']
numeric_feats_discrete= ['BsmtFullBath', 'BsmtHalfBath', 'FullBath', 'HalfBath', 'BedroomAbvGr', 'KitchenAbvGr', 'TotRmsAbvGrd', 'Fireplaces', 'GarageCars','haspool', 'has2ndfloor', 'hasgarage', 'hasbsmt', 'hasfireplace']
```

### **Methods:**
1. **Data Inspection:**
    * Use histogram and correlation matrix to visualize the relationships between two variables
    * The features that highly correlate with SalePrice are:
      * OverallQual (0.79)
      * GrLivArea (0.71), GarageArea (0.62), TotalBsmtSF (0.61), 1stFlrSF (0.61)
      * YearBuilt (0.52), YearRemodAdd (0.51)
      * FullBath(0.56), TotRmsAbvGrd (0.53), GarageCars (0.64)
    * Each of these features are then plotted individually against SalePrice
  
2. **Data Cleaning/Processing:**
    * Remove outliers, unnecessary features
    * Fix data types
    * Impute missing values
    * Analyze for multicollinearity using Variance Inflation Factor and remove feature 'LowQualFinSF'
  
3. **Feature Scaling/Engineering:**
    * Correct for data skewness by using Box Cox transformation 
    * Add 10 new features to the train and test sets
    * Encode categorical features using labels and one-hot encoding
  
4. **Target Variable Analysis:**
    * Adjust for skewness in 'SalePrice' variable using log transformation
    
5. **Regression Models:**
    * Use linear, Bayesian ridge, ridge, lasso, elastic net, svm, and gradient boosting regressor as an ensemble

### **Results:**
TODO
