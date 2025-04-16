# 📊 Projects - Mastering DELETE Operations

## 🌟 Overview

Welcome to the **Projects** section for **DELETE Operations**! 🚀 These five unique projects are your playground to master the four core concepts—`Basic DELETE`, `DELETE with WHERE`, `DELETE with JOIN`, and `DELETE with Subqueries`. Dive into AI/ML-themed challenges like cleaning datasets or purging invalid records, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL DELETE operations practical and fun, helping you:
- **Apply Skills**: Prune ML datasets and logs with `DELETE`.
- **Ace Interviews**: Solve data cleanup problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Remove noise from data for model training, analysis, or deployment.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key DELETE techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Prediction Cleanup** | Basic DELETE, DELETE with WHERE | Remove outdated or invalid predictions from a `predictions` table. |
| **User Pruning** | DELETE with WHERE, DELETE with Subqueries | Delete inactive or incomplete user records from a `users` table. |
| **Sales Purge** | DELETE with JOIN | Purge `sales_data` records linked to inactive customers. |
| **Dataset Filtering** | DELETE with Subqueries | Remove outliers from a `training_data` table using subqueries. |
| **Capstone: Data Purification** | All Four | Purify a `customer_orders` table with comprehensive DELETE operations. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Prediction_Cleanup/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Basic DELETE`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Prediction Cleanup
- **Folder**: `Project1_Prediction_Cleanup/`
- **Concepts**: `Basic DELETE`, `DELETE with WHERE`
- **Description**: Remove outdated or invalid predictions from a `predictions` table to streamline an ML pipeline.
- **Tasks**:
  - Delete all predictions with null `score`.
  - Delete predictions where `eval_date` is before '2025-08-01'.
  - Delete predictions for `model_id` = 101.
- **AI/ML Use Case**: Cleans model outputs for accurate performance analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELETE FROM predictions
  WHERE score IS NULL;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELETE FROM predictions
  WHERE eval_date < '2025-08-01';
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELETE FROM predictions
  WHERE model_id = 101;
  ```
  </details>

### Project 2: User Pruning
- **Folder**: `Project2_User_Pruning/`
- **Concepts**: `DELETE with WHERE`, `DELETE with Subqueries`
- **Description**: Delete inactive or incomplete user records from a `users` table to refine a recommendation system dataset.
- **Tasks**:
  - Delete users with `activity` = 0.
  - Delete users where `user_id` is in a subquery of users with null `email`.
  - Delete users in 'South' with `activity` < 3.
- **AI/ML Use Case**: Removes noise for personalized ML models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELETE FROM users
  WHERE activity = 0;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELETE FROM users
  WHERE user_id IN (SELECT user_id FROM users WHERE email IS NULL);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELETE FROM users
  WHERE region = 'South' AND activity < 3;
  ```
  </details>

### Project 3: Sales Purge
- **Folder**: `Project3_Sales_Purge/`
- **Concepts**: `DELETE with JOIN`
- **Description**: Purge `sales_data` records linked to inactive customers to maintain data quality for sales predictions.
- **Tasks**:
  - Delete `sales_data` records for customers with `activity` < 3 using an INNER JOIN.
  - Delete `sales_data` records with no matching `customer_id` using a LEFT JOIN.
  - Delete `sales_data` records for customers in 'West' via JOIN.
- **AI/ML Use Case**: Ensures clean data for forecasting models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELETE s FROM sales_data s
  INNER JOIN customers c ON s.customer_id = c.customer_id
  WHERE c.activity < 3;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELETE s FROM sales_data s
  LEFT JOIN customers c ON s.customer_id = c.customer_id
  WHERE c.customer_id IS NULL;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELETE s FROM sales_data s
  INNER JOIN customers c ON s.customer_id = c.customer_id
  WHERE c.region = 'West';
  ```
  </details>

### Project 4: Dataset Filtering
- **Folder**: `Project4_Dataset_Filtering/`
- **Concepts**: `DELETE with Subqueries`
- **Description**: Remove outliers from a `training_data` table using subqueries to prepare a clean ML dataset.
- **Tasks**:
  - Delete rows where `feature1` exceeds the average `feature1` of 'positive' labels.
  - Delete rows where `feature2` is less than the minimum `feature2` from all rows.
  - Delete rows with null `label` using a subquery to confirm `id` exists.
- **AI/ML Use Case**: Filters noise for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELETE FROM training_data
  WHERE feature1 > (SELECT AVG(feature1) FROM training_data WHERE label = 'positive');
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELETE FROM training_data
  WHERE feature2 < (SELECT MIN(feature2) FROM training_data);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELETE FROM training_data
  WHERE label IS NULL
  AND id IN (SELECT id FROM training_data);
  ```
  </details>

### Project 5: Capstone - Data Purification
- **Folder**: `Project5_Capstone_Data_Purification/`
- **Concepts**: All Four (`Basic DELETE`, `DELETE with WHERE`, `DELETE with JOIN`, `DELETE with Subqueries`)
- **Description**: Purify a `customer_orders` table with comprehensive DELETE operations for an ML fraud detection pipeline.
- **Tasks**:
  - Delete all orders with `amount` = 0.
  - Delete orders where `order_date` is before '2025-07-01'.
  - Delete orders with no matching `customer_id` in `sales_data` using a JOIN.
  - Delete orders where `amount` exceeds the average `amount` from a subquery.
  - Delete orders with null `customer_id` and `amount` < 10.
- **AI/ML Use Case**: Prepares clean order data for fraud analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELETE FROM customer_orders
  WHERE amount = 0;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELETE FROM customer_orders
  WHERE order_date < '2025-07-01';
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELETE co FROM customer_orders co
  LEFT JOIN sales_data s ON co.customer_id = s.customer_id
  WHERE s.customer_id IS NULL;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  DELETE FROM customer_orders
  WHERE amount > (SELECT AVG(amount) FROM customer_orders);
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  DELETE FROM customer_orders
  WHERE customer_id IS NULL AND amount < 10;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Basic DELETE`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix `JOIN` and `Subqueries` for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for DELETE operations? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all four DELETE concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: predictions
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML model predictions for cleanup.
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
  (101, 0.92, '2025-07-15'),
  (102, NULL, '2025-07-16'),
  (103, 0.87, '2025-07-17'),
  (104, 0.95, '2025-07-18'),
  (105, 0.78, '2025-07-19'),
  (106, NULL, '2025-07-20'),
  (107, 0.91, '2025-07-21'),
  (108, 0.84, '2025-07-22'),
  (109, 0.96, '2025-07-23'),
  (110, NULL, '2025-07-24'),
  (111, 0.89, '2025-07-25'),
  (112, 0.93, '2025-07-26'),
  (113, 0.77, '2025-07-27'),
  (114, NULL, '2025-07-28'),
  (115, 0.94, '2025-07-29'),
  (116, 0.85, '2025-07-30'),
  (117, 0.90, '2025-07-31'),
  (118, 0.88, '2025-08-01'),
  (119, NULL, '2025-08-02'),
  (120, 0.97, '2025-08-03');
  ```
- **Notes**: Supports `Basic DELETE` (null scores), `WHERE` (date/model ID).

### Dataset 2: users
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: User data for pruning.
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
  (102, NULL, 'South', 0),
  (103, 'mike@outlook.com', 'East', 6),
  (104, 'sara@gmail.com', 'West', 2),
  (105, 'tom@company.com', 'North', 5),
  (106, NULL, 'South', 1),
  (107, 'mark@outlook.com', 'East', 7),
  (108, 'anna@gmail.com', 'West', 0),
  (109, 'paul@company.com', 'North', 3),
  (110, 'emma@yahoo.com', 'South', 4),
  (111, NULL, 'East', 2),
  (112, 'clara@gmail.com', 'West', 5),
  (113, 'steve@company.com', 'North', 0),
  (114, 'lucy@yahoo.com', 'South', 2),
  (115, 'peter@outlook.com', 'East', 6),
  (116, NULL, 'West', 1),
  (117, 'nick@company.com', 'North', 4),
  (118, 'zoe@yahoo.com', 'South', 0),
  (119, 'ben@outlook.com', 'East', 7),
  (120, 'kate@gmail.com', 'West', 3),
  (121, 'lily@company.com', 'North', 5),
  (122, NULL, 'South', 2),
  (123, 'jack@outlook.com', 'East', 4),
  (124, 'rose@gmail.com', 'West', 0),
  (125, 'sam@yahoo.com', 'North', 6);
  ```
- **Notes**: Supports `WHERE` (activity/region), `Subqueries` (email checks).

### Dataset 3: customers
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Customer data for sales purge.
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
  (202, 'Bob Johnson', 'West', 2),
  (203, 'Carol White', 'South', 4),
  (204, 'Dave Brown', 'North', 1),
  (205, 'Emma Davis', 'East', 5),
  (206, 'Frank Wilson', 'West', 3),
  (207, 'Grace Lee', 'South', 6),
  (208, 'Henry Clark', 'North', 2),
  (209, 'Ivy Taylor', 'East', 4),
  (210, 'Jack Moore', 'West', 1),
  (211, 'Kate Adams', 'South', 5),
  (212, 'Liam Harris', 'North', 3),
  (213, 'Mia Lewis', 'East', 6),
  (214, 'Noah Walker', 'West', 2),
  (215, 'Olivia Young', 'South', 4),
  (216, 'Peter King', 'North', 1),
  (217, 'Quinn Scott', 'East', 5),
  (218, 'Rose Hall', 'West', 3),
  (219, 'Sam Green', 'South', 6),
  (220, 'Tina Baker', 'North', 2);
  ```
- **Notes**: Supports `JOIN` (activity/region checks).

### Dataset 4: sales_data
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Sales data for purging.
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
- **Notes**: Supports `JOIN` (customer checks), `WHERE` (amount/date).

### Dataset 5: training_data
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: ML training data for filtering.
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
  (102, 1.2, 2.5, NULL),
  (103, 2.3, 3.1, 'negative'),
  (104, 0.8, 1.4, 'positive'),
  (105, 1.9, 2.9, NULL),
  (106, 0.3, 1.7, 'negative'),
  (107, 2.1, 3.4, 'positive'),
  (108, 1.0, 2.0, NULL),
  (109, 1.6, 2.6, 'positive'),
  (110, 0.7, 1.9, 'negative'),
  (111, 2.4, 3.2, NULL),
  (112, 0.9, 1.5, 'positive'),
  (113, 1.8, 2.8, 'negative'),
  (114, 0.4, 1.3, NULL),
  (115, 2.0, 3.0, 'positive'),
  (116, 0.8, 1.7, 'negative'),
  (117, 1.7, 2.7, NULL),
  (118, 0.6, 1.6, 'positive'),
  (119, 2.2, 3.3, 'negative'),
  (120, 0.5, 1.9, NULL);
  ```
- **Notes**: Supports `Subqueries` (feature/label checks).

### Dataset 6: customer_orders
- **Used In**: Project 5 (Capstone)
- **Description**: Customer orders for purification.
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
  (101, 301, 80.0, '2025-06-15'),
  (102, NULL, 0.0, '2025-06-16'),
  (103, 302, 120.5, '2025-06-17'),
  (104, 303, 5.0, '2025-06-18'),
  (105, 304, 250.0, '2025-06-19'),
  (106, NULL, 65.3, '2025-06-20'),
  (107, 305, 0.0, '2025-06-21'),
  (108, 306, 400.0, '2025-06-22'),
  (109, 307, 30.0, '2025-06-23'),
  (110, NULL, 110.7, '2025-06-24'),
  (111, 308, 70.5, '2025-06-25'),
  (112, 309, 50.0, '2025-06-26'),
  (113, 310, 200.0, '2025-06-27'),
  (114, NULL, 8.0, '2025-06-28'),
  (115, 311, 20.0, '2025-06-29'),
  (116, 312, 160.0, '2025-06-30'),
  (117, 313, 90.0, '2025-07-01'),
  (118, NULL, 0.0, '2025-07-02'),
  (119, 314, 60.5, '2025-07-03'),
  (120, 315, 180.5, '2025-07-04'),
  (121, 316, 45.0, '2025-07-05'),
  (122, NULL, 100.0, '2025-07-06'),
  (123, 317, 75.0, '2025-07-07'),
  (124, 318, 110.0, '2025-07-08'),
  (125, 319, 65.0, '2025-07-09');
  ```
- **Notes**: Supports all concepts for cleaning tasks.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` statements in your database.
2. **Load Data**: Copy-paste the `INSERT` statements or save as a `.sql` file and import.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to avoid production risks.
4. **Compatibility**:
   - MySQL: Add `AUTO_INCREMENT` to `PRIMARY KEY` if needed (e.g., `id INT PRIMARY KEY AUTO_INCREMENT`).
   - PostgreSQL: Use `SERIAL PRIMARY KEY` for IDs. `DELETE` syntax is standard.
   - SQL Server: Use `TOP` with `DELETE` if limiting rows; standard syntax otherwise.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master DELETE Operations and shine in AI/ML interviews! Happy querying! ✨</p>
</div>