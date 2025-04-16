# 🛠️ Project 1: Retail Sales Pipeline

## 🌟 Overview

Welcome to **ML Data Pipeline**, where you’ll build an end-to-end SQL pipeline to clean, transform, and query retail sales data for ML model training! This project weaves together *DQL* for querying, *DML* for updates, *Joins* for merging, and *Indexing* for speed, preparing a clean dataset for customer purchase predictions. Perfect for your *ML-Interview-Preparation-Hub* portfolio! 🚀

## 📊 Project Details

- **Scenario**: You’re a data engineer at an e-commerce company. Your task is to process raw `sales` and `customers` data, clean inconsistencies, merge datasets, and create a feature table for an ML model predicting customer purchases.
- **Goals**: Clean data, join tables, optimize queries, and export a CSV.
- **SQL Skills**: *DQL* (SELECT), *DML* (UPDATE, INSERT), *Joins* (INNER, LEFT), *Indexing*.

## 📋 Tasks

1. Create `sales` (`sale_id INT, customer_id INT, amount FLOAT, sale_date DATE, product VARCHAR`) and `customers` (`customer_id INT, region VARCHAR`) tables.
2. Insert sample data (e.g., 10 sales, 5 customers).
3. Clean `sales` by setting negative `amount` to 0 using *DML*.
4. Join `sales` and `customers` to create a feature table with *Joins*.
5. Add an index on `customer_id` for faster joins.
6. Query total sales per region for ML features using *DQL*.
7. Export results to a CSV for portfolio use.

## 💻 Sample Solution

```sql
-- Task 1: Create Tables
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    region VARCHAR(50)
);
CREATE TABLE sales (
    sale_id INT PRIMARY KEY,
    customer_id INT,
    amount FLOAT,
    sale_date DATE,
    product VARCHAR(50),
    FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);

-- Task 2: Insert Sample Data
INSERT INTO customers VALUES
(1, 'North'), (2, 'South'), (3, 'East'), (4, 'West'), (5, 'North');
INSERT INTO sales VALUES
(1, 1, 100.0, '2025-04-01', 'Laptop'),
(2, 2, -50.0, '2025-04-02', 'Phone'),
(3, 3, 200.0, '2025-04-03', 'Tablet'),
(4, 1, 150.0, '2025-04-04', 'Laptop'),
(5, 4, -20.0, '2025-04-05', 'Phone'),
(6, 2, 300.0, '2025-04-06', 'Tablet'),
(7, 5, 400.0, '2025-04-07', 'Laptop'),
(8, 3, -10.0, '2025-04-08', 'Phone'),
(9, 4, 250.0, '2025-04-09', 'Tablet'),
(10, 5, 180.0, '2025-04-10', 'Laptop');

-- Task 3: Clean Data
UPDATE sales
SET amount = 0
WHERE amount < 0;

-- Task 4: Join Tables
CREATE TABLE sales_features AS
SELECT s.sale_id, s.customer_id, s.amount, s.sale_date, s.product, c.region
FROM sales s
INNER JOIN customers c ON s.customer_id = c.customer_id;

-- Task 5: Add Index
CREATE INDEX idx_customer_id ON sales(customer_id);

-- Task 6: Query Features
SELECT c.region, COUNT(s.sale_id) AS sale_count, SUM(s.amount) AS total_amount
FROM sales s
JOIN customers c ON s.customer_id = c.customer_id
GROUP BY c.region;

-- Task 7: Export (Pseudo-code, depends on DB tool)
-- COPY (SELECT ...) TO 'sales_features.csv' WITH CSV HEADER;
```

**Explanation**:
- *DDL* creates tables with constraints.
- *DML* inserts data and fixes negative amounts.
- *Joins* merge sales and customer data.
- *Indexing* speeds up joins.
- *DQL* aggregates for ML features, grouping by region.

## 🎯 Expected Outcome

- A `sales_features` table with cleaned, joined data.
- A CSV file (`sales_features.csv`) with regional sales metrics.
- A portfolio-ready dataset showcasing data prep for ML.

## 💼 Portfolio Tips

- Add `sales_features.csv` to `irohanportfolio.netlify.app`.
- Write a README explaining the pipeline and ML use (e.g., customer purchase prediction).
- Visualize with Python’s `seaborn` (e.g., bar plot of sales by region).
- Tag skills: *DQL*, *DML*, *Joins*, *Indexing*.

## 🔥 Challenge

Extend the pipeline by adding a *Window Function* to rank sales per customer within each region.

---