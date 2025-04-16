# 📊 Projects - Mastering INSERT Operations

## 🌟 Overview

Welcome to the **Projects** section for **INSERT Operations**! 🚀 These five unique projects are your playground to master the four core concepts—`Basic INSERT`, `INSERT with SELECT`, `INSERT with Multiple Rows`, and `INSERT with Default/Null Values`. Dive into AI/ML-themed challenges like logging model predictions or populating datasets, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL INSERT operations practical and fun, helping you:
- **Apply Skills**: Populate ML datasets and logs with `INSERT`.
- **Ace Interviews**: Solve data manipulation problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Create and manage data for model training, logging, or analysis.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key INSERT techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Logging** | Basic INSERT, INSERT with Default/Null Values | Log ML model predictions into a `predictions` table with single inserts. |
| **Dataset Migration** | INSERT with SELECT | Migrate data from a `training_data_temp` table to `training_data` using `INSERT with SELECT`. |
| **Bulk User Import** | INSERT with Multiple Rows | Import multiple user records into a `users` table in a single query. |
| **Sales Initialization** | Basic INSERT, INSERT with Default/Null Values | Initialize a `sales_data` table with sales records, handling nulls and defaults. |
| **Capstone: Data Population** | All Four | Populate a `customer_orders` table with varied INSERT methods for an ML pipeline. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Logging/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Basic INSERT`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Logging
- **Folder**: `Project1_Model_Logging/`
- **Concepts**: `Basic INSERT`, `INSERT with Default/Null Values`
- **Description**: Log ML model predictions into a `predictions` table, using single-row inserts and handling nulls or defaults for incomplete data.
- **Tasks**:
  - Insert a single prediction with `model_id`, `score`, and `eval_date`.
  - Insert a prediction with a null `score` to represent a failed run.
  - Insert a prediction using default `eval_date` (CURRENT_DATE).
- **AI/ML Use Case**: Logs model outputs for performance tracking.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  INSERT INTO predictions (model_id, score, eval_date)
  VALUES (1, 0.95, '2025-08-01');
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  INSERT INTO predictions (model_id, score, eval_date)
  VALUES (2, NULL, '2025-08-01');
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO predictions (model_id, score, eval_date)
  VALUES (3, 0.88, CURRENT_DATE);
  ```
  </details>

### Project 2: Dataset Migration
- **Folder**: `Project2_Dataset_Migration/`
- **Concepts**: `INSERT with SELECT`
- **Description**: Migrate data from a temporary `training_data_temp` table to a permanent `training_data` table using `INSERT with SELECT` for ML dataset preparation.
- **Tasks**:
  - Insert all rows from `training_data_temp` into `training_data`.
  - Insert rows from `training_data_temp` where `label` is not null.
  - Insert selected columns (`feature1`, `label`) from `training_data_temp` with a default `feature2`.
- **AI/ML Use Case**: Prepares clean datasets for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label)
  SELECT id, feature1, feature2, label
  FROM training_data_temp;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label)
  SELECT id, feature1, feature2, label
  FROM training_data_temp
  WHERE label IS NOT NULL;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label)
  SELECT id, feature1, 0.0, label
  FROM training_data_temp;
  ```
  </details>

### Project 3: Bulk User Import
- **Folder**: `Project3_Bulk_User_Import/`
- **Concepts**: `INSERT with Multiple Rows`
- **Description**: Import multiple user records into a `users` table in a single query to populate a recommendation system.
- **Tasks**:
  - Insert 3 user records in one `INSERT` statement.
  - Insert 5 user records with varying `activity` values.
  - Insert multiple users with null `region` for later updates.
- **AI/ML Use Case**: Populates user data for personalization models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  INSERT INTO users (user_id, email, region, activity)
  VALUES
      (1, 'alice@gmail.com', 'North', 5),
      (2, 'bob@yahoo.com', 'South', 3),
      (3, 'carol@outlook.com', 'East', 6);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  INSERT INTO users (user_id, email, region, activity)
  VALUES
      (4, 'dave@gmail.com', 'West', 2),
      (5, 'emma@yahoo.com', 'North', 7),
      (6, 'frank@company.com', 'South', 4),
      (7, 'grace@gmail.com', 'East', 8),
      (8, 'henry@outlook.com', 'West', 1);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO users (user_id, email, region, activity)
  VALUES
      (9, 'ivy@yahoo.com', NULL, 5),
      (10, 'jack@gmail.com', NULL, 3),
      (11, 'kate@company.com', NULL, 6);
  ```
  </details>

### Project 4: Sales Initialization
- **Folder**: `Project4_Sales_Initialization/`
- **Concepts**: `Basic INSERT`, `INSERT with Default/Null Values`
- **Description**: Initialize a `sales_data` table with sales records, handling nulls and defaults for an ML sales prediction model.
- **Tasks**:
  - Insert a single sale with all columns specified.
  - Insert a sale with null `customer_id` for anonymous purchases.
  - Insert a sale using default `sale_date` (CURRENT_DATE).
- **AI/ML Use Case**: Sets up sales data for forecasting models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date, region)
  VALUES (1, 101, 50.0, '2025-08-01', 'East');
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date, region)
  VALUES (2, NULL, 150.5, '2025-08-02', 'West');
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date, region)
  VALUES (3, 102, 25.0, CURRENT_DATE, 'South');
  ```
  </details>

### Project 5: Capstone - Data Population
- **Folder**: `Project5_Capstone_Data_Population/`
- **Concepts**: All Four (`Basic INSERT`, `INSERT with SELECT`, `INSERT with Multiple Rows`, `INSERT with Default/Null Values`)
- **Description**: Populate a `customer_orders` table with varied INSERT methods to prepare data for an ML fraud detection pipeline.
- **Tasks**:
  - Insert a single order with all columns specified.
  - Insert multiple orders (3 rows) in one statement.
  - Use `INSERT with SELECT` to copy orders from `sales_data` with `amount` > 100.
  - Insert an order with null `customer_id` and default `order_date`.
  - Combine methods to insert 2 orders, one with null `amount`.
- **AI/ML Use Case**: Prepares order data for fraud analysis models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date)
  VALUES (1, 201, 75.3, '2025-08-01');
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date)
  VALUES
      (2, 202, 200.0, '2025-08-02'),
      (3, 203, 30.0, '2025-08-03'),
      (4, 204, 120.7, '2025-08-04');
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date)
  SELECT sale_id + 100, customer_id, amount, sale_date
  FROM sales_data
  WHERE amount > 100;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date)
  VALUES (5, NULL, 60.0, CURRENT_DATE);
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date)
  VALUES
      (6, 205, NULL, '2025-08-05'),
      (7, 206, 90.5, CURRENT_DATE);
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Basic INSERT`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix `INSERT with SELECT` and `Multiple Rows` for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for INSERT operations? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all four INSERT concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: predictions
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML model predictions for logging new results.
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
  (101, 0.92, '2025-07-01'),
  (102, 0.87, '2025-07-01'),
  (103, 0.95, '2025-07-02'),
  (104, 0.78, '2025-07-02'),
  (105, 0.91, '2025-07-03'),
  (106, 0.84, '2025-07-03'),
  (107, 0.96, '2025-07-04'),
  (108, 0.80, '2025-07-04'),
  (109, 0.89, '2025-07-05'),
  (110, 0.93, '2025-07-05'),
  (111, 0.77, '2025-07-06'),
  (112, 0.94, '2025-07-06'),
  (113, 0.85, '2025-07-07'),
  (114, 0.90, '2025-07-07'),
  (115, 0.88, '2025-07-08'),
  (116, 0.97, '2025-07-08'),
  (117, 0.79, '2025-07-09'),
  (118, 0.92, '2025-07-09'),
  (119, 0.86, '2025-07-10'),
  (120, 0.91, '2025-07-10');
  ```
- **Notes**: Supports `Basic INSERT` (new predictions), `Default/Null Values` (null `score`).

### Dataset 2: training_data_temp
- **Used In**: Project 2
- **Description**: Temporary ML training data for migration.
- **Schema**:
  ```sql
  CREATE TABLE training_data_temp (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO training_data_temp (id, feature1, feature2, label) VALUES
  (1, 0.5, 1.8, 'positive'),
  (2, 1.2, 2.5, NULL),
  (3, 2.3, 3.1, 'negative'),
  (4, 0.8, 1.4, 'positive'),
  (5, 1.9, 2.9, 'negative'),
  (6, 0.3, 1.7, NULL),
  (7, 2.1, 3.4, 'positive'),
  (8, 1.0, 2.0, 'negative'),
  (9, 1.6, 2.6, 'positive'),
  (10, 0.7, 1.9, NULL),
  (11, 2.4, 3.2, 'negative'),
  (12, 0.9, 1.5, 'positive'),
  (13, 1.8, 2.8, 'negative'),
  (14, 0.4, 1.3, 'positive'),
  (15, 2.0, 3.0, NULL),
  (16, 1.1, 2.4, 'positive'),
  (17, 0.6, 1.6, 'negative'),
  (18, 2.2, 3.3, 'positive'),
  (19, 0.8, 1.8, NULL),
  (20, 1.7, 2.7, 'negative'),
  (21, 0.5, 1.9, 'positive'),
  (22, 2.5, 3.5, 'negative'),
  (23, 1.3, 2.2, 'positive'),
  (24, 0.9, 1.4, NULL),
  (25, 1.5, 2.5, 'positive');
  ```
- **Notes**: Supports `INSERT with SELECT` (data migration).

### Dataset 3: training_data
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Permanent ML training data for migrated records.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (20 rows, initially populated for context):
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label) VALUES
  (101, 1.5, 2.3, 'positive'),
  (102, 0.8, 1.9, 'negative'),
  (103, 2.1, 3.0, 'positive'),
  (104, 0.4, 1.2, 'negative'),
  (105, 1.7, 2.8, 'positive'),
  (106, 0.9, 1.5, 'negative'),
  (107, 2.3, 3.2, 'positive'),
  (108, 0.6, 1.0, 'negative'),
  (109, 1.9, 2.7, 'positive'),
  (110, 0.5, 1.4, 'negative'),
  (111, 2.0, 3.1, 'positive'),
  (112, 0.7, 1.8, 'negative'),
  (113, 1.6, 2.9, 'positive'),
  (114, 0.3, 1.1, 'negative'),
  (115, 2.2, 3.3, 'positive'),
  (116, 0.8, 1.7, 'negative'),
  (117, 1.8, 2.6, 'positive'),
  (118, 0.4, 1.3, 'negative'),
  (119, 2.4, 3.4, 'positive'),
  (120, 0.9, 1.6, 'negative');
  ```
- **Notes**: Receives data via `INSERT with SELECT`.

### Dataset 4: users
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: User data for bulk imports.
- **Schema**:
  ```sql
  CREATE TABLE users (
      user_id INT PRIMARY KEY,
      email VARCHAR(100),
      region VARCHAR(50),
      activity INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO users (user_id, email, region, activity) VALUES
  (101, 'john@gmail.com', 'North', 4),
  (102, 'jane@yahoo.com', 'South', 2),
  (103, 'mike@outlook.com', 'East', 6),
  (104, 'sara@gmail.com', 'West', 3),
  (105, 'tom@company.com', 'North', 5),
  (106, 'lisa@yahoo.com', 'South', 1),
  (107, 'mark@outlook.com', 'East', 7),
  (108, 'anna@gmail.com', 'West', 4),
  (109, 'paul@company.com', 'North', 2),
  (110, 'emma@yahoo.com', 'South', 6),
  (111, 'david@outlook.com', 'East', 3),
  (112, 'clara@gmail.com', 'West', 5),
  (113, 'steve@company.com', 'North', 4),
  (114, 'lucy@yahoo.com', 'South', 2),
  (115, 'peter@outlook.com', 'East', 6),
  (116, 'mary@gmail.com', 'West', 3),
  (117, 'nick@company.com', 'North', 5),
  (118, 'zoe@yahoo.com', 'South', 1),
  (119, 'ben@outlook.com', 'East', 7),
  (120, 'kate@gmail.com', 'West', 4);
  ```
- **Notes**: Supports `INSERT with Multiple Rows`, `Default/Null Values`.

### Dataset 5: sales_data
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Sales data for initialization.
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
  (102, NULL, 150.5, '2025-07-02', 'West'),
  (103, 202, 25.0, '2025-07-03', 'South'),
  (104, 203, 200.0, '2025-07-04', 'North'),
  (105, 204, 75.3, '2025-07-05', 'East'),
  (106, NULL, 300.0, '2025-07-06', 'West'),
  (107, 205, 40.0, '2025-07-07', 'South'),
  (108, 206, 120.7, '2025-07-08', 'North'),
  (109, 207, 90.5, '2025-07-09', 'East'),
  (110, NULL, 60.0, '2025-07-10', 'West'),
  (111, 208, 250.0, '2025-07-11', 'South'),
  (112, 209, 30.0, '2025-07-12', 'North'),
  (113, 210, 180.0, '2025-07-13', 'East'),
  (114, NULL, 45.0, '2025-07-14', 'West'),
  (115, 211, 100.0, '2025-07-15', 'South'),
  (116, 212, 70.5, '2025-07-16', 'North'),
  (117, 213, 200.5, '2025-07-17', 'East'),
  (118, NULL, 55.0, '2025-07-18', 'West'),
  (119, 214, 130.0, '2025-07-19', 'South'),
  (120, 215, 85.0, '2025-07-20', 'North'),
  (121, 216, 110.0, '2025-07-21', 'East'),
  (122, NULL, 65.0, '2025-07-22', 'West'),
  (123, 217, 175.0, '2025-07-23', 'South'),
  (124, 218, 35.0, '2025-07-24', 'North'),
  (125, 219, 95.0, '2025-07-25', 'East');
  ```
- **Notes**: Supports `Basic INSERT`, `Default/Null Values`.

### Dataset 6: customer_orders
- **Used In**: Project 5 (Capstone)
- **Description**: Customer orders for comprehensive population.
- **Schema**:
  ```sql
  CREATE TABLE customer_orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      order_date DATE
  );
  ```
- **Sample Data** (20 rows, initially populated for context):
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
- **Notes**: Supports all four concepts for varied inserts.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` statements in your database.
2. **Load Data**: Copy-paste the `INSERT` statements or save as a `.sql` file and import.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to avoid production risks.
4. **Compatibility**:
   - MySQL: Add `AUTO_INCREMENT` to `PRIMARY KEY` if needed (e.g., `id INT PRIMARY KEY AUTO_INCREMENT`).
   - PostgreSQL: Use `SERIAL PRIMARY KEY` for auto-incrementing IDs if preferred.
   - SQL Server: Standard syntax works; ensure date format is `YYYY-MM-DD`.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master INSERT Operations and shine in AI/ML interviews! Happy querying! ✨</p>
</div>