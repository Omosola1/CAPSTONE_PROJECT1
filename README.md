# CAPSTONE_PROJECT1

## Project 1: Sales Performance Analysis for a Retail Store

[Project Overview](#project-overview)

[Data](#data)

[Tools Used](#tools-used)

[Data Cleaning and Preparations](#data-cleaning-and-preparations)

[Exploratory Data Analysis](#exploratory-data-analysis)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

[Results and Findings](#results-and-findings)

[Recommendations](#recommendations)

[Conclusion](#conclusion)



### Project Overview
---
The goal of this project is to analyze the sales performance of a retail store using the provided sales data, uncover key insights, and create a detailed Excel report. The insights gained from this analysis will focus on important areas like top-selling products, regional performance, and monthly sales trends. Additionally, the final outcome will involve an interactive Power BI dashboard to present these findings in a dynamic, visually appealing format.

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

2. SQL - Structured Query Language for Querying the data [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)

3. Microsoft PowerBI for Visualisation [Download here](https://www.microsoft.com/en-us/download/details.aspx?id=58494)
   
 
 4. Github For Portfolio Building  🗃️
  
  - Building up your portfolio as an Data Analyst

### Data Cleaning and Preparations
---
 
 **For Data Cleaning**

To achive a proper Data Cleaning and preparations, I perform the following action:
1. Data loading and Inspection
2. Handling missing variables
3. Data Cleaning and formatting

The Capstone Sale Data Contains '50,000' raw data, how we were left witn '9921' dataset after cleaning the data by removing the duplicates.


### Exploratory Data Analysis
---
EDA involves the examining the Data From the retail store in order to get some fact.

**Excel**   
A. In order to give a proper data analysis of the information gotten from the dataset we explore it through:
   - By creating a New column for '**Total Sales**'. The new colomn is gotten calculated by multipy **'Quantity'** by **'Unit Price'** (UnitPrice*Quantity).
   - Average Sales per Product was calculated using '**Averageif**'.
   - Total Revenue by Region was calculated using '**Sumif**'.

B. We examine the Data From the retail store in order to get some fact such as  ;
- Sales performance of the retail store
- What is the overall sales trend in the store
- Total sales by product, region, and month
- Average sales per product
- Total revenue by region
- Highest Selling Products

**Power BI**
     
   In order to give a proper data analysis of the information gotten from the dataset we explore it through:

   - Creating New measures for:
     
a. Average Sales

b. Product Count

c. Quantity count.


### Data Analysis
---

The data provides total sales figures for six different product categories. Here’s an analysis of the sales distribution:

   - Pivot table is  use to summarize 'Total sales by product', 'Total sales by region', 'Total sales by month', 'Quantity by region', 'Quantity by product' and 'Total number of product sold'.


      [LITA PROJECT1 PIVOT.xlsx](https://github.com/user-attachments/files/17630780/LITA.PROJECT1.PIVOT.xlsx)



**Analysis of Total Sales by Product**

Sales Distribution:

The shoes category leads with a total of $613,380, accounting for about 29.2% of total sales.
Shirts follow with $485,600, representing 23.1% of total sales.
Hats generate $316,195, or approximately 15.1% of total sales.
Gloves contribute $296,900, or about 14.1% of total sales.
Jackets generate $208,230, or roughly 9.9% of total sales.
Socks have the smallest share with $180,785, which is 8.6% of total sales.
Sales Share Breakdown:

The top two categories, Shoes and Shirts, dominate sales, making up 52.3% of the total sales. This indicates that these categories are key revenue drivers.
The remaining categories (Hats, Gloves, Jackets, and Socks) together account for 47.7% of the total sales, with socks generating the least revenue.


**Analysis of Total Sales by Region**

The table provides total sales figures across four regions. Let’s break down the sales distribution and analyze the performance by region:

Sales Distribution:

South leads with $927,820, accounting for about 44.2% of total sales.
East follows with $485,925, representing 23.1% of total sales.
North contributes $387,000, or about 18.4% of total sales.
West has the lowest total sales at $300,345, which is 14.3% of the total sales.
Regional Share Breakdown:

South dominates the sales with nearly half of the total sales (44.2%), making it by far the most important region.
The East region contributes a significant share (23.1%), while North (18.4%) and West (14.3%) both have comparatively lower shares. 

**Analysis of Total Sales by Month**

The table shows total sales by month, and we can observe clear patterns and trends over the year. Let’s break down the sales distribution and highlight key insights.

Sales Distribution by Month:

Top Performers:

February leads with $546,300, accounting for 26.0% of total sales.
July follows with $274,800, contributing 13.1% of total sales.
January comes next with $248,000, representing 11.8% of total sales.
June also performs strongly, generating $247,600, or 11.8% of total sales.

Lowest Performers:

September has the smallest sales at $34,720, contributing just 1.7% of total sales.
December follows closely behind with $49,300, or 2.3% of total sales.
April and March also underperform, generating $46,865 and $107,175, respectively.




**SQL**

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




Data Analysis in Power BI

### Data Visualization                  
💹📊📉


Data Visualization with Excel Pivot Table 

Data Visualization With Power BI

  - Created a dashboard that visualizes the insights found in Excel and SQL. The
     dashboard includes a sales overview, top-performing products, and 
     regional breakdown using Text box, Cards, Map, Charts and a Slicer




![PROJECT2 POWERBI](https://github.com/user-attachments/assets/b8f9b9bc-4c10-46a4-ace2-110d69c87ec3)






### Results and Findings

 **Total Sales by Product**
 
Shoes are the standout performer, with nearly twice the sales of Shirts and more than twice the sales of Hats and Gloves. This suggests a strong demand or larger price point for shoes, or potentially greater marketing success.
Socks have the lowest total sales, which may indicate lower customer interest, lower margins, or possibly a seasonal variation in demand.
There is a general pattern where the higher-ticket items (Shoes, Shirts) perform better, while lower-ticket items like Jackets and Socks see reduced demand.

**Total Sales by Region**

The South region is the clear leader in total sales, contributing almost twice as much as the East region and significantly more than the North and West regions. This could be due to stronger demand, a larger customer base, or effective marketing in the South.
West region has the smallest share of total sales, which could indicate lower market penetration, fewer sales opportunities, or less effective marketing strategies in that region.
North and West regions have similar shares, but both trail far behind the South and East regions, indicating potential for improvement in these regions.

**Total Sales by Month**
February stands out as the highest-performing month, with nearly half a million dollars in sales. This could indicate a strong seasonal boost or a key marketing campaign running during this period.
The months of July, January, and June all show solid sales figures, with these four months (Feb, Jul, Jan, Jun) accounting for over 60% of the total sales.
September, December, April, and March show very weak sales, especially in September and December, which likely indicate lower sales during these months.
August and October show a slight dip in sales compared to the earlier months but still contribute a reasonable amount to total sales.

### Recommendations

Socks have the lowest sales, and it may be worth investigating why they are underperforming. Are the prices too high? Is there sufficient variety or novelty? Consider conducting customer surveys or testing promotions to understand the reasons.
Similarly, Jackets are underperforming compared to other products, and their sales could be seasonally affected. Consider bundling jackets with other products (like shirts) or launching targeted campaigns during colder seasons.

The South region is performing strongly and represents nearly half of the total sales. It would be prudent to maintain and strengthen your efforts in this region. Consider increasing marketing spend, launching exclusive promotions, or expanding your product range to continue capitalizing on this success.
Evaluate what is driving sales in the South—whether it’s specific products, promotions, or customer demographics—and look for ways to replicate this success in other regions.
    
### Conclusion

While Shoes and Shirts are clearly the dominant product categories driving the business, there is room to improve the performance of Jackets and Socks through targeted promotions, innovation, and better customer understanding. Consider focusing on strengthening the high-performing categories while exploring ways to stimulate interest in underperforming products, especially in seasonally relevant markets.

The South region is clearly the strongest performer, driving nearly half of the total sales, and should continue to be a key focus for marketing and expansion. However, there’s significant opportunity to improve performance in the West and North regions through tailored strategies, such as localized promotions, better market understanding, and increased customer engagement. By optimizing regional strategies, you can ensure a more balanced performance across all regions and capture untapped potential in the underperforming markets.
