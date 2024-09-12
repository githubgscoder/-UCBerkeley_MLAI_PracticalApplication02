# UCBerkeley_MLAI_PracticalApplication02

Report: Optimizing Used Car Inventory
Introduction
This report presents the findings of a data analysis project aimed at optimizing used car inventory. The goal was to identify key factors influencing used car prices and provide insights for dealers to make informed decisions.

Data Analysis
Data Sources: https://mo-pcco.s3.us-east-1.amazonaws.com/BH-PCMLAI/module_11/practical_application_II_starter.zip

Data Cleaning and Preparation: 
1. Dropped all rows of data where manufacturer and model did not have any data
2. Dropped id and VIN as it wasn't required to train the model.
3. Filled the value 'unknown' for the following columns - cylinders, fuel, title status, transmission, drive, size, type and paint color
4. Dropped additional rows that had no values in year and odometer
5. Filtered down the dataset to only include data with vehicles that had less than 999,999 on their odometer
6. Included only vehicles with a price greater than $999
7. Since there is a possibility of price variation across regions and states, filtered down the data to just the state of CA with regions having greater than 1500 datapoints
8. Converted all manufacturer and model to lower case

Feature Engineering:
1. Added price ratio as a ratio of price and odometer
2. Added age derived as the year 2024 - year the vehicle was manufactured

Model Development and Evaluation
Model Selection: 
1. Looked at 3 models built using Ridge, Lasso and Linear Regression
2. Applied KFold and GridSearchCV to find the best parameters with the Ridge and Lasso model

Model Training:
Two different approaches were taken, one was to train a model with the manufacturer and model and the second to remove them and then train the model. A pre-processor was created to transform the columns based on categorical and numerical data types, OneHotEncoder was used for categorical columns and StandardScaler for numerical columns.

Ridge model
1. Created a pipeline to use the preprocessor and ridge regressions for various alphas 0.1, 1, 10, 100
2. Found the best alpha and reran the model
3. Created another model using KFold and GridSearchCV using neg_mean_squared_error for scoring to find the MSE.

Lasso Model
1. Created a pipeline to use a preprocessor on the categorical and numerical columns but also applied PolynomialFeatures to a degree of 2 on the numerical columns, created an alternative with a passthrough as well.
2. Used SequentialFeatureSelector using linear regresson to select 5 features
3. Applied lasso regression
4. Created another model using KFold cross validation and GridSearchCV Hyperparameter tuning

Linear Regression
1. Created a pipeline to use a preprocessor on the categorical and numerical columns but also applied PolynomialFeatures to a degree of 2 on the numerical columns, created an alternative with a passthrough as well.
2. Used SequentialFeatureSelector using linear regresson to select 5 features
3. Applied linear regression
4. Left this model at Hold out cross validation


Model Evaluation:

Ridge Vs. Linear Vs. Lasso
  ![image](https://github.com/user-attachments/assets/bd81b7c4-c655-45a7-a719-3a0c5f36409c)

Lasso Regression Feature Importance
  ![image](https://github.com/user-attachments/assets/6e7ef95b-9553-452b-979c-ce98caac14ff)

Ridge Regression Feature Importance
  ![image](https://github.com/user-attachments/assets/c86b0114-5ff3-4114-8793-f9ae398c4fa2)

Linear Regression Feature Importance
  ![image](https://github.com/user-attachments/assets/85bbccce-3844-4bdb-af36-600b93dc7a1b)



Key Findings
Significant Factors: Three of the models mentioned that odometer readings were a key factor in predicting price, followed by type of the vehicle. The Linear and Lasso regression model transmission and title_status that played additional roles, whereas for the model that included the manufacturer and model into the training data, showcased manufacturer, model, odometer and age and price predictors.

Conclusion
Summary of Key Findings: In the state of California, purchase of inventory on ceratain types of vehicle like the sedans and SUVs had a lot of demand and as expected lower the odometer readings the car pricings where higher.
![image](https://github.com/user-attachments/assets/3855b01d-6f77-4a97-9585-a1a6b3951d96)

![image](https://github.com/user-attachments/assets/d094979d-6679-4d23-ae6f-14a3c698cf6b)

![image](https://github.com/user-attachments/assets/59fd3745-3442-42ca-b96e-d95ea0d527fc)

![image](https://github.com/user-attachments/assets/d1e27ad1-1656-48af-bb62-5ef22234b5b6)


Next Steps: It would be good to look at it state by state to see if the features change or if they are all the same. We could also look at top sellig manufacturers and models to look at the features that consumers are searching for in a vehicle.



