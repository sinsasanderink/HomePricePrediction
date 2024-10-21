# Home Price Prediction Using Regression and Decision Tree Models

## Overview
This project aims to predict housing prices based on various features such as area, number of bathrooms, parking spaces, etc., using different machine learning techniques. We explore and compare three models: Multiple Linear Regression, Decision Trees, and Random Forest, to determine which model provides the most accurate predictions.

## Project Workflow

### Step 1: Data Understanding and Preprocessing
We begin by importing the dataset and performing an initial exploration:
- **Dataset:** Contains features like area, number of bedrooms, bathrooms, parking, and more.
- **Objective:** To identify the key factors influencing house prices and build predictive models.

Data exploration involves:
- Checking data types and handling missing values.
- Visualizing relationships between variables using pair plots and box plots to understand data distribution and correlations.
- Converting categorical variables (e.g., yes/no values) into binary (1/0) to prepare the dataset for modeling.

### Step 2: Feature Engineering
- **Creating Dummy Variables:** We converted categorical features such as `furnishingstatus` into dummy variables for use in the regression models.
- **Normalization:** Used MinMax scaling for continuous features (e.g., area) to ensure all variables are on a similar scale.

### Step 3: Train-Test Split
- **Splitting the Data:** The dataset is split into training (70%) and testing (30%) sets to evaluate the model's performance.
- **Random Seed:** A fixed random seed ensures consistent results across multiple runs.

### Step 4: Building Multiple Linear Regression Model
- **Initial Model:** We started with a simple linear regression using `area` as the predictor. 
- **Adding Variables:** Added more features (e.g., bathrooms, bedrooms) iteratively and observed the adjusted R-squared to assess model improvement.
- **Feature Selection:** Used p-values and VIF (Variance Inflation Factor) to remove insignificant or highly collinear variables. After several iterations, we arrived at a final linear regression model with the following features:
  - Area, bathrooms, stories, mainroad, guestroom, hotwaterheating, airconditioning, parking, prefarea, and unfurnished.
- **Model Evaluation:** 
  - R-squared (Train): 0.676
  - R-squared (Test): 0.660

### Step 5: Decision Tree Regression
- **Model Setup:** We created a decision tree regressor to predict housing prices.
- **Model Insights:** 
  - The highest-priced homes had more than 1.5 parking spaces, over 1.5 bathrooms, and a large area (above 5930 sq ft).
  - The lowest-priced homes had smaller areas, fewer bathrooms, and were unfurnished.
- **Model Performance:** The R-squared score was significantly lower compared to linear regression, indicating that the decision tree model did not perform well.

### Step 6: Random Forest Regression
- **Building the Model:** Utilized multiple decision trees (random forest) to improve prediction accuracy.
- **Model Insights:** Random forest allows for capturing non-linear relationships better than a single decision tree.
- **Feature Importance:** The most influential factors were identified through feature importance scores.
- **Model Evaluation:**
  - R-squared (Train): 0.678
  - R-squared (Test): 0.585

### Step 7: Model Comparison and Conclusion
- **Comparison:** 
  - **Multiple Linear Regression:** Best performance with an R-squared of 0.676 (Train) and 0.660 (Test). Indicates a relatively good fit and a straightforward interpretability.
  - **Decision Tree:** Poor performance, not recommended.
  - **Random Forest:** Better than decision tree but not as effective as linear regression, with R-squared values of 0.678 (Train) and 0.585 (Test).
- **Conclusion:** Multiple linear regression outperformed the other models and provided clearer insights into the variables affecting home prices. Future improvements could include adding new features or exploring non-linear models for better performance.

## Key Insights
- The most critical factors affecting house prices are area, number of bathrooms, and air conditioning.
- Furnishing status and parking availability also have a notable impact on prices.
- While the linear regression model provided the best overall fit, the random forest model can still be improved by hyperparameter tuning or additional data.

### Image Visualization
![Decision Tree Visualization](heartdisease.png)

## Libraries Used
- `pandas`, `numpy`: For data handling and preprocessing.
- `matplotlib`, `seaborn`: For data visualization.
- `sklearn`: For model building, evaluation, and train-test splitting.
- `statsmodels`: For regression analysis and model summaries.

## Future Improvements
1. **Feature Engineering:** Explore new feature combinations (e.g., area/rooms ratio) to enhance prediction accuracy.
2. **Model Tuning:** Perform hyperparameter tuning for the random forest model to improve performance.
3. **Non-Linear Models:** Consider using advanced models like XGBoost or neural networks to capture more complex relationships.
