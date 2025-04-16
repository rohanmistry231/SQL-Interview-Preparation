# 📊 Projects - Mastering Views

## 🌟 Overview

Welcome to the **Projects** section for **Views**! 🚀 These five unique projects are your playground to master the four core concepts—`Basic CREATE VIEW`, `CREATE VIEW with JOIN`, `CREATE OR REPLACE VIEW`, and `Materialized Views`. Dive into AI/ML-themed challenges like summarizing model predictions or joining datasets, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL views practical and fun, helping you:
- **Apply Skills**: Simplify ML data access with views for analysis.
- **Ace Interviews**: Solve data presentation problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Create reusable views for model metrics, reporting, or training data.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key view techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Prediction Summary** | Basic CREATE VIEW | Create simple views to summarize ML model predictions. |
| **Sales Insights** | CREATE VIEW with JOIN | Build views combining sales and customer data for insights. |
| **User Activity View** | CREATE OR REPLACE VIEW | Update views to reflect changing user activity metrics. |
| **Model Metrics** | Materialized Views | Create materialized views for persisted model performance data. |
| **Capstone: Views** | All Four | Design a suite of views for an ML fraud detection pipeline. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Prediction_Summary/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Basic CREATE VIEW`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Prediction Summary
- **Folder**: `Project1_Prediction_Summary/`
- **Concepts**: `Basic CREATE VIEW`
- **Description**: Create simple views to summarize ML model predictions for quick analysis.
- **Tasks**:
  - Create a view `high_score_predictions` for predictions with `score` > 0.9.
  - Create a view `recent_predictions` for predictions after '2025-08-01'.
  - Create a view `model_avg_scores` with average scores per `model_id`.
- **AI/ML Use Case**: Simplifies access to key prediction metrics.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE VIEW high_score_predictions AS
  SELECT prediction_id, model_id, score, eval_date
  FROM predictions
  WHERE score > 0.9;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE VIEW recent_predictions AS
  SELECT prediction_id, model_id, score, eval_date
  FROM predictions
  WHERE eval_date > '2025-08-01';
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE VIEW model_avg_scores AS
  SELECT model_id, AVG(score) AS avg_score
  FROM predictions
  GROUP BY model_id;
  ```
  </details>

### Project 2: Sales Insights
- **Folder**: `Project2_Sales_Insights/`
- **Concepts**: `CREATE VIEW with JOIN`
- **Description**: Build views combining sales and customer data to provide insights for ML models.
- **Tasks**:
  - Create a view `sales_by_customer` joining `sales_data` and `customers` to show sales per customer.
  - Create a view `active_customer_sales` for sales where customer `activity` > 5.
  - Create a view `regional_sales_summary` joining tables to sum sales by region.
- **AI/ML Use Case**: Prepares joined data for sales prediction models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE VIEW sales_by_customer AS
  SELECT c.customer_id, c.name, s.sale_id, s.amount
  FROM sales_data s
  INNER JOIN customers c ON s.customer_id = c.customer_id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE VIEW active_customer_sales AS
  SELECT c.customer_id, c.name, s.sale_id, s.amount
  FROM sales_data s
  INNER JOIN customers c ON s.customer_id = c.customer_id
  WHERE c.activity > 5;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE VIEW regional_sales_summary AS
  SELECT c.region, SUM(s.amount) AS total_sales
  FROM sales_data s
  INNER JOIN customers c ON s.customer_id = c.customer_id
  GROUP BY c.region;
  ```
  </details>

### Project 3: User Activity View
- **Folder**: `Project3_User_Activity_View/`
- **Concepts**: `CREATE OR REPLACE VIEW`
- **Description**: Update views to reflect changing user activity metrics for a recommendation system.
- **Tasks**:
  - Create a view `active_users` for users with `activity` > 3, then replace it to use `activity` > 4.
  - Create a view `user_regions` for user counts by region, then replace it to include only regions with >5 users.
  - Create a view `user_emails`, then replace it to exclude null emails.
- **AI/ML Use Case**: Keeps user data views current for personalization models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE VIEW active_users AS
  SELECT user_id, email, activity
  FROM users
  WHERE activity > 3;

  CREATE OR REPLACE VIEW active_users AS
  SELECT user_id, email, activity
  FROM users
  WHERE activity > 4;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE VIEW user_regions AS
  SELECT region, COUNT(*) AS user_count
  FROM users
  GROUP BY region;

  CREATE OR REPLACE VIEW user_regions AS
  SELECT region, COUNT(*) AS user_count
  FROM users
  GROUP BY region
  HAVING COUNT(*) > 5;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE VIEW user_emails AS
  SELECT user_id, email
  FROM users;

  CREATE OR REPLACE VIEW user_emails AS
  SELECT user_id, email
  FROM users
  WHERE email IS NOT NULL;
  ```
  </details>

### Project 4: Model Metrics
- **Folder**: `Project4_Model_Metrics/`
- **Concepts**: `Materialized Views`
- **Description**: Create materialized views to persist model performance data for ML analysis.
- **Tasks**:
  - Create a materialized view `model_performance` with average scores by model.
  - Create a materialized view `high_risk_predictions` for predictions with `score` > 0.95.
  - Create a materialized view `monthly_model_stats` for model stats by month.
- **AI/ML Use Case**: Stores performance data for model evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE MATERIALIZED VIEW model_performance AS
  SELECT model_id, AVG(score) AS avg_score, COUNT(*) AS prediction_count
  FROM predictions
  GROUP BY model_id
  WITH DATA;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE MATERIALIZED VIEW high_risk_predictions AS
  SELECT prediction_id, model_id, score, eval_date
  FROM predictions
  WHERE score > 0.95
  WITH DATA;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE MATERIALIZED VIEW monthly_model_stats AS
  SELECT model_id, DATE_FORMAT(eval_date, '%Y-%m') AS eval_month, AVG(score) AS avg_score
  FROM predictions
  GROUP BY model_id, DATE_FORMAT(eval_date, '%Y-%m')
  WITH DATA;
  ```
  </details>

### Project 5: Capstone - Views
- **Folder**: `Project5_Capstone_Views/`
- **Concepts**: All Four (`Basic CREATE VIEW`, `CREATE VIEW with JOIN`, `CREATE OR REPLACE VIEW`, `Materialized Views`)
- **Description**: Design a suite of views for an ML fraud detection pipeline.
- **Tasks**:
  - Create a view `fraud_orders` for orders with `amount` > 200.
  - Create a view `customer_order_details` joining `orders` and `customers`.
  - Create a view `high_risk_customers`, then replace it to tighten risk criteria.
  - Create a materialized view `fraud_stats` for order counts by customer.
  - Create a view `recent_fraud_orders` for orders after '2025-07-10'.
- **AI/ML Use Case**: Simplifies fraud analysis with reusable views.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE VIEW fraud_orders AS
  SELECT order_id, customer_id, amount, order_date
  FROM orders
  WHERE amount > 200;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE VIEW customer_order_details AS
  SELECT o.order_id, o.amount, o.order_date, c.customer_id, c.email
  FROM orders o
  INNER JOIN customers c ON o.customer_id = c.customer_id;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE VIEW high_risk_customers AS
  SELECT customer_id, SUM(amount) AS total_amount
  FROM orders
  GROUP BY customer_id
  HAVING SUM(amount) > 500;

  CREATE OR REPLACE VIEW high_risk_customers AS
  SELECT customer_id, SUM(amount) AS total_amount
  FROM orders
  GROUP BY customer_id
  HAVING SUM(amount) > 1000;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  CREATE MATERIALIZED VIEW fraud_stats AS
  SELECT customer_id, COUNT(*) AS order_count, SUM(amount) AS total_amount
  FROM orders
  GROUP BY customer_id
  WITH DATA;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  CREATE VIEW recent_fraud_orders AS
  SELECT order_id, customer_id, amount, order_date
  FROM orders
  WHERE order_date > '2025-07-10';
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Basic CREATE VIEW`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to verify view outputs.
- **Combine Skills**: Mix `JOIN` and `Materialized Views` for realistic scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more view challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for views? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project creates views based on these tables, testing all four view concepts. Below are schemas and sample data for input tables—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: predictions
- **Used In**: Project 1, Project 4, Project 5 (Capstone)
- **Description**: ML model predictions for view creation.
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
  (1, 101, 0.92, '2025-07-15'),
  (2, 101, 0.87, '2025-07-16'),
  (3, 102, 0.95, '2025-07-17'),
  (4, 102, 0.78, '2025-07-18'),
  (5, 103, 0.91, '2025-07-19'),
  (6, 103, 0.84, '2025-07-20'),
  (7, 104, 0.96, '2025-07-21'),
  (8, 104, 0.80, '2025-07-22'),
  (9, 105, 0.89, '2025-07-23'),
  (10, 105, 0.93, '2025-07-24'),
  (11, 106, 0.77, '2025-07-25'),
  (12, 106, 0.94, '2025-07-26'),
  (13, 107, 0.85, '2025-07-27'),
  (14, 107, 0.90, '2025-07-28'),
  (15, 108, 0.88, '2025-07-29'),
  (16, 108, 0.97, '2025-07-30'),
  (17, 109, 0.79, '2025-07-31'),
  (18, 109, 0.92, '2025-08-01'),
  (19, 110, 0.86, '2025-08-02'),
  (20, 110, 0.91, '2025-08-03');
  ```
- **Notes**: Supports `Basic CREATE VIEW`, `Materialized Views` for prediction metrics.

### Dataset 2: users
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: User data for activity-based views.
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
- **Notes**: Supports `CREATE OR REPLACE VIEW` for user activity metrics.

### Dataset 3: customers
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Customer data for sales-related views.
- **Schema**:
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      name VARCHAR(100),
      region VARCHAR(50),
      activity INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO customers (customer_id, name, region, activity) VALUES
  (201, 'Alice Smith', 'East', 6),
  (202, 'Bob Johnson', 'West', 3),
  (203, 'Carol White', 'South', 5),
  (204, 'Dave Brown', 'North', 2),
  (205, 'Emma Davis', 'East', 7),
  (206, 'Frank Wilson', 'West', 4),
  (207, 'Grace Lee', 'South', 6),
  (208, 'Henry Clark', 'North', 1),
  (209, 'Ivy Taylor', 'East', 5),
  (210, 'Jack Moore', 'West', 3),
  (211, 'Kate Adams', 'South', 4),
  (212, 'Liam Harris', 'North', 6),
  (213, 'Mia Lewis', 'East', 2),
  (214, 'Noah Walker', 'West', 5),
  (215, 'Olivia Young', 'South', 7),
  (216, 'Peter King', 'North', 3),
  (217, 'Quinn Scott', 'East', 4),
  (218, 'Rose Hall', 'West', 6),
  (219, 'Sam Green', 'South', 2),
  (220, 'Tina Baker', 'North', 5);
  ```
- **Notes**: Supports `CREATE VIEW with JOIN` for sales insights.

### Dataset 4: sales_data
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Sales data for view creation.
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
  (121, 201, 110.0, '2025-07-21', 'East'),
  (122, 202, 65.0, '2025-07-22', 'West'),
  (123, 203, 175.0, '2025-07-23', 'South'),
  (124, 204, 35.0, '2025-07-24', 'North'),
  (125, 205, 95.0, '2025-07-25', 'East');
  ```
- **Notes**: Supports `CREATE VIEW with JOIN` for sales analysis.

### Dataset 5: orders
- **Used In**: Project 5 (Capstone)
- **Description**: Order data for fraud detection views.
- **Schema**:
  ```sql
  CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      order_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO orders (order_id, customer_id, amount, order_date) VALUES
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
- **Notes**: Supports `Basic CREATE VIEW`, `CREATE OR REPLACE VIEW`, `Materialized Views` for fraud analysis.

### Setup Instructions
1. **Create Input Tables**: Run the `CREATE TABLE` and `INSERT` statements for `predictions`, `users`, `customers`, `sales_data`, and `orders`.
2. **Generate Views**: Use project tasks to create views (e.g., `high_score_predictions`, `fraud_stats`).
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify view results.
4. **Compatibility**:
   - MySQL: Limited materialized view support; simulate with `CREATE TABLE AS SELECT` or use MariaDB for full support. `DATE_FORMAT` used for monthly grouping.
   - PostgreSQL: Full support for `MATERIALIZED VIEW`; replace `DATE_FORMAT` with `TO_CHAR(eval_date, 'YYYY-MM')`.
   - SQL Server: No native materialized views; use indexed views or tables. Use `FORMAT(eval_date, 'yyyy-MM')` for monthly grouping.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master Views and shine in AI/ML interviews! Happy querying! ✨</p>
</div>