# Supply-Chain-Management
A machine learning project for predicting warehouse product movement using regression and ensemble models.

## Supply Chain Management: Warehouse Product Movement Prediction

## Project Overview
This project aims to predict warehouse product movement (product weight in tons) using warehouse infrastructure, operational, and logistical factors. The objective is to identify key drivers of warehouse productivity and develop machine learning models to support supply chain planning and decision-making.

## Business Problem
Efficient warehouse operations are critical for supply chain performance. Organizations need to understand how factors such as warehouse capacity, infrastructure, workforce, storage issues, and distribution networks impact product movement. This project builds predictive models to estimate warehouse throughput and generate actionable business recommendations.

## Dataset
•	25,000 warehouse records 
•	Numerical and categorical features 
•	Target Variable: product_wg_ton 

## Key Steps
•	Conducted Exploratory Data Analysis (EDA) to understand data distribution, identify patterns and assess relationships between variables.
•	Performed data cleaning by removing identifier variables (‘Ware_house_ID’ and ‘WH_Manager_ID’) that did not contribute to the prediction.
•	Handled missing values using appropriate imputation techniques:
o	‘workers_num’ – 990 missing values – Median imputation
o	‘approved_wh_govt_certificate’ – 908 missing values – Mode imputation
o	‘wh_est_year’ – 11881 missing values – transformed into ‘wh_age’ and imputed missing values.
•	Engineered new features:
o	Warehouse Age (wh_age)
o	Infrastructure Score (infra_score)
•	Detected outliers in ‘retail_shop_num’, ‘workers_num’ and ‘Competitor_in_mkt’. Applied IQR-based capping (Winsorization) to reduce the impact of extreme values while preserving valuable supply chain information.
•	Applied Standard Scaler to normalise numerical features and improve model stability.
•	Built a baseline Linear Regression model and evaluated RMSE, MAE, MAPE, R-squared, and Adjusted R-squared. 
•	The Linear Regression model achieved an R² of 0.99, but its performance was heavily influenced by the highly correlated feature storage_issue_reported_l3m (correlation = 0.99).
•	Developed an alternative baseline excluding this feature, the baseline model performance reduced to R² = 0.48, providing a more realistic benchmark.
•	Developed and executed 6 advanced regression models:
o	Decision Tree Regressor
o	Bagging Regressor
o	Random Forest Regressor
o	AdaBoost Regressor
o	Gradient Boosting Regressor
o	XGBoost Regressor
•	Selected Random Forest, Gradient Boosting, and XGBoost for hyperparameter tuning due to their strong predictive performance and potential for further improvements.
•	Selected the Tuned Gradient Boosting Regressor as the final model based on:
o	Highest Test R² Score (0.56)
o	Lowest Test RMSE (7668.57)
o	Strong generalisation capability
o	Stable train-test performance
•	Provided actionable insights and recommendations to improve warehouse operations, management, storage and overall efficiency.

## Model Performance
Model	Test R²
Linear Regression	0.48
Decision Tree	0.09
Random Forest (Tuned)	0.56
Gradient Boosting (Tuned)	0.56
XGBoost (Tuned)	0.54

## Best Model
Gradient Boosting Regressor
Performance:
•	RMSE: 7668.57 
•	MAE: 5886.27 
•	R²: 0.56 
•	MAPE: 39.02% 

## Key Insights 
• The variable ‘storage_issue_reported_l3m’ showed a very strong relationship with the target variable ‘product_wg_ton’. Warehouses reporting higher storage issues had higher product movement. This feature was later identified as a potential data leakage variable and removed from the baseline model. 
• Warehouses with better infrastructure conditions like electric supply, flood proof facilities, temperature regulation systems showed better warehouse functioning and product handling. 
• Warehouse capacity and workforce affected the product shipment. Larger warehouses with more workforce and greater distributor coverage handled larger product volumes. 
• Geographical factors influenced the warehouse performance. Warehouses located farther from distributor hubs experienced lower operational efficiency due to transportation and delivery challenges. 

## Actionable Business Recommendations 
• The company should invest in temperature regulation systems, backup power supply and flood proof mechanisms to improve the efficiency and reduce the disruptions. 
• According to the numbers, the workforce doesn’t really affect the product movement. So, focus on productivity improvement by implementing training, using technology and automation. 
• Increase storage capacity to accommodate growing product volumes and reduce storage related issues. 
• Consider expanding warehouse capacity in high volume regions to reduce delivery times and improve customer service levels 
• Lower certified warehouses can adopt best practices from highly certified warehouses to improve the quality standards, and overall performance.


