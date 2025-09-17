# Sales Analysis-Dashboard

### Dashboard Link : https://app.powerbi.com/groups/me/reports/f4638b62-a5d3-4a2e-8752-228fef62563f/2780ac2f96b94735cab2?experience=power-bi

## Problem Statement

Electro Hub is an offline retail store selling products across multiple categories like Electronics, Clothing, Footwear, and more. The goal of this project is to build an interactive Power BI dashboard that transforms raw sales data into actionable insights.

The dashboard helps:

- Identify top & bottom products by sales, profit, and quantity.

- Track sales trends over time (daily, monthly, yearly).

- Analyze the relationship between sales and profit.

- Compare performance across two time periods.

- Evaluate average discounts by category.

- Show sales by city and overall KPIs like orders, profit, and net sales.

This analysis enables Electro Hub to optimize product strategies, promotions, inventory, and city-wise operations, turning offline sales data into data-driven decisions.


### Steps followed 

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
        
- Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.
- Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".
- Step 4 : Change the Data Type of each column based of the type of values it contains .
- Step 5 : New column i.e. Price_per_unit was add in the fact table using merge operation and kept the data type as whole number.
- Step 6 : Adding new column "Total_sales" to the transactions_table.

        Total_Sales = unit_sold * Price_per_unit
- Step 7 : Adding new column "Discount_percentage" using Merge operation.

 <img width="168" height="262" alt="Discount Percentage" src="https://github.com/user-attachments/assets/cfe6df4f-6523-42b1-b64c-e1f09b9a5b21" />

- Step 8 : Create new column "Discount".

        Discount = (Total_Sales * Discount_percentage) /100
- Step 9 : Add new column Net_Sales in the transactions_table.

        Net_Sales = Total_Sales - Discount
- Step 10 : relationship between all tables was created using Data Modelling.

In our dataset, Some parameters were assigned value 0, in the Promotions_table representing those parameters are not applicable for some customers.


- Step 11 : Created report page named "Overview" to visualize following insights,

        - Sales Trend by periods
        - Sales by city 
        - Average Discount Per promotion category
        - Profit Vs Net Sales
        - Total Orders
- Step 12 : In the report view, create another page to visualize Top/Bottom 5 Products by, Sales, Profit, & unit_sold. 
- Step 13 : In the report view, new report page for alanyzing the dataset by create table visual and slicers.  

## DAX Requirements


      1). Total Net Sales = 

        CALCULATE(SUM(Transactions[Net Sales]),
        ALL('Date Table 1'),
        USERELATIONSHIP('Date Table 2'[Date],Transactions[Date (dd/mm/yyyy)]))

       2).  Total Profit = 
       
            CALCULATE(SUM(Transactions[Profit ]),
            ALL('Date Table 1'[Date]),
            USERELATIONSHIP('Date Table 2'[Date],Transactions[Date (dd/mm/yyyy)]))

        3). Total Quantity = 
        
        CALCULATE(SUM(Transactions[Units Sold]),
        ALL('Date Table 1'[Date]),
        USERELATIONSHIP('Date Table 2'[Date],Transactions[Date (dd/mm/yyyy)]))

         4). total_amnt = SUM('Transactions'[Net Sales]) 

        
- Step 14 : A card visual was used to count total orders.

<img width="302" height="106" alt="Total Orders" src="https://github.com/user-attachments/assets/84388755-6072-4ee2-aa72-cdf6ee06e5bb" />

 
 - Step 15 : The report was then published to Power BI Service.
 
 

# Snapshot of Dashboard 
## Overview

<img width="1366" height="667" alt="Snap" src="https://github.com/user-attachments/assets/027aabe0-1404-4884-b938-d32219ad8353" />

## Top/Bottom 5 Products

<img width="1360" height="644" alt="Top" src="https://github.com/user-attachments/assets/fd1e7f82-0345-4cb7-af17-6af2134a82f5" />

## Sales/Profit/Quantity - Edit Interaction

<img width="1365" height="641" alt="page3" src="https://github.com/user-attachments/assets/82196130-f3f6-4f99-b9f9-d23a1b6f3cf5" />

## Table Summary

<img width="1363" height="647" alt="page 4" src="https://github.com/user-attachments/assets/9a996f26-5e40-48f9-8d81-54b5ed98e525" />



# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

### [1] Overall Sales Performance:

  - A total of 3,510 orders were recorded across different product categories.

- Sales show consistent activity from 2020 to 2024, with noticeable spikes during promotional periods.

           
### [2] Top & Bottom Performing Products:
  -  Apple iPhone 14, HP Pavilion Laptop, Samsung Galaxy S21, Apple MacBook Air, Sony Bravia 55” TV are top products by sales and profit.
  - Tupperware Lunch Box, L’Oreal Shampoo, Nivea Body Lotion, Dove Soap Pack, Colgate Toothpaste were among the lowest in sales and profit, indicating low customer traction.
  
  
  ### [3] Profit vs. Net Sales Relationship:
- A strong positive correlation exists between profit and net sales, showing that higher sales generally translate into higher profitability.

- However, some categories with high sales showed lower margins, suggesting the need for pricing and discount strategy reviews.

 ### [4] Discount Analysis:
 - Weekend Flash Sale and Clearance Sale had the highest average discounts.
 - Festive Diwali and New Year Special contributed less in terms of average discount.
 
 ### [5] Geographic Insights:
- Major cities like Delhi, Mumbai, Bangalore, Hyderabad, and Chennai contributed significantly to sales.

- Regional variations suggest potential for city-specific campaigns and localized promotions.
 
 ###  [6] Business Implications:
 
- Focus marketing efforts and promotions on top-performing products to maximize revenue.

- Reevaluate strategy for low-performing SKUs (e.g., personal care items) — consider bundling, repositioning, or phasing out.

- Optimize discounting by focusing on categories where promotions boost profit rather than erode margins.

- Leverage strong sales in metropolitan areas while designing strategies to expand reach in underperforming cities.
         
