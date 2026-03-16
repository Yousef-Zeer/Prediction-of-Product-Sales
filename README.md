# Prediction-of-Product-Sales

<p align = "center"> 
  <img src = "https://github.com/user-attachments/assets/0fe5fc53-79f9-42bb-ac92-90083372b2b0">
</p>

## Objective
The primary goal is to identify which product and store attributes play the most crucial roles in increasing sales. This insight allows retailers to optimize their inventory, marketing, and store management strategies . 

## Data Source: 
sales_predictions_2023.csv

For this dataset, there were 8523 rows and 12 columns.


## Data Dictionary

<p align = "center"> 
  <img src = "https://github.com/user-attachments/assets/b4fd8ab7-ac2a-4398-a272-6ebed3f6ff92">
</p>

## Data Preparation

Cleaned the dataset by handling missing values using group-wise imputation strategy and fixed categorical inconsistencies to ensure data integrity for modeling

## Exploratory Data Analysis

```text
- During the exploratory data analysis, a boxplot and histogram was visualized for each numeric datatype column.
- Also, a countplot and boxplot was visualized for each categorical column.

```

<img width="989" height="690" alt="Item outlet sales" src="https://github.com/user-attachments/assets/a23a05ef-5665-438f-8e35-c0bd6d9922ab" />


- Distribution of Item_Outlet_Sales is right-skewed, showing that the majority of products have relatively low sales. While there a numerous outliers on the right as boxplot shows , which represent high-performing products that significantly drive up the average sales.

### HeatMap Analysis 
<img width="932" height="731" alt="download" src="https://github.com/user-attachments/assets/dc25f0e6-ce66-4de4-8a26-69cbe6786bfb" />


- Correlation analysis revealed that Item MRP has a moderate positive impact on Outlet Sales (0.57). This suggests that pricing strategy is a key driver of total revenue.


