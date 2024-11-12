# CAPSTONE_PROJECT1

## Project 1: Sales Performance Analysis for a Retail Store

[Project Overview](#project-overview)

[Data](#data)

[Tools Used](#tools-used)

[Data Cleaning and Preparations](#data-cleaning-and-preparations)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

### Project Overview
---
This Data Analysis project is set to analyze the sales performance of a retail store. It will explore sales data to uncover key insights such as top-selling products, regional 
performance, and monthly sales trends. The goal is to analyse the various parameter in the data received .Then gather enough insight to make reasonable decisions which will enable us to tell compelling stories around our data from the findings gotten and to know the best performance from our Capstone Project data.

### Data
---
- **Data Sources**
  
  The Data is Capstone Project and this is a data that was freely downloaded from Ladies in Tech Africa (LITA) Canvas.

- **Data Summary**

   There are 7 Colomns in the dataset, which are the key indicators that give us insight into of the Sales data

  a .**Order Date**- This is the exact date when the customer placed the order.

  b. **Product** - The column lists the specific items that were purchased in the order.

  c. **Region** - The column identifies the geographical area where the order originated.

  d. **Quantity** - The Quantity column represents the number of units of a particular product that were purchased in a given order.

  e. **Unit Price** - This refers to the price of a single unit of a product. - 

  f. **Total Sales** - The column shows the total revenue generated from a specific order. It’s the result of multiplying the Quantity of the 
         product(s) by their UnitPrice.
### Tools Used
---
1. Microsoft Excel [Download Here](https://wwwmicrosoft.com)
 
 a. **For Data Cleaning**

   The Capstone Sale Data Contains '50,000' raw data, how we were left witn '9921' dataset after cleaning the data by removing the duplicates.

 b. **For Analysis**
   
   In order to give a proper data analysis of the information gotten from the dataset we explore it through:
   - By creating a New column for '**Total Sales**'. The new colomn is gotten calculated by multipy **'Quantity'** by **'Unit Price'** (UnitPrice*Quantity).
   - Average Sales per Product was calculated using '**Averageif**'.
   - Total Revenue by Region was calculated using '**Sumif**'.
     
 c. **For data Visualization**
   - Pivot table is  use to summarize 'Total sales by product', 'Total sales by region', 'Total sales by month', 'Quantity by region', 'Quantity by product' and 'Total number of product sold'.

     [LITA PROJECT1 PIVOT.xlsx](https://github.com/user-attachments/files/17630780/LITA.PROJECT1.PIVOT.xlsx)


2. SQL - Structured Query Language for Querying the data [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

   - **For Analysis**
  
 We wrote queries to extract key insights by. 
-  retrieve the total sales for each product category.
- find the number of sales transactions in each region.
- find the highest-selling product by total sales value.
- calculate total revenue per product.
- calculate monthly sales totals for the current year.
- find the top 5 customers by total purchase amount.
- calculate the percentage of total sales contributed by each region.
- identify products with no sales in the last quarter.

     ---
Here I include all basic lines of queries ;

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



3. Microsoft PowerBI for Visualisation [Download here](https://www.microsoft.com/en-us/download/details.aspx?id=58494)
 
  a. **For Data Cleaning**

   The Dataset is upload into Power BI and cleaned
   
  b. **For Analysis**
   
   In order to give a proper data analysis of the information gotten from the dataset we explore it through:

   - Creating New measures for: Average Sales, Product Count and Quantity count.
 
  c. **For data Visualization**

  - Created a dashboard that visualizes the insights found in Excel and SQL. The
     dashboard includes a sales overview, top-performing products, and 
     regional breakdown using Text box, Cards, Map, Charts and a Slicer






![PROJECT2 POWERBI](https://github.com/user-attachments/assets/b8f9b9bc-4c10-46a4-ace2-110d69c87ec3)


4. **Github For Portfolio Building ** 🗃️
  
  - Building up your portfolio as an Data Analyst

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


Data Analysis in Excel

Data Analysis in SQL

Data Analysis in Power BI

Total Sales by Product

The Analysis Shows Shoe is the highest selling product with Total Sales of  #613,380 , this is followed by Shirt being the second highest selling product. While socks remains the lowest selling product.

Highlight

Shoe and Shirt are the highest selling product which makes them the star products which is the major source of revenue to the retail store. Stock and Jacket are the lowest selling Product and the Retail store will need find a way to promote these two product in order to improve the sales 

![Uploading image.png…]()

### Data Visualization                  
💹📊📉


Data Visualization with Excel Pivot Table 

Data Visualization With Power BI


CONTACT ADDRESS:
Number 35 Olajesu street Agodo ,Ikotun. Lagos 🏠

📧
``` Email 
omo_sola@yahoo.com
```



