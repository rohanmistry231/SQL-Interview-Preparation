# 📊 Projects - Mastering Subqueries

## 🌟 Overview

Welcome to the **Projects** section for **Subqueries**! 🚀 These five unique projects are your playground to master the four core concepts—`Single-Row Subqueries`, `Multi-Row Subqueries`, `Correlated Subqueries`, and `Nested Subqueries`. Dive into AI/ML-themed challenges like selecting top models or segmenting data, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL subqueries practical and fun, helping you:
- **Apply Skills**: Use subqueries to filter and analyze ML data.
- **Ace Interviews**: Solve problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Query data for model selection, validation, or segmentation.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key subquery techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Selection** | Single-Row Subqueries, Nested Subqueries | Select models from a `predictions` table that beat a benchmark score using subqueries. |
| **User Filtering** | Multi-Row Subqueries, Nested Subqueries | Filter users from a `users` table who match multiple criteria via subqueries. |
| **Order Validation** | Correlated Subqueries | Validate orders in a `customer_orders` table against customer data using correlated subqueries. |
| **Data Segmentation** | Multi-Row Subqueries, Single-Row Subqueries | Segment `training_data` based on feature thresholds derived from subqueries. |
| **Capstone: Analysis** | All Four | Analyze `sales_data` for an ML model, combining all subquery types to extract insights. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Selection/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Single-Row Subqueries`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Selection
- **Folder**: `Project1_Model_Selection/`
- **Concepts**: `Single-Row Subqueries`, `Nested Subqueries`
- **Description**: Select ML models from a `predictions` table that outperform a benchmark score, using subqueries to derive thresholds.
- **Tasks**:
  - Select models with a `score` greater than the average `score`.
  - Find models where `score` exceeds the maximum `score` from a specific `eval_date`.
  - Use a nested subquery to select models above the average `score` of models from ‘2025-03-01’.
- **AI/ML Use Case**: Identifies high-performing models for deployment.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT model_id, score
  FROM predictions
  WHERE score > (SELECT AVG(score) FROM predictions);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT model_id, score
  FROM predictions
  WHERE score > (SELECT MAX(score) FROM predictions WHERE eval_date = '2025-03-01');
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT model_id, score
  FROM predictions
  WHERE score > (SELECT AVG(score) FROM predictions WHERE eval_date = '2025-03-01');
  ```
  </details>

### Project 2: User Filtering
- **Folder**: `Project2_User_Filtering/`
- **Concepts**: `Multi-Row Subqueries`, `Nested Subqueries`
- **Description**: Filter users from a `users` table who meet multiple criteria (e.g., high activity, specific regions) using multi-row and nested subqueries.
- **Tasks**:
  - Select users with `activity` greater than any user in the ‘South’ region.
  - Find users whose `user_id` is in a subquery of active users (`activity > 5`).
  - Use a nested subquery to select users with `activity` above the average of ‘North’ users.
- **AI/ML Use Case**: Segments users for personalized ML recommendations.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT user_id, email, activity
  FROM users
  WHERE activity > ANY (SELECT activity FROM users WHERE region = 'South');
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT user_id, email
  FROM users
  WHERE user_id IN (SELECT user_id FROM users WHERE activity > 5);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT user_id, email, activity
  FROM users
  WHERE activity > (SELECT AVG(activity) FROM users WHERE region = 'North');
  ```
  </details>

### Project 3: Order Validation
- **Folder**: `Project3_Order_Validation/`
- **Concepts**: `Correlated Subqueries`
- **Description**: Validate orders in a `customer_orders` table by checking against customer data using correlated subqueries to ensure consistency.
- **Tasks**:
  - Select orders where the `customer_id` exists in the `customers` table.
  - Find orders with `amount` greater than the average `amount` for that `customer_id`.
  - Select orders where the `order_date` is the latest for each `customer_id`.
- **AI/ML Use Case**: Ensures valid orders for fraud detection models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT order_id, customer_id, amount
  FROM customer_orders co
  WHERE EXISTS (
      SELECT 1
      FROM customers c
      WHERE c.customer_id = co.customer_id
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT order_id, customer_id, amount
  FROM customer_orders co
  WHERE amount > (
      SELECT AVG(amount)
      FROM customer_orders co2
      WHERE co2.customer_id = co.customer_id
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT order_id, customer_id, order_date
  FROM customer_orders co
  WHERE order_date = (
      SELECT MAX(order_date)
      FROM customer_orders co2
      WHERE co2.customer_id = co.customer_id
  );
  ```
  </details>

### Project 4: Data Segmentation
- **Folder**: `Project4_Data_Segmentation/`
- **Concepts**: `Multi-Row Subqueries`, `Single-Row Subqueries`
- **Description**: Segment `training_data` based on feature thresholds derived from subqueries, preparing data for ML model training.
- **Tasks**:
  - Select rows where `feature1` is greater than the average `feature1`.
  - Find rows with `label` in a subquery of common labels (`label` appearing multiple times).
  - Select rows where `feature2` exceeds any `feature2` from ‘positive’ labels.
- **AI/ML Use Case**: Prepares segmented data for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT id, feature1, label
  FROM training_data
  WHERE feature1 > (SELECT AVG(feature1) FROM training_data);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT id, feature1, label
  FROM training_data
  WHERE label IN (
      SELECT label
      FROM training_data
      GROUP BY label
      HAVING COUNT(*) > 1
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT id, feature2, label
  FROM training_data
  WHERE feature2 > ANY (SELECT feature2 FROM training_data WHERE label = 'positive');
  ```
  </details>

### Project 5: Capstone - Analysis
- **Folder**: `Project5_Capstone_Analysis/`
- **Concepts**: All Four (`Single-Row Subqueries`, `Multi-Row Subqueries`, `Correlated Subqueries`, `Nested Subqueries`)
- **Description**: Analyze `sales_data` for an ML model, combining all subquery types to extract insights like top sales or valid records.
- **Tasks**:
  - Select sales with `amount` above the average `amount` (single-row).
  - Find sales where `customer_id` is in a subquery of active customers (`activity > 5`).
  - Use a correlated subquery to select sales with the latest `sale_date` per `customer_id`.
  - Use a nested subquery to select sales above the average `amount` of ‘East’ region sales.
  - Combine subqueries to filter sales with `amount` above any `West` region sale.
- **AI/ML Use Case**: Prepares insights for sales prediction models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT sale_id, customer_id, amount
  FROM sales_data
  WHERE amount > (SELECT AVG(amount) FROM sales_data);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT sale_id, customer_id
  FROM sales_data
  WHERE customer_id IN (SELECT customer_id FROM customers WHERE activity > 5);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT sale_id, customer_id, sale_date
  FROM sales_data sd
  WHERE sale_date = (
      SELECT MAX(sale_date)
      FROM sales_data sd2
      WHERE sd2.customer_id = sd.customer_id
  );
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  SELECT sale_id, customer_id, amount
  FROM sales_data
  WHERE amount > (SELECT AVG(amount) FROM sales_data WHERE region = 'East');
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  SELECT sale_id, customer_id, amount
  FROM sales_data
  WHERE amount > ANY (SELECT amount FROM sales_data WHERE region = 'West');
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Single-Row Subqueries`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix correlated and nested subqueries for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for subqueries? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all four subquery concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: predictions
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML model predictions with scores for benchmarking and selection.
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
  (1, 0.95, '2025-03-01'),
  (2, 0.88, '2025-03-01'),
  (3, 0.92, '2025-03-02'),
  (4, 0.76, '2025-03-02'),
  (5, 0.91, '2025-03-03'),
  (6, 0.85, '2025-03-03'),
  (7, 0.97, '2025-03-04'),
  (8, 0.80, '2025-03-04'),
  (9, 0.89, '2025-03-05'),
  (10, 0.93, '2025-03-05'),
  (11, 0.78, '2025-03-06'),
  (12, 0.96, '2025-03-06'),
  (13, 0.84, '2025-03-07'),
  (14, 0.90, '2025-03-07'),
  (15, 0.87, '2025-03-08'),
  (16, 0.94, '2025-03-08'),
  (17, 0.79, '2025-03-09'),
  (18, 0.98, '2025-03-09'),
  (19, 0.86, '2025-03-10'),
  (20, 0.91, '2025-03-10');
  ```
- **Notes**: Supports `Single-Row Subqueries` (average `score`), `Nested Subqueries` (date-specific metrics).

### Dataset 2: users
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: User data for filtering and segmentation, with activity and regions.
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
  (1, 'alice@gmail.com', 'North', 8),
  (2, 'bob@yahoo.com', 'South', 3),
  (3, 'carol@outlook.com', 'East', 6),
  (4, 'dave@gmail.com', 'West', 2),
  (5, 'emma@yahoo.com', 'North', 7),
  (6, 'frank@company.com', 'South', 4),
  (7, 'grace@gmail.com', 'East', 9),
  (8, 'henry@outlook.com', 'West', 1),
  (9, 'ivy@yahoo.com', 'North', 5),
  (10, 'jack@gmail.com', 'South', 3),
  (11, 'kate@company.com', 'East', 6),
  (12, 'liam@outlook.com', 'West', 2),
  (13, 'mia@gmail.com', 'North', 8),
  (14, 'noah@yahoo.com', 'South', 4),
  (15, 'olivia@company.com', 'East', 7),
  (16, 'peter@gmail.com', 'West', 3),
  (17, 'quinn@outlook.com', 'North', 5),
  (18, 'rose@yahoo.com', 'South', 2),
  (19, 'sam@company.com', 'East', 6),
  (20, 'tina@gmail.com', 'West', 4),
  (21, 'uma@outlook.com', 'North', 7),
  (22, 'victor@yahoo.com', 'South', 3),
  (23, 'wendy@company.com', 'East', 8),
  (24, 'xavier@gmail.com', 'West', 2),
  (25, 'yara@outlook.com', 'North', 6);
  ```
- **Notes**: Enables `Multi-Row Subqueries` (`IN`, `ANY`), `Nested Subqueries` (region-based filters).

### Dataset 3: customers
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Customer data for validating orders, with activity for cross-checking.
- **Schema**:
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      name VARCHAR(100),
      activity INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO customers (customer_id, name, activity) VALUES
  (101, 'Alice Smith', 5),
  (102, 'Bob Johnson', 3),
  (103, 'Carol White', 7),
  (104, 'Dave Brown', 2),
  (105, 'Emma Davis', 6),
  (106, 'Frank Wilson', 4),
  (107, 'Grace Lee', 8),
  (108, 'Henry Clark', 1),
  (109, 'Ivy Taylor', 5),
  (110, 'Jack Moore', 3),
  (111, 'Kate Adams', 6),
  (112, 'Liam Harris', 2),
  (113, 'Mia Lewis', 7),
  (114, 'Noah Walker', 4),
  (115, 'Olivia Young', 5),
  (116, 'Peter King', 3),
  (117, 'Quinn Scott', 6),
  (118, 'Rose Hall', 2),
  (119, 'Sam Green', 8),
  (120, 'Tina Baker', 4);
  ```
- **Notes**: Supports `Correlated Subqueries` (matching `customer_id`).

### Dataset 4: customer_orders
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Customer orders for validation, with amounts and dates.
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
  (1, 101, 50.0, '2025-04-01'),
  (2, 102, 150.5, '2025-04-02'),
  (3, 103, 25.0, '2025-04-03'),
  (4, 104, 200.0, '2025-04-04'),
  (5, 105, 75.3, '2025-04-05'),
  (6, 106, 300.0, '2025-04-06'),
  (7, 107, 40.0, '2025-04-07'),
  (8, 108, 120.7, '2025-04-08'),
  (9, 109, 90.5, '2025-04-09'),
  (10, 110, 60.0, '2025-04-10'),
  (11, 111, 250.0, '2025-04-11'),
  (12, 112, 30.0, '2025-04-12'),
  (13, 113, 180.0, '2025-04-13'),
  (14, 114, 45.0, '2025-04-14'),
  (15, 115, 100.0, '2025-04-15'),
  (16, 116, 70.5, '2025-04-16'),
  (17, 117, 200.5, '2025-04-17'),
  (18, 118, 55.0, '2025-04-18'),
  (19, 119, 130.0, '2025-04-19'),
  (20, 120, 85.0, '2025-04-20'),
  (21, 121, 110.0, '2025-04-21'),
  (22, 101, 65.0, '2025-04-22'),
  (23, 102, 175.0, '2025-04-23'),
  (24, 103, 35.0, '2025-04-24'),
  (25, 104, 95.0, '2025-04-25');
  ```
- **Notes**: Supports `Correlated Subqueries` (customer validation), `Nested Subqueries` (date/amount filters).

### Dataset 5: training_data
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: ML training data for segmentation, with features and labels.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label) VALUES
  (1, 1.5, 2.3, 'positive'),
  (2, 0.8, 1.9, 'negative'),
  (3, 2.1, 3.0, 'positive'),
  (4, 0.4, 1.2, 'negative'),
  (5, 1.7, 2.8, 'positive'),
  (6, 0.9, 1.5, 'negative'),
  (7, 2.3, 3.2, 'positive'),
  (8, 0.6, 1.0, 'negative'),
  (9, 1.9, 2.7, 'positive'),
  (10, 0.5, 1.4, 'negative'),
  (11, 2.0, 3.1, 'positive'),
  (12, 0.7, 1.8, 'negative'),
  (13, 1.6, 2.9, 'positive'),
  (14, 0.3, 1.1, 'negative'),
  (15, 2.2, 3.3, 'positive'),
  (16, 0.8, 1.7, 'negative'),
  (17, 1.8, 2.6, 'positive'),
  (18, 0.4, 1.3, 'negative'),
  (19, 2.4, 3.4, 'positive'),
  (20, 0.9, 1.6, 'negative'),
  (21, 1.5, 2.5, 'positive'),
  (22, 0.6, 1.9, 'negative'),
  (23, 2.1, 3.0, 'positive'),
  (24, 0.7, 1.2, 'negative'),
  (25, 1.9, 2.8, 'positive');
  ```
- **Notes**: Supports `Single-Row Subqueries` (average features), `Multi-Row Subqueries` (label filters).

### Dataset 6: sales_data
- **Used In**: Project 5 (Capstone)
- **Description**: Sales data for comprehensive analysis, with regions and amounts.
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
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date, region) VALUES
  (1, 201, 15.5, '2025-05-01', 'East'),
  (2, 202, 250.0, '2025-05-02', 'West'),
  (3, 203, 8.0, '2025-05-03', 'East'),
  (4, 204, 100.0, '2025-05-04', 'South'),
  (5, 205, 30.7, '2025-05-05', 'West'),
  (6, 206, 12.0, '2025-05-06', 'East'),
  (7, 207, 400.5, '2025-05-07', 'South'),
  (8, 208, 25.0, '2025-05-08', 'West'),
  (9, 209, 200.0, '2025-05-09', 'East'),
  (10, 210, 50.0, '2025-05-10', 'South'),
  (11, 211, 75.3, '2025-05-11', 'West'),
  (12, 212, 300.0, '2025-05-12', 'East'),
  (13, 213, 40.0, '2025-05-13', 'South'),
  (14, 214, 120.7, '2025-05-14', 'West'),
  (15, 215, 60.0, '2025-05-15', 'East'),
  (16, 216, 90.5, '2025-05-16', 'South'),
  (17, 217, 150.0, '2025-05-17', 'West'),
  (18, 218, 20.0, '2025-05-18', 'East'),
  (19, 219, 80.0, '2025-05-19', 'South'),
  (20, 220, 110.0, '2025-05-20', 'West');
  ```
- **Notes**: Supports all subquery types for region-based and amount-based analysis.

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
  <p>Dive into these projects to master Subqueries and shine in AI/ML interviews! Happy querying! ✨</p>
</div>