# 📊 Projects - Mastering UPDATE Operations

## 🌟 Overview

Welcome to the **Projects** section for **UPDATE Operations**! 🚀 These five unique projects are your playground to master the four core concepts—`Basic UPDATE`, `UPDATE with WHERE`, `UPDATE with JOIN`, and `UPDATE with Subqueries`. Dive into AI/ML-themed challenges like correcting model predictions or syncing datasets, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL UPDATE operations practical and fun, helping you:
- **Apply Skills**: Modify ML datasets and logs with `UPDATE`.
- **Ace Interviews**: Solve data manipulation problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Clean and update data for model training, analysis, or deployment.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key UPDATE techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Prediction Correction** | Basic UPDATE, UPDATE with WHERE | Correct errors in a `predictions` table by updating scores and dates. |
| **User Activity Update** | UPDATE with WHERE, UPDATE with Subqueries | Update user activity levels in a `users` table based on conditions. |
| **Sales Region Sync** | UPDATE with JOIN | Sync `sales_data` regions with customer data using joins. |
| **Dataset Adjustment** | UPDATE with Subqueries | Adjust `training_data` features using subquery-derived values. |
| **Capstone: Data Cleaning** | All Four | Clean a `customer_orders` table with comprehensive UPDATE operations. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Prediction_Correction/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Basic UPDATE`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Prediction Correction
- **Folder**: `Project1_Prediction_Correction/`
- **Concepts**: `Basic UPDATE`, `UPDATE with WHERE`
- **Description**: Correct errors in a `predictions` table by updating model scores and evaluation dates for an ML pipeline.
- **Tasks**:
  - Update all `score` values to increase by 0.05.
  - Update `eval_date` to '2025-09-01' for `model_id` = 101.
  - Update `score` to 0.9 where `score` is null.
- **AI/ML Use Case**: Fixes model outputs for accurate performance tracking.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  UPDATE predictions
  SET score = score + 0.05;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  UPDATE predictions
  SET eval_date = '2025-09-01'
  WHERE model_id = 101;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  UPDATE predictions
  SET score = 0.9
  WHERE score IS NULL;
  ```
  </details>

### Project 2: User Activity Update
- **Folder**: `Project2_User_Activity_Update/`
- **Concepts**: `UPDATE with WHERE`, `UPDATE with Subqueries`
- **Description**: Update user activity levels in a `users` table based on conditions and subqueries for a recommendation system.
- **Tasks**:
  - Increase `activity` by 1 for users in the 'North' region.
  - Set `activity` to 5 where `user_id` is in a subquery of users with null `email`.
  - Update `activity` to the average `activity` of 'East' users for users with `activity` < 3.
- **AI/ML Use Case**: Refines user data for personalized ML models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  UPDATE users
  SET activity = activity + 1
  WHERE region = 'North';
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  UPDATE users
  SET activity = 5
  WHERE user_id IN (SELECT user_id FROM users WHERE email IS NULL);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  UPDATE users
  SET activity = (SELECT AVG(activity) FROM users WHERE region = 'East')
  WHERE activity < 3;
  ```
  </details>

### Project 3: Sales Region Sync
- **Folder**: `Project3_Sales_Region_Sync/`
- **Concepts**: `UPDATE with JOIN`
- **Description**: Sync regions in a `sales_data` table with customer regions from a `customers` table using joins for data consistency.
- **Tasks**:
  - Update `sales_data` `region` using an INNER JOIN with `customers` on `customer_id`.
  - Update `sales_data` `region` to 'Unknown' for unmatched `customer_id` using a LEFT JOIN.
  - Update `amount` in `sales_data` by 10% for customers with `activity` > 5 via JOIN.
- **AI/ML Use Case**: Ensures consistent data for sales prediction models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  UPDATE sales_data s
  INNER JOIN customers c ON s.customer_id = c.customer_id
  SET s.region = c.region;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  UPDATE sales_data s
  LEFT JOIN customers c ON s.customer_id = c.customer_id
  SET s.region = 'Unknown'
  WHERE c.customer_id IS NULL;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  UPDATE sales_data s
  INNER JOIN customers c ON s.customer_id = c.customer_id
  SET s.amount = s.amount * 1.10
  WHERE c.activity > 5;
  ```
  </details>

### Project 4: Dataset Adjustment
- **Folder**: `Project4_Dataset_Adjustment/`
- **Concepts**: `UPDATE with Subqueries`
- **Description**: Adjust features in a `training_data` table using values derived from subqueries for ML dataset preparation.
- **Tasks**:
  - Update `feature1` to the average `feature1` where `label` is 'negative'.
  - Update `feature2` to the maximum `feature2` from rows with `label` = 'positive'.
  - Update `label` to 'unknown' where `feature1` is less than the minimum `feature1` of all rows.
- **AI/ML Use Case**: Normalizes data for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  UPDATE training_data
  SET feature1 = (SELECT AVG(feature1) FROM training_data WHERE label = 'negative')
  WHERE label = 'negative';
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  UPDATE training_data
  SET feature2 = (SELECT MAX(feature2) FROM training_data WHERE label = 'positive');
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  UPDATE training_data
  SET label = 'unknown'
  WHERE feature1 < (SELECT MIN(feature1) FROM training_data);
  ```
  </details>

### Project 5: Capstone - Data Cleaning
- **Folder**: `Project5_Capstone_Data_Cleaning/`
- **Concepts**: All Four (`Basic UPDATE`, `UPDATE with WHERE`, `UPDATE with JOIN`, `UPDATE with Subqueries`)
- **Description**: Clean a `customer_orders` table with comprehensive UPDATE operations for an ML fraud detection pipeline.
- **Tasks**:
  - Update all `amount` values to round to 2 decimal places.
  - Update `order_date` to '2025-09-01' for orders with `amount` < 10.
  - Update `customer_id` using a JOIN with `sales_data` to align IDs.
  - Update `amount` to the average `amount` from orders with `customer_id` not null using a subquery.
  - Update `amount` to 0 where `customer_id` is null and `order_date` is before '2025-08-01'.
- **AI/ML Use Case**: Prepares clean order data for fraud analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  UPDATE customer_orders
  SET amount = ROUND(amount, 2);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  UPDATE customer_orders
  SET order_date = '2025-09-01'
  WHERE amount < 10;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  UPDATE customer_orders co
  INNER JOIN sales_data s ON co.order_id = s.sale_id
  SET co.customer_id = s.customer_id;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  UPDATE customer_orders
  SET amount = (SELECT AVG(amount) FROM customer_orders WHERE customer_id IS NOT NULL)
  WHERE customer_id IS NOT NULL;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  UPDATE customer_orders
  SET amount = 0
  WHERE customer_id IS NULL AND order_date < '2025-08-01';
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Basic UPDATE`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix `JOIN` and `Subqueries` for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for UPDATE operations? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all four UPDATE concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: predictions
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML model predictions for score and date corrections.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      model_id INT PRIMARY KEY,
      score FLOAT,
      eval_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO predictions (model_id, score, eval_date) VALUES
  (101, 0.92, '2025-08-01'),
  (102, NULL, '2025-08-01'),
  (103, 0.87, '2025-08-02'),
  (104, 0.95, '2025-08-02'),
  (105, 0.78, '2025-08-03'),
  (106, 0.91, '2025-08-03'),
  (107, NULL, '2025-08-04'),
  (108, 0.84, '2025-08-04'),
  (109, 0.96, '2025-08-05'),
  (110, 0.80, '2025-08-05'),
  (111, 0.89, '2025-08-06'),
  (112, 0.93, '2025-08-06'),
  (113, NULL, '2025-08-07'),
  (114, 0.77, '2025-08-07'),
  (115, 0.94, '2025-08-08'),
  (116, 0.85, '2025-08-08'),
  (117, 0.90, '2025-08-09'),
  (118, NULL, '2025-08-09'),
  (119, 0.88, '2025-08-10'),
  (120, 0.97, '2025-08-10');
  ```
- **Notes**: Supports `Basic UPDATE` (score adjustments), `WHERE` (specific IDs).

### Dataset 2: users
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: User data for activity updates.
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
  (102, NULL, 'South', 2),
  (103, 'mike@outlook.com', 'East', 6),
  (104, 'sara@gmail.com', 'West', 1),
  (105, 'tom@company.com', 'North', 5),
  (106, NULL, 'South', 3),
  (107, 'mark@outlook.com', 'East', 7),
  (108, 'anna@gmail.com', 'West', 2),
  (109, 'paul@company.com', 'North', 4),
  (110, 'emma@yahoo.com', 'South', 6),
  (111, NULL, 'East', 3),
  (112, 'clara@gmail.com', 'West', 5),
  (113, 'steve@company.com', 'North', 2),
  (114, 'lucy@yahoo.com', 'South', 4),
  (115, 'peter@outlook.com', 'East', 6),
  (116, NULL, 'West', 1),
  (117, 'nick@company.com', 'North', 5),
  (118, 'zoe@yahoo.com', 'South', 3),
  (119, 'ben@outlook.com', 'East', 7),
  (120, 'kate@gmail.com', 'West', 2),
  (121, 'lily@company.com', 'North', 4),
  (122, NULL, 'South', 6),
  (123, 'jack@outlook.com', 'East', 3),
  (124, 'rose@gmail.com', 'West', 5),
  (125, 'sam@yahoo.com', 'North', 2);
  ```
- **Notes**: Supports `WHERE` (region-based), `Subqueries` (email checks).

### Dataset 3: customers
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Customer data for syncing with sales.
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
- **Notes**: Supports `JOIN` (region syncing).

### Dataset 4: sales_data
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Sales data for region and amount updates.
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
  (101, 201, 50.0, '2025-08-01', NULL),
  (102, NULL, 150.5, '2025-08-02', 'West'),
  (103, 202, 25.0, '2025-08-03', NULL),
  (104, 203, 200.0, '2025-08-04', 'South'),
  (105, 204, 75.3, '2025-08-05', NULL),
  (106, NULL, 300.0, '2025-08-06', 'North'),
  (107, 205, 40.0, '2025-08-07', NULL),
  (108, 206, 120.7, '2025-08-08', 'East'),
  (109, 207, 90.5, '2025-08-09', NULL),
  (110, NULL, 60.0, '2025-08-10', 'West'),
  (111, 208, 250.0, '2025-08-11', NULL),
  (112, 209, 30.0, '2025-08-12', 'South'),
  (113, 210, 180.0, '2025-08-13', NULL),
  (114, NULL, 45.0, '2025-08-14', 'North'),
  (115, 211, 100.0, '2025-08-15', NULL),
  (116, 212, 70.5, '2025-08-16', 'East'),
  (117, 213, 200.5, '2025-08-17', NULL),
  (118, NULL, 55.0, '2025-08-18', 'West'),
  (119, 214, 130.0, '2025-08-19', NULL),
  (120, 215, 85.0, '2025-08-20', 'South'),
  (121, 216, 110.0, '2025-08-21', NULL),
  (122, NULL, 65.0, '2025-08-22', 'North'),
  (123, 217, 175.0, '2025-08-23', NULL),
  (124, 218, 35.0, '2025-08-24', 'East'),
  (125, 219, 95.0, '2025-08-25', NULL);
  ```
- **Notes**: Supports `JOIN` (region sync), `WHERE` (amount updates).

### Dataset 5: training_data
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: ML training data for feature adjustments.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label) VALUES
  (101, 0.5, 1.8, 'positive'),
  (102, 1.2, 2.5, 'negative'),
  (103, 2.3, 3.1, 'positive'),
  (104, 0.8, 1.4, 'negative'),
  (105, 1.9, 2.9, 'positive'),
  (106, 0.3, 1.7, 'negative'),
  (107, 2.1, 3.4, 'positive'),
  (108, 1.0, 2.0, 'negative'),
  (109, 1.6, 2.6, 'positive'),
  (110, 0.7, 1.9, 'negative'),
  (111, 2.4, 3.2, 'positive'),
  (112, 0.9, 1.5, 'negative'),
  (113, 1.8, 2.8, 'positive'),
  (114, 0.4, 1.3, 'negative'),
  (115, 2.0, 3.0, 'positive'),
  (116, 0.8, 1.7, 'negative'),
  (117, 1.7, 2.7, 'positive'),
  (118, 0.6, 1.6, 'negative'),
  (119, 2.2, 3.3, 'positive'),
  (120, 0.5, 1.9, 'negative');
  ```
- **Notes**: Supports `Subqueries` (feature updates).

### Dataset 6: customer_orders
- **Used In**: Project 5 (Capstone)
- **Description**: Customer orders for comprehensive cleaning.
- **Schema**:
  ```sql
  CREATE TABLE customer_orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      order_date DATE
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date) VALUES
  (101, 301, 80.123, '2025-07-01'),
  (102, NULL, 120.456, '2025-07-02'),
  (103, 302, 5.789, '2025-07-03'),
  (104, 303, 250.0, '2025-07-04'),
  (105, 304, 65.321, '2025-07-05'),
  (106, NULL, 400.987, '2025-07-06'),
  (107, 305, 8.654, '2025-07-07'),
  (108, 306, 110.789, '2025-07-08'),
  (109, 307, 70.456, '2025-07-09'),
  (110, NULL, 50.123, '2025-07-10'),
  (111, 308, 200.0, '2025-07-11'),
  (112, 309, 20.987, '2025-07-12'),
  (113, 310, 160.654, '2025-07-13'),
  (114, NULL, 35.321, '2025-07-14'),
  (115, 311, 90.789, '2025-07-15'),
  (116, 312, 60.456, '2025-07-16'),
  (117, 313, 180.123, '2025-07-17'),
  (118, NULL, 45.987, '2025-07-18'),
  (119, 314, 100.654, '2025-07-19'),
  (120, 315, 75.321, '2025-07-20'),
  (121, 316, 110.789, '2025-07-21'),
  (122, NULL, 65.456, '2025-07-22'),
  (123, 317, 175.123, '2025-07-23'),
  (124, 318, 9.987, '2025-07-24'),
  (125, 319, 95.654, '2025-07-25');
  ```
- **Notes**: Supports all concepts for cleaning tasks.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` statements in your database.
2. **Load Data**: Copy-paste the `INSERT` statements or save as a `.sql` file and import.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to avoid production risks.
4. **Compatibility**:
   - MySQL: Add `AUTO_INCREMENT` to `PRIMARY KEY` if needed (e.g., `id INT PRIMARY KEY AUTO_INCREMENT`).
   - PostgreSQL: Use `SERIAL PRIMARY KEY` for IDs. `UPDATE` syntax is standard.
   - SQL Server: Use `TOP` with `UPDATE` if limiting rows; standard syntax otherwise.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master UPDATE Operations and shine in AI/ML interviews! Happy querying! ✨</p>
</div>