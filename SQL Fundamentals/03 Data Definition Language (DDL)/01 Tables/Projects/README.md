# 📊 Projects - Mastering Table Creation

## 🌟 Overview

Welcome to the **Projects** section for **Table Creation**! 🚀 These five unique projects are your playground to master the four core concepts—`Basic CREATE TABLE`, `CREATE TABLE with Data Types`, `CREATE TABLE AS SELECT`, and `Temporary Tables`. Dive into AI/ML-themed challenges like setting up datasets or staging model outputs, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL table creation practical and fun, helping you:
- **Apply Skills**: Build ML datasets and storage with `CREATE TABLE`.
- **Ace Interviews**: Solve schema design problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Set up robust tables for model training, logging, or analysis.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key table creation techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Storage** | Basic CREATE TABLE, CREATE TABLE with Data Types | Create tables to store ML model metadata and predictions. |
| **Dataset Setup** | CREATE TABLE with Data Types | Build a dataset table with precise data types for ML training. |
| **Sales Aggregation** | CREATE TABLE AS SELECT | Create a summary table from sales data for reporting. |
| **Temp Processing** | Temporary Tables | Use temporary tables to stage ML data processing. |
| **Capstone: Table Creation** | All Four | Design a suite of tables for an ML pipeline with varied creation methods. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Storage/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Basic CREATE TABLE`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Storage
- **Folder**: `Project1_Model_Storage/`
- **Concepts**: `Basic CREATE TABLE`, `CREATE TABLE with Data Types`
- **Description**: Create tables to store ML model metadata and predictions, focusing on structure and data types.
- **Tasks**:
  - Create a `models` table with columns for `model_id`, `name`, and `version`.
  - Create a `predictions` table with appropriate data types for `model_id`, `score`, and `eval_date`.
  - Create a `model_logs` table with a mix of integer, string, and date types.
- **AI/ML Use Case**: Sets up storage for model tracking and outputs.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      name VARCHAR(100),
      version FLOAT
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      eval_date DATE
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE model_logs (
      log_id INT PRIMARY KEY,
      model_id INT,
      log_message VARCHAR(255),
      log_date DATETIME
  );
  ```
  </details>

### Project 2: Dataset Setup
- **Folder**: `Project2_Dataset_Setup/`
- **Concepts**: `CREATE TABLE with Data Types`
- **Description**: Build a dataset table with precise data types for ML training data, ensuring compatibility with numeric and categorical features.
- **Tasks**:
  - Create a `training_data` table with columns for `id`, `feature1`, `feature2`, and `label`.
  - Create a `test_data` table with similar structure but add a `confidence` column (FLOAT).
  - Create a `feature_metadata` table to store feature names and types (e.g., 'numeric', 'categorical').
- **AI/ML Use Case**: Prepares structured datasets for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE test_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50),
      confidence FLOAT
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE feature_metadata (
      feature_id INT PRIMARY KEY,
      feature_name VARCHAR(100),
      feature_type VARCHAR(50)
  );
  ```
  </details>

### Project 3: Sales Aggregation
- **Folder**: `Project3_Sales_Aggregation/`
- **Concepts**: `CREATE TABLE AS SELECT`
- **Description**: Create a summary table from sales data for reporting, using `CREATE TABLE AS SELECT` to aggregate metrics.
- **Tasks**:
  - Create a `sales_summary` table with total sales by region from `sales_data`.
  - Create a `customer_sales` table with average sale amount per customer.
  - Create a `monthly_sales` table with sales totals grouped by month.
- **AI/ML Use Case**: Generates aggregated data for sales prediction models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE sales_summary AS
  SELECT region, SUM(amount) AS total_sales
  FROM sales_data
  GROUP BY region;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE customer_sales AS
  SELECT customer_id, AVG(amount) AS avg_sale
  FROM sales_data
  GROUP BY customer_id;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE monthly_sales AS
  SELECT DATE_FORMAT(sale_date, '%Y-%m') AS sale_month, SUM(amount) AS total_sales
  FROM sales_data
  GROUP BY DATE_FORMAT(sale_date, '%Y-%m');
  ```
  </details>

### Project 4: Temp Processing
- **Folder**: `Project4_Temp_Processing/`
- **Concepts**: `Temporary Tables`
- **Description**: Use temporary tables to stage ML data processing, such as filtering or transforming predictions.
- **Tasks**:
  - Create a temporary table `temp_predictions` to store high-confidence predictions.
  - Create a temporary table `temp_users` for active users based on `activity`.
  - Create a temporary table `temp_sales` to hold recent sales for analysis.
- **AI/ML Use Case**: Stages intermediate data for model evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TEMPORARY TABLE temp_predictions AS
  SELECT model_id, score, eval_date
  FROM predictions
  WHERE score > 0.9;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TEMPORARY TABLE temp_users AS
  SELECT user_id, email, region
  FROM users
  WHERE activity > 5;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TEMPORARY TABLE temp_sales AS
  SELECT sale_id, customer_id, amount
  FROM sales_data
  WHERE sale_date >= '2025-08-01';
  ```
  </details>

### Project 5: Capstone - Table Creation
- **Folder**: `Project5_Capstone_Table_Creation/`
- **Concepts**: All Four (`Basic CREATE TABLE`, `CREATE TABLE with Data Types`, `CREATE TABLE AS SELECT`, `Temporary Tables`)
- **Description**: Design a suite of tables for an ML pipeline, combining all creation methods to support fraud detection.
- **Tasks**:
  - Create a `fraud_logs` table with columns for `log_id`, `order_id`, and `flag` (BOOLEAN).
  - Create a `order_features` table with numeric and string data types for ML features.
  - Create a `fraud_summary` table using `CREATE TABLE AS SELECT` from `customer_orders`.
  - Create a temporary table `temp_fraud_candidates` for high-risk orders.
  - Create a `fraud_metadata` table to track analysis details.
- **AI/ML Use Case**: Sets up a robust schema for fraud detection models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE fraud_logs (
      log_id INT PRIMARY KEY,
      order_id INT,
      flag BOOLEAN
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE order_features (
      feature_id INT PRIMARY KEY,
      order_id INT,
      feature_value FLOAT,
      feature_type VARCHAR(50)
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE fraud_summary AS
  SELECT customer_id, COUNT(*) AS order_count, SUM(amount) AS total_amount
  FROM customer_orders
  GROUP BY customer_id;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  CREATE TEMPORARY TABLE temp_fraud_candidates AS
  SELECT order_id, amount
  FROM customer_orders
  WHERE amount > 200;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  CREATE TABLE fraud_metadata (
      meta_id INT PRIMARY KEY,
      analysis_name VARCHAR(100),
      created_date DATE
  );
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Basic CREATE TABLE`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix `AS SELECT` and `Temporary Tables` for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more schema challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for table creation? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all four table creation concepts. Below are schemas and sample data for input tables—copy-paste to create tables or save as a `.sql` file. Output tables are created via project tasks.

### Dataset 1: predictions
- **Used In**: Project 1, Project 4, Project 5 (Capstone)
- **Description**: ML model predictions for table creation.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      eval_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, eval_date) VALUES
  (1, 101, 0.92, '2025-08-01'),
  (2, 101, 0.87, '2025-08-02'),
  (3, 102, 0.95, '2025-08-03'),
  (4, 102, 0.78, '2025-08-04'),
  (5, 103, 0.91, '2025-08-05'),
  (6, 103, 0.84, '2025-08-06'),
  (7, 104, 0.96, '2025-08-07'),
  (8, 104, 0.80, '2025-08-08'),
  (9, 105, 0.89, '2025-08-09'),
  (10, 105, 0.93, '2025-08-10'),
  (11, 106, 0.77, '2025-08-11'),
  (12, 106, 0.94, '2025-08-12'),
  (13, 107, 0.85, '2025-08-13'),
  (14, 107, 0.90, '2025-08-14'),
  (15, 108, 0.88, '2025-08-15'),
  (16, 108, 0.97, '2025-08-16'),
  (17, 109, 0.79, '2025-08-17'),
  (18, 109, 0.92, '2025-08-18'),
  (19, 110, 0.86, '2025-08-19'),
  (20, 110, 0.91, '2025-08-20');
  ```
- **Notes**: Provides source data for `Temporary Tables`, `CREATE TABLE AS SELECT`.

### Dataset 2: users
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: User data for temporary table creation.
- **Schema**:
  ```sql
  CREATE TABLE users (
      user_id INT PRIMARY KEY,
      email VARCHAR(100),
      region VARCHAR(50),
      activity INT
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO users (user_id, email, region, activity) VALUES
  (101, 'john@gmail.com', 'North', 4),
  (102, 'jane@yahoo.com', 'South', 6),
  (103, 'mike@outlook.com', 'East', 7),
  (104, 'sara@gmail.com', 'West', 3),
  (105, 'tom@company.com', 'North', 8),
  (106, 'lisa@yahoo.com', 'South', 2),
  (107, 'mark@outlook.com', 'East', 6),
  (108, 'anna@gmail.com', 'West', 5),
  (109, 'paul@company.com', 'North', 4),
  (110, 'emma@yahoo.com', 'South', 7),
  (111, 'david@outlook.com', 'East', 3),
  (112, 'clara@gmail.com', 'West', 6),
  (113, 'steve@company.com', 'North', 5),
  (114, 'lucy@yahoo.com', 'South', 4),
  (115, 'peter@outlook.com', 'East', 8),
  (116, 'mary@gmail.com', 'West', 2),
  (117, 'nick@company.com', 'North', 6),
  (118, 'zoe@yahoo.com', 'South', 5),
  (119, 'ben@outlook.com', 'East', 7),
  (120, 'kate@gmail.com', 'West', 4),
  (121, 'lily@company.com', 'North', 3),
  (122, 'jack@yahoo.com', 'South', 6),
  (123, 'rose@outlook.com', 'East', 5),
  (124, 'sam@gmail.com', 'West', 4),
  (125, 'tina@company.com', 'North', 7);
  ```
- **Notes**: Supports `Temporary Tables` for filtering active users.

### Dataset 3: sales_data
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Sales data for aggregation tables.
- **Schema**:
  ```sql
  CREATE TABLE sales_data (
      sale_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      sale_date DATE,
      region VARCHAR(50)
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date, region) VALUES
  (101, 201, 50.0, '2025-07-01', 'East'),
  (102, 202, 150.5, '2025-07-02', 'West'),
  (103, 203, 25.0, '2025-07-03', 'South'),
  (104, 204, 200.0, '2025-07-04', 'North'),
  (105, 205, 75.3, '2025-07-05', 'East'),
  (106, 206, 300.0, '2025-07-06', 'West'),
  (107, 207, 40.0, '2025-07-07', 'South'),
  (108, 208, 120.7, '2025-07-08', 'North'),
  (109, 209, 90.5, '2025-07-09', 'East'),
  (110, 210, 60.0, '2025-07-10', 'West'),
  (111, 211, 250.0, '2025-07-11', 'South'),
  (112, 212, 30.0, '2025-07-12', 'North'),
  (113, 213, 180.0, '2025-07-13', 'East'),
  (114, 214, 45.0, '2025-07-14', 'West'),
  (115, 215, 100.0, '2025-07-15', 'South'),
  (116, 216, 70.5, '2025-07-16', 'North'),
  (117, 217, 200.5, '2025-07-17', 'East'),
  (118, 218, 55.0, '2025-07-18', 'West'),
  (119, 219, 130.0, '2025-07-19', 'South'),
  (120, 220, 85.0, '2025-07-20', 'North'),
  (121, 221, 110.0, '2025-07-21', 'East'),
  (122, 222, 65.0, '2025-07-22', 'West'),
  (123, 223, 175.0, '2025-07-23', 'South'),
  (124, 224, 35.0, '2025-07-24', 'North'),
  (125, 225, 95.0, '2025-07-25', 'East');
  ```
- **Notes**: Supports `CREATE TABLE AS SELECT` for aggregations.

### Dataset 4: customer_orders
- **Used In**: Project 5 (Capstone)
- **Description**: Customer orders for fraud-related table creation.
- **Schema**:
  ```sql
  CREATE TABLE customer_orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      order_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date) VALUES
  (101, 301, 80.0, '2025-07-01'),
  (102, 302, 120.5, '2025-07-02'),
  (103, 303, 15.0, '2025-07-03'),
  (104, 304, 250.0, '2025-07-04'),
  (105, 305, 65.3, '2025-07-05'),
  (106, 306, 400.0, '2025-07-06'),
  (107, 307, 30.0, '2025-07-07'),
  (108, 308, 110.7, '2025-07-08'),
  (109, 309, 70.5, '2025-07-09'),
  (110, 310, 50.0, '2025-07-10'),
  (111, 311, 200.0, '2025-07-11'),
  (112, 312, 20.0, '2025-07-12'),
  (113, 313, 160.0, '2025-07-13'),
  (114, 314, 35.0, '2025-07-14'),
  (115, 315, 90.0, '2025-07-15'),
  (116, 316, 60.5, '2025-07-16'),
  (117, 317, 180.5, '2025-07-17'),
  (118, 318, 45.0, '2025-07-18'),
  (119, 319, 100.0, '2025-07-19'),
  (120, 320, 75.0, '2025-07-20');
  ```
- **Notes**: Supports `CREATE TABLE AS SELECT`, `Temporary Tables` for fraud analysis.

### Setup Instructions
1. **Create Input Tables**: Run the `CREATE TABLE` and `INSERT` statements for `predictions`, `users`, `sales_data`, and `customer_orders`.
2. **Generate Output Tables**: Use project tasks to create new tables (e.g., `models`, `sales_summary`).
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to avoid production risks.
4. **Compatibility**:
   - MySQL: Use `TEMPORARY TABLE` for temp tables; `DATE_FORMAT` for monthly grouping.
   - PostgreSQL: Use `CREATE TEMPORARY TABLE`; replace `DATE_FORMAT` with `TO_CHAR(sale_date, 'YYYY-MM')`.
   - SQL Server: Use `#table_name` for temp tables; `FORMAT(sale_date, 'yyyy-MM')` for monthly grouping.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master Table Creation and shine in AI/ML interviews! Happy querying! ✨</p>
</div>