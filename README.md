# Car Price Prediction - Regression Analysis

Dataset taken from: https://www.kaggle.com/datasets/hellbuoy/car-price-prediction

## Overview
This project focuses on predicting car prices using multiple linear regression. The dataset was analyzed to identify key predictors, address multicollinearity, and improve model performance. Key steps included data cleaning, exploratory data analysis (EDA), feature engineering, and model evaluation.

## Key Steps

### 1. **Data Preparation**
   - Loaded the dataset using the Pandas library.
   - Checked for missing values and confirmed the dataset was clean.
   - Identified and analyzed categorical and numerical variables.

### 2. **Exploratory Data Analysis (EDA)**
   - Examined relationships between predictors and the target variable (`price`).
   - Identified variables with high **linear** correlation:
     - `Enginesize`, `Curbweight`, `Carwidth`, `Carlength`, `Horsepower`.
   - Identified variables with high **non-linear** correlation:
     - `Highwaympg`, `Citympg`.

### 3. **Feature Engineering**
   - Combined `Highwaympg` and `Citympg` into a new variable, `com_mpg`.
   - Created interaction terms for highly correlated variables:
     - `Enginesize` × `Curbweight`
     - `Horsepower` × `Curbweight`
     - `Horsepower` × `com_mpg`
   - Removed redundant variables (`Carwidth`, `Carlength`, `Wheelbase`) to reduce multicollinearity.

### 4. **Model Building**
   - Built an initial multiple linear regression model.
   - Applied a natural logarithm transformation to the target variable (`price`) to address heteroscedasticity.
   - Evaluated the model using **RMSE** and **R²** metrics.

### 5. **Model Diagnostics**
   - Identified high-leverage points and removed them to improve model performance.
   - Computed the **Variance Inflation Factor (VIF)** to assess multicollinearity.
   - Removed variables with high VIF values (`Horsepower`, `Horsepower:Curbweight`).

### 6. **Final Model**
   - The final model had a higher RMSE and R² but included more significant predictors with reduced multicollinearity.
   - The model demonstrated decent predictive performance, though limited by the small dataset and increasing error variance with higher car prices.

## Challenges
   - **Heteroscedasticity**: Variance of errors increased with higher car prices, complicating regression analysis.
   - **Small Dataset**: Limited data availability constrained the model's robustness.
   - **Multicollinearity**: High correlation among predictors required careful feature engineering and variable selection.

## Tools and Libraries
   - Python
   - Pandas, NumPy, Scikit-learn, Statsmodels
   - Matplotlib, Seaborn for visualization

## Conclusion
This project highlights the importance of thorough EDA, feature engineering, and model diagnostics in building a reliable regression model. Despite challenges posed by the dataset, the final model provides a solid foundation for predicting car prices, with potential for further improvement using larger datasets or advanced modeling techniques.
