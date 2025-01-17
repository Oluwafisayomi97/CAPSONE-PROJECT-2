# CAPSONE-PROJECT-2

## Project Title: Customer Segmentation For a Subscription Service Summary

## Project Summary
This project focuses on analyzing customer data from a subscription-based service to identify key segments and trends. The primary goal is to understand customer behavior, track subscription types, and uncover patterns related to cancellations and renewals. 

## The Data Sources
---
The data sources include: 
•CustomerID: Unique identifier for each customer.

•CustomerName: Name of the customer

•Region: Geographical area where the customer is located (e.g., North, South, East, West)

•SubscriptionType: Type of subscription plan the customer is enrolled in (Basic, Premium and standard)

•SubscriptionStart: Start date of the customer's subscription

•SubscriptionEnd: End date of the customer's subscription

•Canceled: Indicates if the subscription was canceled (TRUE or FALSE)

•Revenue: Revenue generated from the customer's subscription

•Subscription Duration: Duration of the subscription period

## The Data Tools Used
---
•	Microsoft Excel: Excel was used for initial data exploration, cleaning, and basic analysis. Pivot tables and formulas were applied to calculate metrics like average sales 
  per product and total revenue by region.• The Microsoft Excel was used to removed eliminate records to ensure data accuracy. 
 The microsoft Excel functions (SUM, COUNT, AVERAGE, AVERAGEIF, AND SUMIF) for statistical calculations like total revenue, and average revenue.
 Creating a New Calculated Columns: I added a new sales column to calculate the sum of unit price and quantity [Download here](http://www.microsoft.com)
  
•	SQL: SQL was employed to load and query the dataset within a SQL Server environment. This allowed for more advanced analysis, such as calculating total revenue per 
  product, identifying top-performing products, and analyzing sales trends. SQL also enabled efficient filtering and grouping to derive insights from large volumes of data.
  
•	Power BI: Power BI was used to create an interactive dashboard that visually represents the insights obtained from Excel and SQL analyses. The dashboard includes 
  components like a subcription trends, average subscription duration, popular subscription type.
  
•	Github: for portfolio building

## Exploratory Data Analysis
---
Exploratory data analysis invoved explorying the data to answer some of the question, needful for the data such as;
---
•  What is the total number of customers from each region?

•  Find the most popular subscription type by the number of customers. 

•  Find customers who canceled their subscription within 6 months. 

•  Calculate the average subscription duration for all customers.

•  Find customers with subscriptions longer than 12 months. 

•  Calculate total revenue by subscription type. 

•  Find the top 3 regions by subscription cancellations. 

•  Find the total number of active and canceled subscriptions.

## Data Analysis 

```SQL
Select * from [dbo].[CUSTOMER DATA]
```

SELECT Region, COUNT(DISTINCT CustomerID) AS total_customers
FROM [dbo].[CUSTOMER DATA]
GROUP BY Region;

SELECT TOP 1 SubscriptionType, COUNT(CustomerID) AS CustomerCount
FROM [dbo].[CUSTOMER DATA]
GROUP BY SubscriptionType
ORDER BY CustomerCount DESC;

SELECT DISTINCT
CustomerID AS Cancelled_Subscription,CustomerName, Region,SubscriptionType
FROM [dbo].[CUSTOMER DATA]
WHERE canceled = 'true';

SELECT AVG(DATEDIFF(DAY, SubscriptionStart, SubscriptionEnd))
AS AvgSubscriptionDuration
FROM [dbo].[CUSTOMER DATA]

SELECT CustomerID,CustomerName,Region, SubscriptionType
FROM [dbo].[CUSTOMER DATA]
WHERE DATEDIFF(MONTH, SubscriptionStart, ISNULL(SubscriptionEnd, GETDATE())) > 12;

SELECT SubscriptionType, SUM(Revenue) AS TotalRevenue
FROM [dbo].[CUSTOMER DATA]
GROUP BY SubscriptionType;

DECLARE @limit INT = 3;  
SELECT TOP (@limit) region, COUNT(Revenue) AS canceled_count
FROM[dbo].[CUSTOMER DATA]
WHERE canceled IS NOT NULL  
GROUP BY region
ORDER BY COUNT(Revenue) DESC;

SELECT Count(*) as canceledsubscription from [dbo].[CUSTOMER DATA]
where canceled =1

SELECT Count(*) as activesubscription from [dbo].[CUSTOMER DATA]
where canceled =0


## The pivot table below shows the summaarization of the customer sales data.
[image](https://github.com/user-attachments/assets/9a9ef50d-de4b-4e6c-98a5-5ec49ec6e0c0)


## Data Visualization
The customer dashboard report visualization
[image](https://github.com/user-attachments/assets/0b32f703-ee5d-4a0d-b89e-0a3d44f34624)


The Donut chart shows the percentage average revenue by each region
[image](https://github.com/user-attachments/assets/84b33b9b-8df2-460d-aa72-d8ab77cd31ed)


The line chart shows the count of region by the subcsription type
[image](https://github.com/user-attachments/assets/d40df1df-3f6b-45c2-b991-96078ad300e9)




