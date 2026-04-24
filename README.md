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
- Identified missing values in Item_Weight and Outlet_Size - temporarily filled with placeholders to avoid data leakage.
- Validated data for impossible or unrealistic values


### Key Findings

- Higher-priced items consistently generate more sales.
- Supermarket Type 3 achieves the highest average sales despite having fewer products than Type 1.
- Grocery Stores have the lowest average sales by far. 

#### Sales Trend Across Price Segments

<img width="980" height="508" alt="Sales Trend Across Price Segments" src="https://github.com/user-attachments/assets/139a7017-9b2c-488a-8130-653da437a97a" /> <br>

*Items with higher retail prices show a clear upward trend in total outlet sales, confirming MRP as a strong sales driver.*

#### Outlet Type: Volume vs Sales Performance

<img width="981" height="525" alt="Outlet Type - Vlume vs Sales Performacne" src="https://github.com/user-attachments/assets/2d55a634-b9f5-431a-acd6-63cb0b9e37d9" /> <br>

*Despite Supermarket Type 1 carrying the most products, Type 3 outlets generate significantly higher average sales suggesting that outlet type has more influence on sales than product volume alone.*


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


## Feature Importance

### Linear Regression — Top Coefficients

<img width="743" height="745" alt="Linear Reg coff" src="https://github.com/user-attachments/assets/5c0037b2-33ec-42c9-a36f-7c4921837920" /><br>

- **Outlet_Type_Supermarket Type3:** Being sold in a Type 3 Supermarket adds ~$$1,605 to predicted sales. These outlets are high-performing regardless of product volume.
- **Item_MRP:** Every 1$ increase in a product's retail price is associated with ~$984 increase in sales, confirming price as a core sales driver.
- **Outlet_Type_Grocery Store:** Products sold in Grocery Stores are predicted to generate ~$1,722 less in sales. Significant performance gap between outlet formats.


### Random Forest — Feature Importances
<img width="1019" height="594" alt="Rf Importance" src="https://github.com/user-attachments/assets/110f2b6d-fccc-4a5d-ad46-7b89d4914236" /><br>

1. **Item_MRP (~0.55)** - By far the most dominant predictor. Price alone explains over half of the model's predictive power.
2. **Outlet_Type_Grocery Store (~0.29)** - Outlet format is the second most critical factor
3. **Outlet_Type_Supermarket Type3 (~0.12)** - Confirms the high-performance of Type 3 outlets.
4. **Outlet_Type_Supermarket Type1 & Type2 (~0.02 each)** - Both show minimal but present influence, far below Type3.

**Item_Visibility and Outlet_Size showed near zero importance**, they have little practical influence on sales despite their intuitive relevance.


## Recommendations

1. **Prioritize high-MRP product placement** - Price is the strongest predictor of sales. Stocking and promoting premium-priced items should be a core strategy across all outlets.

2. **Invest in Supermarket Type 3 expansion** - Despite having fewer locations than Type 1, Type 3 outlets generate significantly higher average sales. Opening more Type 3 stores is likely a better use of resources than expanding Type 1 further.

4. **Re-evaluate Grocery Store strategy** - Grocery Stores show the weakest sales performance by a large margin. A format upgrade or a shift in product mix could help close this gap.

5. **Don't over invest in shelf space optimization** - Item visibility had almost no impact on sales in this model. Resources are better spent on pricing strategy and outlet format decisions.

## Limitations & Next Steps

- The model explains 61% of sales variance - 39% is still driven by factors not captured in this dataset.

Next Steps:
-  Collecting additional data on external factors that could help explain the remaining 39% of sales variance and improve model performance
-  Exploring alternative algorithms to check whether different approaches yield better results on this dataset.
