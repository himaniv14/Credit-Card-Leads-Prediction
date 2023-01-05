# Credit-Card-Leads-Prediction

## Requirements
- python > 3.6
- pandas
- numpy
- matplotlib
- seaborn
- sklearn
- xgboost
- catboost  
- imblearn

## Problem Statement
  Happy Customer Bank is a mid-sized private bank that deals in all kinds of banking products, like Savings accounts, Current accounts, investment products, credit products,   among other offerings.
  The bank also cross-sells products to its existing customers and to do so they use different kinds of communication like telecasting, e-mails, recommendations on net         banking, mobile banking, etc.
  In this case, the Happy Customer Bank wants to cross-sell its credit cards to its existing customers. The bank has identified a set of customers that are eligible for         taking these credit cards.
  Now, the bank is looking for your help in identifying customers that could show higher intent towards a recommended credit card.
  
## Prediction Metric
  roc_auc_score

## Dataset

  This dataset was part of May 2021 Hackathon conducted by analytics vidhya, for more info check: https://datahack.analyticsvidhya.com/contest/job-a-thon-2/

## Dataset Description
  * ID - IUnique Identifier for a row
  * Gender- Gender of the Customer
  * Age-Age of the Customer (in Years)
  * Region_Code-Code of the Region for the customers
  * Occupation-Occupation Type for the customer
  * Channel_Code-Acquisition Channel Code for the Customer (Encoded)
  * Vintage-Vintage for the Customer (In Months)
  * Credit_Product-If the Customer has any active credit product (Home loan, Personal loan, Credit Card etc.)
  * Avg_Account_Balance- Average Account Balance for the Customer in last 12 Months
  * Is_Active-If the Customer is Active in last 3 Months

## Data Understanding
  * Shape of the data
  * Number of columns and their dtypes
  * Null value analysis (Found some Null values in Credit Product column which are of significant amount, so didnt remove them)
  * ID column values from both the sets are captured to a list and dropped from dataframes.

## Descriptive Analysis
- Exploratory Data Analysis is done for each independent column with target column and meaningful insights are observed.
  * Gender - Male are more inclined for credit card.
  * Age - People from 43 to 60 years of age shown much interest for credit cards.
  * Region_Code - People from some regions have shown interest.
  * Occupation - Self_Employed and Salaried people are our lead compared to Entrepreneur.
  * Channel_Code - X2 and X3 are more intrested
  * Vintage - people with vintage 13-33 and 80-99 are mre intrested
  * Credit_Product - People who already have credit product have shown more affinity.(This column has null values and as observed 80% of people out of these null rows are                            likely to have a credit card.)
  * Is_Active - People who are not active are in need of money
  * Avg_Account_Balance - People with higher account balance have shown more interest.

## Pre-Processing
  * Label Encoding is done for columns Credit_Product, Region_Code, Gender, Occupation, Is Active, Channel_Code.(Also tried binning the data for some columns and then encode     but results are degraded)
  * Log transformation is applied for Avg_Account_Balance column since it is right skewed.
  * From heatmap we can observe the correlation between variables and target column.

## Model Building
  * Train test split is done with 80:20 ratio.
  * We can observe that there is an imbalance in our target variable. Oversampling is done to balance the classes.
  * Started with baseline XGBoostClassifier and then manually finetuned it.
  * Also used CatBoostClassifier and optimized it.
  * It is observed that both the models performed well and so I went for stacking.
  * For StackingClassifier base models XGBoost and CatBoost are passed and LogisticRegression is used are meta model.
  * Final Model is built with improved performance!

## Predictions
  * Atlast predictions are made for test data and got roc auc score of 0.8732186587

## Future Improvements
  * Deep Learning models can be given a shot for improvement in score.
