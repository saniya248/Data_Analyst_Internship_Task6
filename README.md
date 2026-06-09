# Data_Analyst_Inte# Data Analyst Internship - Task 6: Sales Trend Analysis Using Aggregations

## 📌 Project Objective
The goal of this task is to analyze monthly revenue and order volume using SQL aggregation functions, group the data by specific time periods (Year/Month), and sort the trends chronologically.

## 🛠️ Tools Used
- **Database Engine:** MySQL
- **Interface:** MySQL Workbench

## 📝 SQL Script Developed
```sql
-- 1. Database Creation
CREATE DATABASE IF NOT EXISTS internship_tasks;
USE internship_tasks;

-- 2. Table Creation
CREATE TABLE IF NOT EXISTS online_sales (
    order_id INT,
    order_date DATE,
    amount DECIMAL(10, 2),
    product_id INT
);

-- 3. Inserting Mock Dataset
INSERT INTO online_sales (order_id, order_date, amount, product_id) VALUES
(101, '2026-01-10', 150.00, 1),
(102, '2026-01-15', 200.00, 2),
(103, '2026-02-05', 350.00, 1),
(104, '2026-02-20', 120.00, 3),
(105, '2026-03-01', 500.00, 2),
(106, '2026-03-15', 250.00, 1);

-- 4. Final Aggregation Query (Sales Trend Analysis)
SELECT 
    YEAR(order_date) AS `Year`,
    EXTRACT(MONTH FROM order_date) AS `Month`,
    SUM(amount) AS `Revenue`,
    COUNT(DISTINCT order_id) AS `Order Volume`
FROM 
    online_sales
GROUP BY 
    YEAR(order_date),
    EXTRACT(MONTH FROM order_date)
ORDER BY 
    `Year` ASC, 
    `Month` ASC;rnship 
