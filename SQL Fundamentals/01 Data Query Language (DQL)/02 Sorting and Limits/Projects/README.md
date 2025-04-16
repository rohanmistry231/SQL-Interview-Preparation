# 📊 Projects - Mastering Sorting and Limits

## 🌟 Overview

Welcome to the **Projects** section for **Sorting and Limits**! 🚀 These five unique projects are your chance to master the four core concepts—`ORDER BY`, `LIMIT`, `OFFSET`, and `TOP`. Dive into AI/ML-themed challenges like ranking model predictions or paginating datasets, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL fun and practical, helping you:
- **Apply Skills**: Sort and limit data for real-world ML tasks.
- **Ace Interviews**: Solve problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Organize data for model analysis or batch processing.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key sorting and limiting operations, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Ranking** | ORDER BY, LIMIT | Rank ML model predictions by score and select the top few for evaluation. |
| **Data Pagination** | LIMIT, OFFSET | Paginate a `training_data` table for batch processing in an ML pipeline. |
| **Top Users** | TOP, ORDER BY | Identify top active users from a `users` table for a recommendation system. |
| **Sales Trends** | ORDER BY, LIMIT | Analyze recent sales trends by sorting and limiting a `sales_data` table. |
| **Capstone: Batch Processing** | All Four | Process batches of `customer_orders` with sorting and limits for fraud analysis. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Ranking/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to combine all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to master `ORDER BY`, use solutions sparingly, and hit the capstone to flex your full SQL skills for interviewers!

---

## 📚 Project Details

### Project 1: Model Ranking
- **Folder**: `Project1_Model_Ranking/`
- **Concepts**: `ORDER BY`, `LIMIT`
- **Description**: You’re evaluating ML model predictions. Sort predictions by score and select the top performers for further analysis.
- **Tasks**:
  - Sort `predictions` by `score` in descending order.
  - Select the top 5 predictions using `LIMIT`.
  - Sort by `score` ascending and limit to top 3.
- **AI/ML Use Case**: Identifies high-performing models for deployment.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT * FROM predictions ORDER BY score DESC;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT * FROM predictions ORDER BY score DESC LIMIT 5;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT * FROM predictions ORDER BY score ASC LIMIT 3;
  ```
  </details>

### Project 2: Data Pagination
- **Folder**: `Project2_Data_Pagination/`
- **Concepts**: `LIMIT`, `OFFSET`
- **Description**: Paginate a `training_data` table to process data in batches for an ML pipeline, simulating chunked data loading.
- **Tasks**:
  - Select the first 10 rows of `training_data`.
  - Select the next 10 rows using `OFFSET`.
  - Select rows 21-25 with `LIMIT` and `OFFSET`.
- **AI/ML Use Case**: Prepares data batches for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT * FROM training_data LIMIT 10;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT * FROM training_data LIMIT 10 OFFSET 10;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT * FROM training_data LIMIT 5 OFFSET 20;
  ```
  </details>

### Project 3: Top Users
- **Folder**: `Project3_Top_Users/`
- **Concepts**: `TOP`, `ORDER BY`
- **Description**: Identify top active users from a `users` table for a recommendation system, sorting by activity count.
- **Tasks**:
  - Select top 5 users by `activity` descending.
  - Select top 3 users by `activity` ascending.
  - Sort by `user_id` and select top 10.
- **AI/ML Use Case**: Targets high-value users for personalized ML models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT TOP 5 * FROM users ORDER BY activity DESC;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT TOP 3 * FROM users ORDER BY activity ASC;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT TOP 10 * FROM users ORDER BY user_id;
  ```
  </details>

### Project 4: Sales Trends
- **Folder**: `Project4_Sales_Trends/`
- **Concepts**: `ORDER BY`, `LIMIT`
- **Description**: Analyze recent sales trends by sorting a `sales_data` table by date and limiting to recent records.
- **Tasks**:
  - Sort `sales_data` by `sale_date` descending.
  - Select the 5 most recent sales.
  - Sort by `amount` descending and limit to top 3.
- **AI/ML Use Case**: Informs sales prediction models with recent data.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT * FROM sales_data ORDER BY sale_date DESC;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT * FROM sales_data ORDER BY sale_date DESC LIMIT 5;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT * FROM sales_data ORDER BY amount DESC LIMIT 3;
  ```
  </details>

### Project 5: Capstone - Batch Processing
- **Folder**: `Project5_Capstone_Batch_Processing/`
- **Concepts**: All Four (`ORDER BY`, `LIMIT`, `OFFSET`, `TOP`)
- **Description**: Process batches of `customer_orders` for fraud analysis, sorting by amount and using limits to handle chunks.
- **Tasks**:
  - Sort orders by `amount` descending.
  - Select top 5 orders by `amount`.
  - Select the first 10 orders using `LIMIT`.
  - Select orders 11-20 with `OFFSET`.
  - Combine sorting and limits to select top 3 orders after skipping 5.
- **AI/ML Use Case**: Prepares order batches for fraud detection models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT * FROM customer_orders ORDER BY amount DESC;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT TOP 5 * FROM customer_orders ORDER BY amount DESC;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT * FROM customer_orders LIMIT 10;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  SELECT * FROM customer_orders LIMIT 10 OFFSET 10;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  SELECT TOP 3 * FROM customer_orders ORDER BY amount DESC OFFSET 5 ROWS;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `ORDER BY`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix `LIMIT` and `OFFSET` for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for sorting and limits? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

See our [CONTRIBUTING.md](../../../../CONTRIBUTING.md) for guidelines!

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all four concepts (`ORDER BY`, `LIMIT`, `OFFSET`, `TOP`). Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: predictions
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML model predictions with scores, ideal for ranking and limiting.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      model_id INT PRIMARY KEY,
      score FLOAT,
      eval_date DATE
  );
  ```
- **Sample Data** (25 rows):
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
  (20, 0.91, '2025-03-10'),
  (21, 0.83, '2025-03-11'),
  (22, 0.95, '2025-03-11'),
  (23, 0.77, '2025-03-12'),
  (24, 0.92, '2025-03-12'),
  (25, 0.88, '2025-03-13');
  ```
- **Notes**: Supports `ORDER BY` (`score`, `eval_date`), `LIMIT` (top scores).

### Dataset 2: training_data
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: ML training data for batch processing, with varied features.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (30 rows):
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
  (25, 1.9, 2.8, 'positive'),
  (26, 0.5, 1.5, 'negative'),
  (27, 2.3, 3.2, 'positive'),
  (28, 0.8, 1.0, 'negative'),
  (29, 1.7, 2.7, 'positive'),
  (30, 0.4, 1.4, 'negative');
  ```
- **Notes**: Enables `LIMIT`, `OFFSET` for batching, `ORDER BY` for sorting features.

### Dataset 3: users
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: User data for a recommendation system, with activity counts for ranking.
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
  (20, 'tina@gmail.com', 'West', 4);
  ```
- **Notes**: Supports `TOP`, `ORDER BY` for ranking by `activity` or `user_id`.

### Dataset 4: sales_data
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Sales data for trend analysis, with dates and amounts for sorting.
- **Schema**:
  ```sql
  CREATE TABLE sales_data (
      sale_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      sale_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date) VALUES
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
  (20, 120, 85.0, '2025-04-20');
  ```
- **Notes**: Enables `ORDER BY` (`sale_date`, `amount`), `LIMIT` for recent sales.

### Dataset 5: customer_orders
- **Used In**: Project 5 (Capstone)
- **Description**: Customer orders for fraud analysis, with amounts for batch processing.
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
  (1, 201, 50.0, '2025-05-01'),
  (2, 202, 150.5, '2025-05-02'),
  (3, 203, 25.0, '2025-05-03'),
  (4, 204, 200.0, '2025-05-04'),
  (5, 205, 75.3, '2025-05-05'),
  (6, 206, 300.0, '2025-05-06'),
  (7, 207, 40.0, '2025-05-07'),
  (8, 208, 120.7, '2025-05-08'),
  (9, 209, 90.5, '2025-05-09'),
  (10, 210, 60.0, '2025-05-10'),
  (11, 211, 250.0, '2025-05-11'),
  (12, 212, 30.0, '2025-05-12'),
  (13, 213, 180.0, '2025-05-13'),
  (14, 214, 45.0, '2025-05-14'),
  (15, 215, 100.0, '2025-05-15'),
  (16, 216, 70.5, '2025-05-16'),
  (17, 217, 200.5, '2025-05-17'),
  (18, 218, 55.0, '2025-05-18'),
  (19, 219, 130.0, '2025-05-19'),
  (20, 220, 85.0, '2025-05-20'),
  (21, 221, 110.0, '2025-05-21'),
  (22, 222, 65.0, '2025-05-22'),
  (23, 223, 175.0, '2025-05-23'),
  (24, 224, 35.0, '2025-05-24'),
  (25, 225, 95.0, '2025-05-25');
  ```
- **Notes**: Supports all four concepts for batch processing and ranking.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` statements in your database.
2. **Load Data**: Copy-paste the `INSERT` statements or save as a `.sql` file and import.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to avoid production risks.
4. **Compatibility**:
   - MySQL: Add `AUTO_INCREMENT` to `PRIMARY KEY` if needed (e.g., `id INT PRIMARY KEY AUTO_INCREMENT`).
   - PostgreSQL: Use `SERIAL PRIMARY KEY` for auto-incrementing IDs if preferred.
   - SQL Server: Use `TOP` for tasks; `LIMIT`/`OFFSET` may need `FETCH`/`OFFSET ROWS`.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

Dive into these projects to master Sorting and Limits and shine in AI/ML interviews! Happy querying! ✨