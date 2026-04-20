# Pizza-Sales-Dashboard-SQL-Power-BI-Project-3
The Pizza Sales Dashboard is designed to help stakeholders monitor key performance indicators (KPIs) and identify growth opportunities. The project involves extracting data from a SQL database, performing complex transformations, and building an interactive dashboard to visualize sales dynamics.
📊 Key Performance Indicators (KPIs)
The dashboard successfully calculates and tracks the requested core metrics:
Key Performance Indicators (KPIs)
A. KPI’s
Total Revenue:

SQL Query: SELECT SUM(total_price) AS Total_Revenue FROM pizza_sales;
Average Order Value:

SQL Query: SELECT (SUM(total_price) / COUNT(DISTINCT order_id)) AS Avg_order_Value FROM pizza_sales
Total Pizzas Sold:

SQL Query: SELECT SUM(quantity) AS Total_pizza_sold FROM pizza_sales
Total Orders:

SQL Query: SELECT COUNT(DISTINCT order_id) AS Total_Orders FROM pizza_sales
Average Pizzas Per Order:

SQL Query:
SELECT CAST(CAST(SUM(quantity) AS DECIMAL(10,2)) / 
CAST(COUNT(DISTINCT order_id) AS DECIMAL(10,2)) AS DECIMAL(10,2))
AS Avg_Pizzas_per_order
FROM pizza_sales

B. Daily Trend for Total Orders
SQL Query:
SELECT DATENAME(DW, order_date) AS order_day, COUNT(DISTINCT order_id) AS total_orders 
FROM pizza_sales
GROUP BY DATENAME(DW, order_date)

C. Monthly Trend for Orders
SQL Query:
SELECT DATENAME(MONTH, order_date) as Month_Name, COUNT(DISTINCT order_id) as Total_Orders
FROM pizza_sales
GROUP BY DATENAME(MONTH, order_date)

D. % of Sales by Pizza Category
SQL Query:
SELECT pizza_category, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_category

E. % of Sales by Pizza Size
SQL Query:
SELECT pizza_size, CAST(SUM(total_price) AS DECIMAL(10,2)) as total_revenue,
CAST(SUM(total_price) * 100 / (SELECT SUM(total_price) from pizza_sales) AS DECIMAL(10,2)) AS PCT
FROM pizza_sales
GROUP BY pizza_size
ORDER BY pizza_size

Top and Bottom Performers

F. Total Pizzas Sold by Pizza Category
SQL Query:
SELECT pizza_category, SUM(quantity) as Total_Quantity_Sold
FROM pizza_sales
WHERE MONTH(order_date) = 2
GROUP BY pizza_category
ORDER BY Total_Quantity_Sold DESC

G. Top 5 Pizzas by Revenue
SQL Query:
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue DESC

H. Bottom 5 Pizzas by Revenue
SQL Query:
SELECT Top 5 pizza_name, SUM(total_price) AS Total_Revenue
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Revenue ASC

I. Top 5 Pizzas by Quantity
SQL Query:
SELECT Top 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold DESC

J. Bottom 5 Pizzas by Quantity
SQL Query:
SELECT TOP 5 pizza_name, SUM(quantity) AS Total_Pizza_Sold
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Pizza_Sold ASC

K. Top 5 Pizzas by Total Orders
SQL Query:
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders DESC

L. Bottom 5 Pizzas by Total Orders
SQL Query:
SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
GROUP BY pizza_name
ORDER BY Total_Orders ASC

Applying Filters
If you want to apply filters to the above queries, you can use the WHERE clause in SQL. For example:

SELECT Top 5 pizza_name, COUNT(DISTINCT order_id) AS Total_Orders
FROM pizza_sales
WHERE pizza_category = 'Classic'
GROUP BY pizza_name
ORDER BY Total_Orders ASC

Feel free to explore and customize the report based on your specific requirements!
<img width="590" height="329" alt="pizza sales project-power Bi reports" src="https://github.com/user-attachments/assets/f7d8c36b-2b70-4387-9ddf-7005ca1ba85d" />
<img width="593" height="335" alt="pizza sales project-power Bi reports-2" src="https://github.com/user-attachments/assets/772460b8-c11e-4413-b38c-acfbdec84d24" />


