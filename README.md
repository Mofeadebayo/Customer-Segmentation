# LITA Capstone Dataset

### Project title: Customer Segmentation

[Project Overview](#project-overview)

[Data Sources](#data-sources)

[Tools Used](#tools-used)

[Data Cleaning and Preparation](#data-cleaning-and-preparation)

[Data Analysis](#data-analysis)

[Data Visualization](#data-visualization)

### Project Overview
This Customer segmentation project aims to generate insights into sales performance of the E commerce project over the past years. By analyzing the various parameters in the data received we seek to gather enough insights to make reasonable decisions which then enable us to tell compelling stories around our data from the insight gotten and to know the best performance fromn our data.

### Data Sources
The primary source of data used here is LITA Capstone Dataset.xslx and this is an open source data that can be freely downloaded from an open source online such as kaggle or FRED or any other data repository site.

### Tools Used
- Microsoft Excel [Download Here](https://www.microsoft.com)
  1. For Data Cleaning,
  2. For For Data Analysis and
  3. For Data Visualization

- SQL - Structured Query Language for Querying of Data [Download Here](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
- GitHub for Portfolio Building [Download Here](https://github.com/apps/desktop)

### Data Cleaning and Preparation
In the initial phase of bthe Data cleaning and preparations, we perform the following actions:
1. Data loading and Inspection
2. Handling missing variables
3. Data cleaning and formatting.

Explorative Data Analysis
EDA involves the exploring of the data to answer some questions about the data such as:
- What is the overall customer segmentation?
- Which region has the most sales?
- Which seller has the most revenue?
- Whaich products are on peak sales?

### Data Analysis
This is where we include some basic lines of codes or queries or even some of the DAX expressions used during your analysis;

```SQL
SELECT * FROM TABLE1
WHERE CONDITION = TRUE
```

### Data Visualization
[Uploading SQLQuery lituse [LITA PROJECT]

--select * from dbo.SalesData

--RETRIEVE THE TOTAL SALES FOR EACH PRODUCT CATEGORY
select product, sum(TotalSales) as Total_Sales
from dbo.SalesData
group by product


--FIND THE NUMBER OF SALES TRANSACTIONS IN EACH REGION
select Region, count(TotalSales) as Sales_Transaction
from dbo.SalesData
group by Region

--FIND THE HIGHEST SELLING PRODUCT BY TOTAL SALES
select Product, max(TotalSales) as Total_Sales
from dbo.SalesData
group by Product
order by Total_Sales desc


--CALCULATE TOTAL REVENUE PER PRODUCT
select Product, SUM(TotalSales) as Revenue
from dbo.SalesData
group by Product


--CALCULATE MONTHLY SALES TOTALS FOR THE CURRENT YEAR
select  DATENAME(MONTH, OrderDate) as Months, sum(TotalSales) as Total_Sales
from SalesData
where YEAR(OrderDate) = 2024
group by DATENAME(MONTH, OrderDate)
order by Total_Sales desc


--FIND THE TOP 5 CUSTOMERS BY TOTAL PURCHASE AMOUNT
select Top 5 Customer_Id, sum(TotalSales) as Total_Purchase 
from SalesData
group by Customer_Id
order by Customer_Id desc


--CALCULATE THE PERCENTAGE OF TOTAL SALES CONTRIBUTION BY EACH REGION
select Region, sum(TotalSales) as [Total Sales], sum(TotalSales)*100 / (select (sum(TotalSales)) from SalesData) as [Percentage%] 
from SalesData
group by Region


---IDENTIFY PRODUCTS WITH NO SALES IN THE LAST QUARTER
SELECT PRODUCT FROM SalesData
WHERE OrderDate<DATEADD(QUARTER, -1, GETDATE())
GROUP BY Product
HAVING SUM(Quantity)=0



---PROJECT 2: CUSTOMER DATA

select * from CustomerData

--RETRIEVE THE TOTAL NUMBER OF CUSTOMERS FROM EACH REGION
select Region, count(CustomerID) as Customers from CustomerData
group by Region


--FIND THE MOST POPULAR SUBSCRIPTION TYPE BY CUSTOMERS
select SubscriptionType, count( DISTINCT CustomerID ) as Customers
from CustomerData
group by SubscriptionType


--FIND CUSTOMERS WHO CANCELED THEIR SUBCRIPTION
SELect CustomerID, Datename(MONTH, SubscriptionStart) as Subcription_Month, count(Canceled) as Canceled
from CustomerData
where Canceled = 'True' 
group by Datename(MONTH, SubscriptionStart), CustomerID
order by Subcription_Month


--CALCULATE THE AVERAGE SUBSCRIPTION DURATION FOR ALL CUSTOMERS
SELECT CustomerID, AVG(DATEDIFF(MONTH, SubscriptionStart, SubscriptionEnd)) as Avg_Subscription 
from CustomerData
GROUP BY CustomerID

--FIND CUSTOMERS WITH SUBSCRIPTION LONGER THAN 12 MONTHS
select CustomerID, DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd) AS DURATION 
from CustomerData
WHERE DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd) >=366


--CALCULATE TOTAT REVENUE BY SUBSCRIPTION TYPE
SELECT SubscriptionType, SUM(REVENUE) AS TOTAL_REVENUE  FROM CustomerData
GROUP BY SubscriptionType


--FIND THE TOP 3 REGIONS BY SUBCRIPTION CANCELLATIONS
SELECT TOP 3 REGION, COUNT(CANCELED) AS [TOP 3] FROM CustomerData
WHERE Canceled ='TRUE'
GROUP BY Region
ORDER BY [TOP 3] DESC

--FIND THE TOTAL NUMBER OF ACTIVE AND CANCELED SUBSCRIPTION
SELECT SubscriptionType, COUNT(CANCELED) AS CANCELED FROM CustomerData
WHERE Canceled ='TRUE' 
GROUP BY SubscriptionType


SELECT SubscriptionType, COUNT(CANCELED) AS ACTIVE FROM CustomerData
WHERE Canceled ='FALSE' 
GROUP BY SubscriptionType

a project.sql…]()


![CUSTOMER SEGMENTS SNAPSHOT](https://github.com/user-attachments/assets/7d966fd9-8adc-445b-946d-4dc5bc90c86e)

![SALES PERFORMANCE OVERVIEW](https://github.com/user-attachments/assets/e3700d77-9df9-4bab-9805-1ab6b9fe9b9b)

🥇
