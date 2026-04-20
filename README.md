# Big Mart Sales Prediction



## Business problem
A retail chain operating multiple outlets wants to understand which product and store attributes drive sales performance, enabling better decisions around inventory and store management. Using historical sales data, this project builds a predictive model to forecast item level sales and identify the key drivers behind them. 

## Data 
For this dataset, there were 8523 rows and 12 columns.

| Variable Name | Description |
|---|---|
| Item_Identifier | Product ID |
| Item_Weight | Weight of product |
| Item_Fat_Content | Whether the product is low-fat or regular |
| Item_Visibility | The percentage of total display area of all products in a store allocated to the particular product |
| Item_Type | The category to which the product belongs |
| Item_MRP | Maximum Retail Price (list price) of the product |
| Outlet_Identifier | Store ID |
| Outlet_Establishment_Year | The year in which the store was established |
| Outlet_Size | The size of the store in terms of ground area covered |
| Outlet_Location_Type | The type of area in which the store is located |
| Outlet_Type | Whether the outlet is a grocery store or some sort of supermarket |
| Item_Outlet_Sales | **Target variable** — Sales of the product in the particular store |

## Data Understanding & Exploration

- Confirmed no duplicate records were present in the dataset
- Standardized inconsistent labels in Item_Fat_Content 
- Identified missing values in Item_Weight and Outlet_Size — temporarily filled with placeholders to avoid data leakage.
- Validated data for impossible or unrealistic values


### Key Findings

- Higher-priced items consistently generate more sales.
- Supermarket Type 3 achieves the highest average sales despite having fewer products than Type 1.
- Grocery Stores have the lowest average sales by far. 

#### Sales Trend Across Price Segments

<img width="980" height="508" alt="Sales Trend Across Price Segments" src="https://github.com/user-attachments/assets/139a7017-9b2c-488a-8130-653da437a97a" />


*Items with higher retail prices show a clear upward trend in total outlet sales, confirming MRP as a strong sales driver.*

#### Outlet Type: Volume vs Sales Performance

<img width="981" height="525" alt="Outlet Type - Vlume vs Sales Performacne" src="https://github.com/user-attachments/assets/2d55a634-b9f5-431a-acd6-63cb0b9e37d9" />


*Despite Supermarket Type 1 carrying the most products, Type 3 outlets generate significantly higher average sales,suggesting that outlet type has more influence on sales than product volume alone.*


## Data preparation 

- Split data into training and testing sets.  
- Applied one-hot encoding to nominal categorical features.  
- Used ordinal encoding for ordered categories.  
- Scaled numerical features for consistency.  
- Imputed missing values using appropriate strategies. 


## Models

    - Linear Regression Model
    - Random Forest Regressor Model
    - Tuned Random Forest Regressor Model

## Model Performance Comparison

| Model                  | RMSE (Test) | MAE (Test) | R² (Test) |
|------------------------|-------------|------------|-----------|
| Linear Regression      | 1095.119    | 806.046    | 0.565     |
| Random Forest (Base)   | 1132.493    | 785.190    | 0.535     |
| Random Forest (Tuned)  | **1042.471**| **726.232**| **0.606** |


- The final model selected is the **Tuned Random Forest**, as it achieved the best balance between accuracy and generalization.

- On average, sales predictions are off by $726 per item
- Explains 61% of the differences in sales across outlets
- Notably, Linear Regression served as a strong baseline suggesting the data holds meaningful linear patterns
