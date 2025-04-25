# SQL Interview Questions for AI/ML Roles

## Data Query Language (DQL)

### Basic
1. **Write a query to retrieve all records from a `products` table where the price is above 100.**  
   Filters high-value products for customer segmentation models.  
   ```sql
   SELECT *
   FROM products
   WHERE price > 100;
   ```

2. **Use DISTINCT to find unique customer IDs from an `orders` table.**  
   Identifies unique users for user-based feature engineering.  
   ```sql
   SELECT DISTINCT customer_id
   FROM orders;
   ```

3. **Write a query using LIKE to find customers with email addresses ending in '@gmail.com'.**  
   Extracts specific user groups for targeted analysis.  
   ```sql
   SELECT *
   FROM customers
   WHERE email LIKE '%@gmail.com';
   ```

4. **Use the IN operator to select orders from specific regions ('North', 'South', 'West').**  
   Filters regional data for geographically segmented models.  
   ```sql
   SELECT *
   FROM orders
   WHERE region IN ('North', 'South', 'West');
   ```

### Intermediate
5. **Write a query to sort customers by total purchase amount in descending order, limiting to the top 10.**  
   Ranks customers for high-value targeting in recommendation systems.  
   ```sql
   SELECT customer_id, SUM(order_amount) AS total_purchase
   FROM orders
   GROUP BY customer_id
   ORDER BY total_purchase DESC
   LIMIT 10;
   ```

6. **Use BETWEEN to find transactions occurring in Q1 2023.**  
   Extracts time-specific data for temporal analysis.  
   ```sql
   SELECT *
   FROM transactions
   WHERE transaction_date BETWEEN '2023-01-01' AND '2023-03-31';
   ```

7. **Write a query with a CASE statement to categorize products as 'Cheap' (< $50), 'Moderate' ($50-$200), or 'Expensive' (> $200).**  
   Creates categorical features for price-based modeling.  
   ```sql
   SELECT product_name,
          CASE
              WHEN price < 50 THEN 'Cheap'
              WHEN price BETWEEN 50 AND 200 THEN 'Moderate'
              ELSE 'Expensive'
          END AS price_category
   FROM products;
   ```

8. **Use COALESCE to replace NULL values in a `customer_rating` column with 0.**  
   Handles missing data for clean model inputs.  
   ```sql
   SELECT customer_id, COALESCE(customer_rating, 0) AS rating
   FROM customers;
   ```

### Advanced
9. **Write a correlated subquery to find employees earning more than their department’s average salary.**  
   Identifies outliers for anomaly detection models.  
   ```sql
   SELECT employee_id, salary
   FROM employees e1
   WHERE salary > (
       SELECT AVG(salary)
       FROM employees e2
       WHERE e2.department_id = e1.department_id
   );
   ```

10. **Use a nested subquery to find the product with the highest sales in each category.**  
    Aggregates data for top-performing product analysis.  
    ```sql
    SELECT category, product_name, total_sales
    FROM (
        SELECT category, product_name, SUM(sales) AS total_sales,
               RANK() OVER (PARTITION BY category ORDER BY SUM(sales) DESC) AS rnk
        FROM sales
        GROUP BY category, product_name
    ) ranked
    WHERE rnk = 1;
    ```

11. **Write a query using NULLIF to avoid division by zero when calculating average order value.**  
    Ensures robust calculations for metrics in ML pipelines.  
    ```sql
    SELECT customer_id,
           SUM(order_amount) / NULLIF(COUNT(order_id), 0) AS avg_order_value
    FROM orders
    GROUP BY customer_id;
    ```

## Data Manipulation Language (DML)

### Basic
12. **Write an INSERT statement to add a new customer to the `customers` table.**  
    Adds new data points for model retraining.  
    ```sql
    INSERT INTO customers (customer_id, name, email)
    VALUES (1001, 'John Doe', 'john.doe@example.com');
    ```

13. **Update the `orders` table to set the status to 'Shipped' for orders older than 7 days.**  
    Updates dataset status for real-time analytics.  
    ```sql
    UPDATE orders
    SET status = 'Shipped'
    WHERE order_date < CURRENT_DATE - INTERVAL '7 days';
    ```

14. **Delete records from a `logs` table where the log date is older than 30 days.**  
    Removes outdated data to maintain dataset relevance.  
    ```sql
    DELETE FROM logs
    WHERE log_date < CURRENT_DATE - INTERVAL '30 days';
    ```

### Intermediate
15. **Insert multiple rows into a `sales` table using a single INSERT statement.**  
    Bulk loads data for batch processing in ETL pipelines.  
    ```sql
    INSERT INTO sales (sale_id, product_id, amount)
    VALUES
        (1, 101, 500),
        (2, 102, 750),
        (3, 103, 300);
    ```

16. **Update multiple columns (e.g., `price` and `stock`) in a `products` table based on a condition.**  
    Adjusts multiple features simultaneously for data consistency.  
    ```sql
    UPDATE products
    SET price = price * 1.1,
        stock = stock - 10
    WHERE category = 'Electronics';
    ```

17. **Delete records from a `users` table where the last login is NULL.**  
    Cleans inactive user data for model accuracy.  
    ```sql
    DELETE FROM users
    WHERE last_login IS NULL;
    ```

### Advanced
18. **Use INSERT INTO SELECT to copy high-value orders into a `premium_orders` table.**  
    Creates a subset of data for premium customer analysis.  
    ```sql
    INSERT INTO premium_orders (order_id, customer_id, order_amount)
    SELECT order_id, customer_id, order_amount
    FROM orders
    WHERE order_amount > 1000;
    ```

19. **Write an UPDATE query using a subquery to adjust prices based on category averages.**  
    Normalizes data for consistent feature scaling.  
    ```sql
    UPDATE products p
    SET price = (
        SELECT AVG(price) * 1.05
        FROM products p2
        WHERE p2.category = p.category
    );
    ```

20. **Delete duplicate rows from a `transactions` table, keeping the most recent entry.**  
    Ensures data quality by removing duplicates.  
    ```sql
    DELETE FROM transactions
    WHERE transaction_id NOT IN (
        SELECT transaction_id
        FROM (
            SELECT transaction_id,
                   ROW_NUMBER() OVER (PARTITION BY customer_id, amount ORDER BY transaction_date DESC) AS rn
            FROM transactions
        ) t
        WHERE rn = 1
    );
    ```

## Data Definition Language (DDL)

### Basic
21. **Create a table `user_activity` with columns for user_id, activity_date, and action.**  
    Designs tables for storing user behavior data.  
    ```sql
    CREATE TABLE user_activity (
        user_id INT,
        activity_date DATE,
        action VARCHAR(50)
    );
    ```

22. **Add a `last_updated` column to an existing `customers` table.**  
    Tracks data updates for versioning in ML pipelines.  
    ```sql
    ALTER TABLE customers
    ADD last_updated TIMESTAMP DEFAULT CURRENT_TIMESTAMP;
    ```

23. **Drop a table named `temp_data`.**  
    Removes temporary tables to optimize storage.  
    ```sql
    DROP TABLE temp_data;
    ```

### Intermediate
24. **Alter a table to add a PRIMARY KEY constraint on the `user_id` column.**  
    Ensures data integrity for unique identifiers.  
    ```sql
    ALTER TABLE users
    ADD CONSTRAINT pk_user_id PRIMARY KEY (user_id);
    ```

25. **Create a view to show total sales by product category.**  
    Simplifies recurring queries for reporting.  
    ```sql
    CREATE VIEW sales_by_category AS
    SELECT category, SUM(sales) AS total_sales
    FROM sales
    GROUP BY category;
    ```

26. **Add a CHECK constraint to ensure prices in a `products` table are positive.**  
    Enforces data quality for reliable model inputs.  
    ```sql
    ALTER TABLE products
    ADD CONSTRAINT chk_price CHECK (price > 0);
    ```

### Advanced
27. **Create a partitioned table for `sales` based on transaction year.**  
    Improves query performance for large-scale data analysis.  
    ```sql
    CREATE TABLE sales (
        sale_id INT,
        transaction_date DATE,
        amount DECIMAL
    ) PARTITION BY RANGE (EXTRACT(YEAR FROM transaction_date));
    CREATE TABLE sales_2022 PARTITION OF sales
        FOR VALUES FROM (2022) TO (2023);
    CREATE TABLE sales_2023 PARTITION OF sales
        FOR VALUES FROM (2023) TO (2024);
    ```

28. **Alter a table to add a FOREIGN KEY constraint linking `orders` to `customers`.**  
    Maintains referential integrity for joined datasets.  
    ```sql
    ALTER TABLE orders
    ADD CONSTRAINT fk_customer
    FOREIGN KEY (customer_id)
    REFERENCES customers (customer_id);
    ```

29. **Create a materialized view for daily user activity summaries.**  
    Caches aggregated data for faster model training.  
    ```sql
    CREATE MATERIALIZED VIEW daily_activity AS
    SELECT user_id, DATE(activity_date) AS activity_day, COUNT(*) AS action_count
    FROM user_activity
    GROUP BY user_id, DATE(activity_date)
    WITH DATA;
    ```

## Data Control Language (DCL)

### Basic
30. **Grant SELECT permission on a `sales` table to a user named 'analyst'.**  
    Controls access for data analysts in collaborative teams.  
    ```sql
    GRANT SELECT ON sales TO analyst;
    ```

31. **Revoke UPDATE permission from a user on the `customers` table.**  
    Restricts modifications to sensitive data.  
    ```sql
    REVOKE UPDATE ON customers FROM analyst;
    ```

### Intermediate
32. **Grant a role 'data_scientist' with SELECT and INSERT permissions on a `datasets` table.**  
    Manages access for data science teams.  
    ```sql
    GRANT SELECT, INSERT ON datasets TO data_scientist;
    ```

33. **Revoke all permissions from a user on a `logs` table.**  
    Ensures security when roles change.  
    ```sql
    REVOKE ALL ON logs FROM analyst;
    ```

### Advanced
34. **Implement row-level security to restrict users to their own department’s data.**  
    Protects sensitive data in multi-user environments.  
    ```sql
    ALTER TABLE employees ENABLE ROW LEVEL SECURITY;
    CREATE POLICY dept_access ON employees
    USING (department_id = (SELECT department_id FROM users WHERE user_id = current_user));
    ```

35. **Grant EXECUTE permission on a stored procedure to a data science team.**  
    Allows teams to run predefined data transformations.  
    ```sql
    GRANT EXECUTE ON PROCEDURE get_sales_data TO data_scientist;
    ```

## Transaction Control Language (TCL)

### Basic
36. **Write a COMMIT statement after inserting a new order.**  
    Ensures data changes are saved in ETL processes.  
    ```sql
    INSERT INTO orders (order_id, customer_id, amount)
    VALUES (1001, 101, 500);
    COMMIT;
    ```

37. **Use ROLLBACK to undo a failed batch update.**  
    Reverts errors during data updates.  
    ```sql
    BEGIN;
    UPDATE products
    SET price = price * 1.2
    WHERE category = 'Electronics';
    -- Error detected
    ROLLBACK;
    ```

### Intermediate
38. **Set a SAVEPOINT before updating a `products` table.**  
    Allows partial rollbacks in complex updates.  
    ```sql
    BEGIN;
    SAVEPOINT before_update;
    UPDATE products
    SET stock = stock - 5
    WHERE product_id = 101;
    -- Optionally: ROLLBACK TO SAVEPOINT before_update;
    COMMIT;
    ```

39. **Use SET TRANSACTION to enforce read-only mode for a query session.**  
    Prevents accidental data changes during analysis.  
    ```sql
    SET TRANSACTION READ ONLY;
    SELECT * FROM sales;
    ```

### Advanced
40. **Write a transaction block to insert an order and update inventory atomically.**  
    Ensures consistency in multi-table updates for real-time systems.  
    ```sql
    BEGIN;
    INSERT INTO orders (order_id, customer_id, amount)
    VALUES (1002, 102, 300);
    UPDATE products
    SET stock = stock - 1
    WHERE product_id = 101;
    COMMIT;
    ```

41. **Explain how to handle transaction isolation levels for concurrent data access.**  
    Isolation levels (e.g., READ COMMITTED, SERIALIZABLE) control data visibility in concurrent transactions. READ COMMITTED prevents dirty reads, while SERIALIZABLE ensures full consistency but may slow performance. In ML pipelines, choose based on data consistency needs vs. throughput.

## Joins and Aggregations

### Basic
42. **Write an INNER JOIN to combine `orders` and `customers` tables on customer_id.**  
    Combines datasets for feature creation.  
    ```sql
    SELECT o.order_id, c.name
    FROM orders o
    INNER JOIN customers c ON o.customer_id = c.customer_id;
    ```

43. **Use COUNT to find the number of orders per customer.**  
    Creates frequency-based features for customer analysis.  
    ```sql
    SELECT customer_id, COUNT(order_id) AS order_count
    FROM orders
    GROUP BY customer_id;
    ```

44. **Write a LEFT JOIN to include all products, even those without sales.**  
    Ensures complete data for inventory analysis.  
    ```sql
    SELECT p.product_name, s.amount
    FROM products p
    LEFT JOIN sales s ON p.product_id = s.product_id;
    ```

### Intermediate
45. **Use GROUP BY to calculate total sales by region.**  
    Aggregates data for regional performance models.  
    ```sql
    SELECT region, SUM(amount) AS total_sales
    FROM sales
    GROUP BY region;
    ```

46. **Write a query with HAVING to find categories with more than 100 sales.**  
    Filters aggregated data for significant trends.  
    ```sql
    SELECT category, COUNT(sale_id) AS sale_count
    FROM sales
    GROUP BY category
    HAVING COUNT(sale_id) > 100;
    ```

47. **Use UNION ALL to combine sales data from two years.**  
    Merges datasets for longitudinal analysis.  
    ```sql
    SELECT sale_id, amount
    FROM sales_2022
    UNION ALL
    SELECT sale_id, amount
    FROM sales_2023;
    ```

### Advanced
48. **Write a query using a self-join to find employees reporting to the same manager.**  
    Analyzes organizational structures for HR analytics.  
    ```sql
    SELECT e1.employee_id, e1.name, e2.employee_id AS colleague_id, e2.name AS colleague_name
    FROM employees e1
    JOIN employees e2 ON e1.manager_id = e2.manager_id
    WHERE e1.employee_id != e2.employee_id;
    ```

49. **Use a window function (RANK) to rank products by sales within each category.**  
    Creates ranking features for recommendation systems.  
    ```sql
    SELECT category, product_name, total_sales,
           RANK() OVER (PARTITION BY category ORDER BY total_sales DESC) AS sales_rank
    FROM (
        SELECT category, product_name, SUM(amount) AS total_sales
        FROM sales
        GROUP BY category, product_name
    ) s;
    ```

50. **Write a query with INTERSECT to find customers who purchased in both 2022 and 2023.**  
    Identifies loyal customers for retention models.  
    ```sql
    SELECT customer_id
    FROM orders
    WHERE YEAR(order_date) = 2022
    INTERSECT
    SELECT customer_id
    FROM orders
    WHERE YEAR(order_date) = 2023;
    ```

## Stored Procedures

### Basic
51. **Create a stored procedure to retrieve all active users.**  
    Automates user data extraction for analysis.  
    ```sql
    CREATE PROCEDURE GetActiveUsers()
    BEGIN
        SELECT *
        FROM users
        WHERE status = 'Active';
    END;
    ```

52. **Call a stored procedure to update product prices.**  
    Executes predefined data transformations.  
    ```sql
    CALL UpdateProductPrices();
    ```

### Intermediate
53. **Create a stored procedure with parameters to filter sales by date range.**  
    Enables flexible data extraction for time-series models.  
    ```sql
    CREATE PROCEDURE GetSalesByDateRange(IN start_date DATE, IN end_date DATE)
    BEGIN
        SELECT *
        FROM sales
        WHERE transaction_date BETWEEN start_date AND end_date;
    END;
    ```

54. **Drop a stored procedure named 'get_sales_data'.**  
    Manages database objects for maintenance.  
    ```sql
    DROP PROCEDURE get_sales_data;
    ```

### Advanced
55. **Write a stored procedure to calculate monthly user engagement metrics.**  
    Automates feature engineering for engagement models.  
    ```sql
    CREATE PROCEDURE CalculateMonthlyEngagement()
    BEGIN
        INSERT INTO engagement_metrics (month, user_id, action_count)
        SELECT DATE_TRUNC('month', activity_date) AS month, user_id, COUNT(*) AS action_count
        FROM user_activity
        GROUP BY DATE_TRUNC('month', activity_date), user_id;
    END;
    ```

56. **Create a stored procedure to handle batch inserts for new transactions.**  
    Optimizes data loading in ETL pipelines.  
    ```sql
    CREATE PROCEDURE BatchInsertTransactions(IN batch_size INT)
    BEGIN
        DECLARE i INT DEFAULT 1;
        WHILE i <= batch_size DO
            INSERT INTO transactions (transaction_id, amount)
            VALUES (i, RAND() * 1000);
            SET i = i + 1;
        END WHILE;
    END;
    ```

## Triggers

### Basic
57. **Create a trigger to log changes to the `orders` table.**  
    Tracks data changes for auditing.  
    ```sql
    CREATE TRIGGER log_order_changes
    AFTER UPDATE ON orders
    FOR EACH ROW
    INSERT INTO order_logs (order_id, change_time, old_status, new_status)
    VALUES (OLD.order_id, NOW(), OLD.status, NEW.status);
    ```

58. **Drop a trigger named 'log_updates'.**  
    Manages database triggers for maintenance.  
    ```sql
    DROP TRIGGER log_updates;
    ```

### Intermediate
59. **Create a BEFORE trigger to validate product prices before insertion.**  
    Ensures data quality for model inputs.  
    ```sql
    CREATE TRIGGER validate_price
    BEFORE INSERT ON products
    FOR EACH ROW
    BEGIN
        IF NEW.price <= 0 THEN
            SIGNAL SQLSTATE '45000'
            SET MESSAGE_TEXT = 'Price must be positive';
        END IF;
    END;
    ```

60. **Create an AFTER trigger to update inventory after an order is placed.**  
    Automates inventory updates for real-time systems.  
    ```sql
    CREATE TRIGGER update_inventory
    AFTER INSERT ON orders
    FOR EACH ROW
    UPDATE products
    SET stock = stock - 1
    WHERE product_id = NEW.product_id;
    ```

### Advanced
61. **Write a trigger to prevent deletion of critical customer records.**  
    Protects key data for model training.  
    ```sql
    CREATE TRIGGER prevent_customer_deletion
    BEFORE DELETE ON customers
    FOR EACH ROW
    BEGIN
        IF OLD.is_vip = 1 THEN
            SIGNAL SQLSTATE '45000'
            SET MESSAGE_TEXT = 'Cannot delete VIP customers';
        END IF;
    END;
    ```

62. **Create a trigger to flag outliers in transaction amounts.**  
    Automates anomaly detection in data pipelines.  
    ```sql
    CREATE TRIGGER flag_outliers
    AFTER INSERT ON transactions
    FOR EACH ROW
    BEGIN
        DECLARE avg_amount DECIMAL;
        DECLARE std_dev DECIMAL;
        SELECT AVG(amount), STDDEV(amount) INTO avg_amount, std_dev
        FROM transactions;
        IF NEW.amount > avg_amount + 2 * std_dev THEN
            INSERT INTO outliers (transaction_id, amount, flag_time)
            VALUES (NEW.transaction_id, NEW.amount, NOW());
        END IF;
    END;
    ```

## Cursors

### Basic
63. **Declare a cursor to iterate over a `customers` table.**  
    Processes data row-by-row for custom transformations.  
    ```sql
    DECLARE customer_cursor CURSOR FOR
    SELECT customer_id, name
    FROM customers;
    ```

64. **Write a query to open and fetch data from a cursor.**  
    Extracts data for iterative processing.  
    ```sql
    DECLARE customer_id INT;
    DECLARE customer_name VARCHAR(100);
    DECLARE customer_cursor CURSOR FOR
    SELECT customer_id, name FROM customers;
    OPEN customer_cursor;
    FETCH customer_cursor INTO customer_id, customer_name;
    CLOSE customer_cursor;
    ```

### Intermediate
65. **Use a cursor to update customer statuses based on activity.**  
    Customizes user data for segmentation.  
    ```sql
    BEGIN
        DECLARE done INT DEFAULT 0;
        DECLARE cid INT;
        DECLARE last_activity DATE;
        DECLARE cur CURSOR FOR
        SELECT customer_id, MAX(activity_date)
        FROM user_activity
        GROUP BY customer_id;
        DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
        OPEN cur;
        read_loop: LOOP
            FETCH cur INTO cid, last_activity;
            IF done THEN
                LEAVE read_loop;
            END IF;
            IF last_activity < CURRENT_DATE - INTERVAL '30 days' THEN
                UPDATE customers
                SET status = 'Inactive'
                WHERE customer_id = cid;
            END IF;
        END LOOP;
        CLOSE cur;
    END;
    ```

66. **Close a cursor after processing a `sales` table.**  
    Manages resources in long-running queries.  
    ```sql
    CLOSE sales_cursor;
    ```

### Advanced
67. **Write a cursor-based script to calculate personalized user scores.**  
    Creates custom features for recommendation systems.  
    ```sql
    BEGIN
        DECLARE done INT DEFAULT 0;
        DECLARE cid INT;
        DECLARE total_amount DECIMAL;
        DECLARE cur CURSOR FOR
        SELECT customer_id, SUM(amount)
        FROM orders
        GROUP BY customer_id;
        DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
        OPEN cur;
        read_loop: LOOP
            FETCH cur INTO cid, total_amount;
            IF done THEN
                LEAVE read_loop;
            END IF;
            INSERT INTO user_scores (customer_id, score)
            VALUES (cid, total_amount / 1000);
        END LOOP;
        CLOSE cur;
    END;
    ```

68. **Use a cursor to process large datasets in chunks.**  
    Optimizes memory usage in data processing.  
    ```sql
    BEGIN
        DECLARE done INT DEFAULT 0;
        DECLARE sid INT;
        DECLARE cur CURSOR FOR
        SELECT sale_id FROM sales LIMIT 1000;
        DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
        OPEN cur;
        read_loop: LOOP
            FETCH cur INTO sid;
            IF done THEN
                LEAVE read_loop;
            END IF;
            -- Process sale_id
            UPDATE sales
            SET processed = 1
            WHERE sale_id = sid;
        END LOOP;
        CLOSE cur;
    END;
    ```

## Indexing

### Basic
69. **Create an index on the `customer_id` column of an `orders` table.**  
    Speeds up queries for large datasets.  
    ```sql
    CREATE INDEX idx_customer_id ON orders (customer_id);
    ```

70. **Explain the purpose of a B-Tree index.**  
    A B-Tree index organizes data in a balanced tree, optimizing range queries (e.g., WHERE price > 100) and equality searches. In AI/ML, it accelerates data retrieval for large datasets.

### Intermediate
71. **Create a composite index on `order_date` and `customer_id`.**  
    Improves performance for multi-column queries.  
    ```sql
    CREATE INDEX idx_order_date_customer ON orders (order_date, customer_id);
    ```

72. **Drop an index named 'idx_customer_id'.**  
    Manages database performance.  
    ```sql
    DROP INDEX idx_customer_id ON orders;
    ```

### Advanced
73. **Explain when a Hash index is preferable over a B-Tree index.**  
    Hash indexes excel in equality searches (e.g., WHERE id = 5) but don’t support range queries. In ML pipelines, use Hash for lookup-heavy tasks and B-Tree for range-based queries.

74. **Write a query to analyze index usage for performance tuning.**  
    Ensures efficient data access for large-scale models.  
    ```sql
    SELECT *
    FROM pg_stat_user_indexes
    WHERE relname = 'orders';
    ```

## Extra Modules

### Pivot Queries
75. **Write a pivot query to show sales by product and month.**  
    Transforms data for feature matrices in ML models.  
    ```sql
    SELECT *
    FROM (
        SELECT product_id, EXTRACT(MONTH FROM transaction_date) AS month, amount
        FROM sales
    ) s
    PIVOT (
        SUM(amount)
        FOR month IN (1 AS Jan, 2 AS Feb, 3 AS Mar)
    );
    ```

76. **Use UNPIVOT to convert columnar data into rows.**  
    Reshapes data for analysis.  
    ```sql
    SELECT product_id, month, amount
    FROM sales_pivot
    UNPIVOT (
        amount
        FOR month IN (Jan, Feb, Mar)
    );
    ```

### Dynamic Queries
77. **Write a dynamic query to filter sales by a user-specified region.**  
    Adapts queries for flexible data extraction.  
    ```sql
    PREPARE dynamic_sales (VARCHAR) AS
    SELECT *
    FROM sales
    WHERE region = $1;
    EXECUTE dynamic_sales('North');
    ```

78. **Create a dynamic query to generate monthly reports.**  
    Automates reporting for business intelligence.  
    ```sql
    DO $$
    DECLARE
        query_text TEXT;
    BEGIN
        query_text := 'SELECT DATE_TRUNC(''month'', transaction_date) AS month, SUM(amount)
                       FROM sales
                       GROUP BY DATE_TRUNC(''month'', transaction_date)';
        EXECUTE query_text;
    END $$;
    ```

### User-Defined Functions
79. **Create a UDF to calculate the distance between two coordinates.**  
    Computes spatial features for location-based models.  
    ```sql
    CREATE FUNCTION calculate_distance(lat1 FLOAT, lon1 FLOAT, lat2 FLOAT, lon2 FLOAT)
    RETURNS FLOAT AS $$
    BEGIN
        RETURN 6371 * ACOS(
            COS(RADIANS(lat1)) * COS(RADIANS(lat2)) *
            COS(RADIANS(lon2) - RADIANS(lon1)) +
            SIN(RADIANS(lat1)) * SIN(RADIANS(lat2))
        );
    END;
    $$ LANGUAGE plpgsql;
    ```

80. **Use a UDF to normalize transaction amounts.**  
    Standardizes data for model training.  
    ```sql
    CREATE FUNCTION normalize_amount(amount DECIMAL, max_amount DECIMAL)
    RETURNS DECIMAL AS $$
    BEGIN
        RETURN amount / max_amount;
    END;
    $$ LANGUAGE plpgsql;
    SELECT normalize_amount(amount, (SELECT MAX(amount) FROM transactions))
    FROM transactions;
    ```

### Window Functions
81. **Use ROW_NUMBER() to assign unique IDs to transactions within each customer.**  
    Creates sequence-based features for time-series models.  
    ```sql
    SELECT customer_id, transaction_id,
           ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY transaction_date) AS transaction_seq
    FROM transactions;
    ```

82. **Write a query with LAG() to compare current and previous sales.**  
    Generates lagged features for forecasting.  
    ```sql
    SELECT transaction_date, amount,
           LAG(amount) OVER (ORDER BY transaction_date) AS prev_amount
    FROM sales;
    ```

### Common Table Expressions (CTEs)
83. **Write a CTE to find duplicate customer records.**  
    Cleans data for model accuracy.  
    ```sql
    WITH duplicates AS (
        SELECT email, COUNT(*) AS cnt
        FROM customers
        GROUP BY email
        HAVING COUNT(*) > 1
    )
    SELECT c.*
    FROM customers c
    JOIN duplicates d ON c.email = d.email;
    ```

84. **Use a recursive CTE to build a hierarchy of employees.**  
    Analyzes organizational structures for HR analytics.  
    ```sql
    WITH RECURSIVE emp_hierarchy AS (
        SELECT employee_id, name, manager_id, 1 AS level
        FROM employees
        WHERE manager_id IS NULL
        UNION ALL
        SELECT e.employee_id, e.name, e.manager_id, eh.level + 1
        FROM employees e
        JOIN emp_hierarchy eh ON e.manager_id = eh.employee_id
    )
    SELECT * FROM emp_hierarchy;
    ```

### Specialized Queries
85. **Write a query to detect outliers in transaction amounts using standard deviation.**  
    Identifies anomalies for preprocessing.  
    ```sql
    WITH stats AS (
        SELECT AVG(amount) AS avg_amount, STDDEV(amount) AS std_dev
        FROM transactions
    )
    SELECT transaction_id, amount
    FROM transactions, stats
    WHERE amount > avg_amount + 2 * std_dev
       OR amount < avg_amount - 2 * std_dev;
    ```

86. **Find the median sale price for each product category.**  
    Computes central tendencies for feature engineering.  
    ```sql
    WITH ranked AS (
        SELECT category, price,
               ROW_NUMBER() OVER (PARTITION BY category ORDER BY price) AS rn,
               COUNT(*) OVER (PARTITION BY category) AS cnt
        FROM products
    )
    SELECT category,
           AVG(price) AS median_price
    FROM ranked
    WHERE rn IN (FLOOR((cnt + 1)/2), CEIL((cnt + 1)/2))
    GROUP BY category;
    ```

### DateTime Functions
87. **Extract the day of the week from a transaction date.**  
    Creates temporal features for behavioral analysis.  
    ```sql
    SELECT transaction_date,
           EXTRACT(DOW FROM transaction_date) AS day_of_week
    FROM transactions;
    ```

88. **Write a query to group sales by quarter.**  
    Aggregates data for seasonal trend analysis.  
    ```sql
    SELECT EXTRACT(QUARTER FROM transaction_date) AS quarter,
           SUM(amount) AS total_sales
    FROM sales
    GROUP BY EXTRACT(QUARTER FROM transaction_date);
    ```

## Additional Practice Questions
89. **Find all neighborhoods with zero users.**  
    Identifies inactive areas for user engagement models.  
    ```sql
    SELECT n.neighborhood
    FROM neighborhoods n
    LEFT JOIN users u ON n.neighborhood_id = u.neighborhood_id
    WHERE u.user_id IS NULL;
    ```

90. **Return pairs of projects where the end date of one matches another’s start date.**  
    Analyzes project timelines for resource allocation.  
    ```sql
    SELECT p1.project_id AS project1, p2.project_id AS project2
    FROM projects p1
    JOIN projects p2 ON p1.end_date = p2.start_date
    WHERE p1.project_id != p2.project_id;
    ```

91. **Measure the quality of search results for each search term.**  
    Evaluates search algorithms for ranking models.  
    ```sql
    SELECT search_term,
           AVG(CASE WHEN clicked = 1 THEN 1.0 ELSE 0 END) AS click_through_rate
    FROM search_logs
    GROUP BY search_term;
    ```

92. **Get the average order value by gender.**  
    Creates gender-based features for customer analysis.  
    ```sql
    SELECT c.gender, AVG(o.order_amount) AS avg_order_value
    FROM customers c
    JOIN orders o ON c.customer_id = o.customer_id
    GROUP BY c.gender;
    ```

93. **Find the third purchase of every user.**  
    Analyzes purchase patterns for loyalty models.  
    ```sql
    WITH ranked_orders AS (
        SELECT customer_id, order_id, order_date,
               ROW_NUMBER() OVER (PARTITION BY customer_id ORDER BY order_date) AS purchase_number
        FROM orders
    )
    SELECT customer_id, order_id, order_date
    FROM ranked_orders
    WHERE purchase_number = 3;
    ```

94. **Calculate first-touch attribution for each user_id that converted.**  
    Tracks conversion paths for marketing analytics.  
    ```sql
    WITH first_touch AS (
        SELECT user_id, MIN(interaction_date) AS first_interaction
        FROM interactions
        WHERE converted = 1
        GROUP BY user_id
    )
    SELECT i.user_id, i.channel
    FROM interactions i
    JOIN first_touch ft
        ON i.user_id = ft.user_id
        AND i.interaction_date = ft.first_interaction;
    ```

95. **Create a histogram of tweets by user.**  
    Analyzes tweet distribution for sentiment models.  
    ```sql
    SELECT user_id,
           FLOOR(COUNT(*) / 10) * 10 AS tweet_bucket,
           COUNT(*) AS tweet_count
    FROM tweets
    GROUP BY user_id, FLOOR(COUNT(*) / 10) * 10
    ORDER BY tweet_bucket;
    ```

96. **Identify pages with no likes.**  
    Detects low-engagement content for recommendation systems.  
    ```sql
    SELECT p.page_id, p.page_name
    FROM pages p
    LEFT JOIN likes l ON p.page_id = l.page_id
    WHERE l.page_id IS NULL;
    ```

97. **Compare laptop vs. mobile viewership.**  
    Analyzes device-based user behavior.  
    ```sql
    SELECT device_type,
           COUNT(*) AS view_count,
           SUM(CASE WHEN engaged = 1 THEN 1 ELSE 0 END) AS engagement_count
    FROM viewership
    WHERE device_type IN ('laptop', 'mobile')
    GROUP BY device_type;
    ```

98. **Calculate year-on-year growth rate for sales.**  
    Supports trend analysis for forecasting.  
    ```sql
    WITH yearly_sales AS (
        SELECT EXTRACT(YEAR FROM transaction_date) AS year,
               SUM(amount) AS total_sales
        FROM sales
        GROUP BY EXTRACT(YEAR FROM transaction_date)
    )
    SELECT year,
           total_sales,
           ((total_sales - LAG(total_sales) OVER (ORDER BY year)) / LAG(total_sales) OVER (ORDER BY year)) * 100 AS yoy_growth
    FROM yearly_sales;
    ```

99. **Write a query to fetch duplicate values from a column.**  
    Cleans data for model accuracy.  
    ```sql
    SELECT email, COUNT(*) AS cnt
    FROM customers
    GROUP BY email
    HAVING COUNT(*) > 1;
    ```

100. **Find departments with the highest average salary.**  
     Analyzes departmental performance for resource allocation.  
     ```sql
     SELECT department_id, AVG(salary) AS avg_salary
     FROM employees
     GROUP BY department_id
     ORDER BY avg_salary DESC
     LIMIT 1;
     ```