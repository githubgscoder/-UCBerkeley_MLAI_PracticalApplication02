# -UCBerkeley_MLAI_PracticalApplication02

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

Model Training: [Describe the training process, including hyperparameter tuning and evaluation metrics]
Model Evaluation: [Present the evaluation results, such as accuracy, precision, recall, F1-score, and other relevant metrics]
Key Findings
Significant Factors: [Highlight the most influential features identified by the models, e.g., mileage, year, make, model, condition]
Price Prediction: [Discuss the model's ability to accurately predict prices based on the identified factors]
Inventory Optimization: [Provide recommendations for optimizing inventory based on the findings, such as focusing on specific car models, mileage ranges, or price points]
Conclusion
Summary of Key Findings: Recap the main conclusions drawn from the analysis.
Recommendations: Offer actionable recommendations for used car dealers to improve their inventory management and pricing strategies.
[Include relevant visualizations, such as feature importance plots, scatter plots, and prediction accuracy graphs, to support your findings]
