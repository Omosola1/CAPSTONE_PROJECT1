# CAPSTONE_PROJECT1

## Project 1: Sales Performance Analysis for a Retail Store

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparations](#data-cleaning-and-preparations)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

### Project Overview
---
This Data Analysis project is set to analyze the sales performance of a retail store. It will explore sales data to uncover key insights such as top-selling products, regional 
performance, and monthly sales trends. The goal is to analyse the various parameter in the data received .Then gather enough insight to make reasonable decisions which will enable us to tell compelling stories around our data from the findings gotten and to know the best performance from our Capstone Project data.

### Data Sources
---
The Data is Capstone Project.csv and this is an open source data that can be freely downloaded from an open source online such as kaggle or FRED or any other data repository site.

### Tools Used
---
- Microsoft Excel [Download Here](https://wwwmicrosoft.com)
1. For Data Cleaning
2. For Analysis
3. For data Visualization

- SQL - Structured Query Language for Querying the data
---
SQL [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- Microsoft PowerBI for Visualisation
- Github For Portfolio Building

### Data Cleaning and Preparations
---
To achive a proper Data Cleaning and preparations, I perform the following action:
1. Data loading and Inspection
2. Handling missing variables
3. Data Cleaning and formatting

### Exploratory Data Analysis
---
EDA involves the examining the Data From the retail store in order to get some fact such as  ;

- Sales performance of the retail store
- What is the overall sales trend in the store
- Total sales by product, region, and month
- Average sales per product
- Total revenue by region
- Highest Selling Products
  
### Data Analysis
---
Here I include all basic lines of queries and some of the DAX expressions used during this analysis;

```SQL
select * from [dbo].[LITA_PROJECTA]

----- retrieve the total sales for each product category----

SELECT Product, SUM ([Total_Sales]) AS TotalSales
FROM [dbo].[LITA_PROJECTA]
GROUP BY Product

----find the number of sales transactions in each region----
SELECT Region, COUNT(OrderID) AS Number_Of_Transactions
FROM [dbo].[LITA_PROJECTA]
GROUP BY Region
ORDER BY Number_Of_Transactions DESC;

----find the highest-selling product by total sales value----

SELECT Product, SUM([Total_Sales]) AS TotalSales
FROM [dbo].[LITA_PROJECTA]
GROUP BY Product
ORDER BY TotalSales DESC; 

----calculate total Sales per product----

SELECT Product, SUM(CAST(Quantity AS INT) * CAST(UnitPrice AS DECIMAL(10, 2))) AS TotalSales
FROM [dbo].[LITA_PROJECTA]
GROUP BY Product
ORDER BY TotalSales DESC;

---- calculate monthly sales totals for the current year.---

SELECT OrderDate, SUM(Total_sales) AS monthlySales
FROM [dbo].[LITA_PROJECTA]
WHERE OrderDate between '2024-01-01' and '2024-12-31'
GROUP BY OrderDate
Order by OrderDate

----find the top 5 customers by total purchase amount----

SELECT TOP 5
    [Customer_Id], 
    SUM([Total_Sales]) AS TotalPurchase
FROM 
    [dbo].[LITA_PROJECTA]
GROUP BY 
    [Customer_Id]
ORDER BY 
    TotalPurchase DESC;

	----calculate the percentage of total sales contributed by each region----

	WITH RegionSales AS    
	(SELECT  Region, 
    SUM([Total_Sales]) AS RegionSales
    FROM [dbo].[LITA_PROJECTA]
    GROUP BY Region),
TotalSales AS (
    SELECT SUM([Total_Sales]) AS OverallTotalSales
    FROM [dbo].[LITA_PROJECTA])
SELECT 
    rs.Region,
    rs.RegionSales,
    (rs.RegionSales * 100.0 / ts.OverallTotalSales) AS PercentageOfTotalSales
FROM RegionSales rs
CROSS JOIN 
    TotalSales ts;
```

### Data Visualization                  
💹📊📉
Tables	
CHARTS




