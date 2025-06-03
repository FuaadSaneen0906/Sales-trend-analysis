# Sales-trend-analysis

use data_analysis;
select * from sales;
select count(*) from sales;
#total sales
     SELECT SUM(`Total Revenue`) AS TotalSales FROM sales;
     
#Revenue by product category
SELECT `Product Category`, SUM(`Total Revenue`) AS TotalAmount
FROM sales
GROUP BY `Product Category`
ORDER BY TotalAmount DESC;

#Sales Trend Analysis
SELECT `Date`, SUM(`Total Revenue`) AS TotalAmount
FROM sales
GROUP BY `Date`
ORDER BY `Date`;

#Seasonality Analysis
SELECT MONTH(STR_TO_DATE(`Date`, '%Y-%m-%d')) AS SaleMonth,
       SUM(`Total Revenue`) AS TotalAmount
FROM sales
GROUP BY SaleMonth
ORDER BY SaleMonth;

#Top 3 month of sales
SELECT 
  MONTH(STR_TO_DATE(`Date`, '%Y-%m-%d')) AS SaleMonth,
  SUM(`Total Revenue`) AS TotalAmount
FROM sales
GROUP BY SaleMonth
ORDER BY TotalAmount DESC
LIMIT 3;
