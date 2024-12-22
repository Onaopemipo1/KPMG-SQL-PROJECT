# KPMG-SQL-PROJECT
This is a project which contains a SQL work. This SQL Work was done using a dataset that was gotten from Forage using the KPMG. I used Queries to extract some dataset needed for analysis which would help solve questions that would be beneficial to the company. 

## Table Of Content
1.0 - Introduction

2.0 - Data Source

3.0 - Tools Used

4.0 - Data Transformation

5.0 - Data Visualization

## 1.0 - Introduction
This is a project where i was able to query the dataset to get insights that would help me gather some key metrics. This was a personal project i took upon myself to pratice my SQL Skills. 

## 2.0 
The Data Source was provided by Forage under the KPMG Data Analysis tasks. It was in a CSV Format. 

## 3.0 Tools Used
3.1 - Microsoft Excel [Download Here](www.microsoft.com)

3.2 - Microsoft PowerBi [Download Here](https;//app.powerbi.com/)

3.3 - MySQL [Download Here](https://www.mysql.com/)

## 4.0 Data Transformation
Using MySQL i used some queires to extract data which was necessary to answer the data questions. 

```sql
create database kpmg;
show databases;
use kpmg;
show tables;
-- Select all data from the company dataset
select * from company;

-- Introducing a new case function for the product quantity category
select store, region, product_item_id, product_item_category, product_item_quantity, product_item_price, revenue, cost_of_goods_sold, payment_method, Profit,
case
when product_item_quantity <= 3 then "Low"
when product_item_quantity between 4 and 7 then "Medium" 
when product_item_quantity > 7 then "High"
end as Product_category
from company;

/* I queried the dataset to get which the total revenue generated,
 total profit generated, count the unique product categories sold
 to check the minimum revenue generated in the period,
 check the number of unique stores, unique regions that the company operated in,
 check the total cost of goods sold,
*/
select * from company where product_item_category = "Meat & Fish";
select sum(revenue) as total_revenue from company;
select sum(profit) as total_profit from company;
select count(distinct product_item_category) as total_category from company;
select min(revenue) as min_revenue from company;
select count(distinct store) as total_store, count(distinct region) as total_region, count(distinct product_item_category) as total_category from company;
select count(region) from company;
select sum(cost_of_goods_sold) as total_cogs from company;

/* I queried the data to check the profit made in descending order,
Checked a specific product category in a particular region which was in the north region,
the specific category checked was also alcohol. 
I also queried the data to check the payment method which was cash and also did an order by using Profit Descending. 
Finally, i used the like function to also check product item category that had C in it.
*/

select * from company order by Profit desc;
select * from company where region = "North" and product_item_category = "Alcohol";
select * from company where payment_method = "Cash" order by Profit desc;
select * from company where store in ("Lancaster","Liverpool","Cornwall") order by revenue desc;
select product_item_category, Profit from company where product_item_category like "%C%"; 
```
After using SQL to Query, i exported the data extracted to excel using csv format

## 5.0 Data Visualization.
Having used the SQL to Query the Dataset and using Excel to crosscheck. I loaded the dataset to PowerBi. The results gotten can be seen in the daahboard below.
![](KPMG.PNG)
