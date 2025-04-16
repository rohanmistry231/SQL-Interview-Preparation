# 📊 Projects - Mastering SQL Aggregations

## 🌟 Overview

Welcome to the **Projects** section for **SQL Aggregations**! 🚀 These five unique projects are your playground to master seven core concepts—`Count`, `Sum`, `Avg`, `Max`, `Min`, `Group By`, and `Having Clause`. Dive into AI/ML-themed challenges like summarizing model performance or aggregating fraud patterns, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL aggregations practical and fun, helping you:
- **Apply Skills**: Summarize ML datasets for model evaluation or fraud detection.
- **Ace Interviews**: Solve data analysis problems like those in real-world ML pipelines.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Aggregate model scores, feature stats, or transaction trends for insights.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key aggregation techniques, with a capstone combining all seven concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Summary** | Count, Group By | Summarize model logs by type and frequency. |
| **Dataset Stats** | Sum, Avg | Aggregate training data features for analysis. |
| **Prediction Analysis** | Max, Min | Analyze prediction score ranges. |
| **Fraud Aggregates** | Avg, Having Clause | Group fraud stats by customer behavior. |
| **Capstone: Metrics** | All Seven | Build a full ML metrics pipeline with aggregations. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Summary/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify aggregation results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all seven concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Count` and `Group By`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Summary
- **Folder**: `Project1_Model_Summary/`
- **Concepts**: `Count`, `Group By`
- **Description**: Summarize model logs by type and frequency to track training events.
- **Tasks**:
  - Count total logs in `model_logs` grouped by `model_id`.
  - Count logs with specific messages (e.g., 'Training started') per model.
  - Group `model_logs` by date (truncated to day) and count entries.
- **AI/ML Use Case**: Tracks model training frequency for pipeline monitoring.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT model_id, COUNT(*) AS log_count
  FROM model_logs
  GROUP BY model_id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT model_id, COUNT(*) AS start_count
  FROM model_logs
  WHERE log_message LIKE '%started%'
  GROUP BY model_id;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT DATE(log_date) AS log_day, COUNT(*) AS daily_count
  FROM model_logs
  GROUP BY DATE(log_date);
  ```
  </details>

### Project 2: Dataset Stats
- **Folder**: `Project2_Dataset_Stats/`
- **Concepts**: `Sum`, `Avg`
- **Description**: Aggregate training data features to analyze dataset properties.
- **Tasks**:
  - Calculate the sum of `feature1` and `feature2` in `training_data`.
  - Compute the average of `feature1` and `feature2` by `label` in `training_data` (joined with `training_labels`).
  - Sum `feature1` for records with `feature2 > 2.0`.
- **AI/ML Use Case**: Summarizes dataset features for preprocessing insights.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT SUM(feature1) AS sum_feature1, SUM(feature2) AS sum_feature2
  FROM training_data;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT tl.label, AVG(td.feature1) AS avg_feature1, AVG(td.feature2) AS avg_feature2
  FROM training_data td
  LEFT JOIN training_labels tl ON td.id = tl.id
  GROUP BY tl.label;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT SUM(feature1) AS high_feature_sum
  FROM training_data
  WHERE feature2 > 2.0;
  ```
  </details>

### Project 3: Prediction Analysis
- **Folder**: `Project3_Prediction_Analysis/`
- **Concepts**: `Max`, `Min`
- **Description**: Analyze prediction score ranges to evaluate model performance.
- **Tasks**:
  - Find the maximum and minimum `score` in `predictions` per `model_id`.
  - Identify the maximum `score` across all predictions.
  - Find the minimum `score` for predictions after '2025-08-20'.
- **AI/ML Use Case**: Evaluates model prediction consistency.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT model_id, MAX(score) AS max_score, MIN(score) AS min_score
  FROM predictions
  GROUP BY model_id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT MAX(score) AS highest_score
  FROM predictions;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT MIN(score) AS lowest_recent_score
  FROM predictions
  WHERE eval_date > '2025-08-20';
  ```
  </details>

### Project 4: Fraud Aggregates
- **Folder**: `Project4_Fraud_Aggregates/`
- **Concepts**: `Avg`, `Having Clause`
- **Description**: Group fraud stats by customer behavior to identify risky patterns.
- **Tasks**:
  - Calculate the average `amount` in `orders` per `customer_id` with more than 2 orders.
  - Average `amount` for flagged orders (joined with `fraud_flags`) grouped by `flag_reason`.
  - Find customers with average `amount` > 150 using `Having Clause`.
- **AI/ML Use Case**: Aggregates transaction data for fraud detection models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT customer_id, AVG(amount) AS avg_amount
  FROM orders
  GROUP BY customer_id
  HAVING COUNT(*) > 2;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT ff.flag_reason, AVG(o.amount) AS avg_flagged_amount
  FROM orders o
  INNER JOIN fraud_flags ff ON o.order_id = ff.order_id
  GROUP BY ff.flag_reason;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT customer_id, AVG(amount) AS avg_amount
  FROM orders
  GROUP BY customer_id
  HAVING AVG(amount) > 150;
  ```
  </details>

### Project 5: Capstone - Metrics
- **Folder**: `Project5_Capstone_Metrics/`
- **Concepts**: All Seven (`Count`, `Sum`, `Avg`, `Max`, `Min`, `Group By`, `Having Clause`)
- **Description**: Build a full ML metrics pipeline with aggregations for fraud analysis.
- **Tasks**:
  - Count logs in `model_logs` grouped by `model_id`.
  - Sum `feature1` in `training_data` by `label`.
  - Average `score` in `predictions` per `model_id`.
  - Find max and min `amount` in `orders` per `customer_id`.
  - Group `orders` by `customer_id`, calculate average `amount`, and filter for averages > 200 using `Having Clause`.
- **AI/ML Use Case**: Summarizes data for a fraud detection pipeline.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT model_id, COUNT(*) AS log_count
  FROM model_logs
  GROUP BY model_id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT tl.label, SUM(td.feature1) AS sum_feature1
  FROM training_data td
  LEFT JOIN training_labels tl ON td.id = tl.id
  GROUP BY tl.label;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT model_id, AVG(score) AS avg_score
  FROM predictions
  GROUP BY model_id;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  SELECT customer_id, MAX(amount) AS max_amount, MIN(amount) AS min_amount
  FROM orders
  GROUP BY customer_id;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  SELECT customer_id, AVG(amount) AS avg_amount
  FROM orders
  GROUP BY customer_id
  HAVING AVG(amount) > 200;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Count` and `Group By`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to verify aggregation outputs.
- **Combine Skills**: Mix aggregations with joins (from `01 Joins`) for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore complex `Having Clause` filters or nested aggregations for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for aggregations? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses aggregations on these tables, testing all seven concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Model training logs for counting and grouping.
- **Schema**:
  ```sql
  CREATE TABLE model_logs (
      log_id INT PRIMARY KEY,
      model_id INT,
      log_message VARCHAR(255),
      log_date DATETIME
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO model_logs (log_id, model_id, log_message, log_date) VALUES
  (1, 101, 'Training started', '2025-08-15 10:00:00'),
  (2, 101, 'Training completed', '2025-08-15 12:00:00'),
  (3, 102, 'Validation error', '2025-08-16 09:30:00'),
  (4, 102, 'Training completed', '2025-08-16 14:00:00'),
  (5, 103, 'Training started', '2025-08-17 11:00:00'),
  (6, 103, 'Testing started', '2025-08-17 15:00:00'),
  (7, 104, 'Prediction generated', '2025-08-18 08:00:00'),
  (8, 104, 'Model updated', '2025-08-18 16:00:00'),
  (9, 105, 'Error logged', '2025-08-19 10:30:00'),
  (10, 105, 'Retraining initiated', '2025-08-19 13:00:00'),
  (11, 106, 'Training started', '2025-08-20 09:00:00'),
  (12, 106, 'Training completed', '2025-08-20 11:00:00'),
  (13, 107, 'Validation error', '2025-08-21 10:00:00'),
  (14, 107, 'Model deployed', '2025-08-21 14:30:00'),
  (15, 108, 'Training started', '2025-08-22 12:00:00'),
  (16, 108, 'Testing started', '2025-08-22 15:00:00'),
  (17, 109, 'Prediction generated', '2025-08-23 09:00:00'),
  (18, 109, 'Model updated', '2025-08-23 17:00:00'),
  (19, 110, 'Error logged', '2025-08-24 11:00:00'),
  (20, 110, 'Training started', '2025-08-24 14:00:00');
  ```
- **Notes**: Supports `Count` and `Group By` for log summaries.

### Dataset 2: training_data
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: ML training data for summing and averaging features.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO training_data (id, feature1, feature2) VALUES
  (1, 0.5, 1.8),
  (2, 1.2, 2.5),
  (3, 2.3, 3.1),
  (4, 0.8, 1.4),
  (5, 1.9, 2.9),
  (6, 0.3, 1.7),
  (7, 2.1, 3.4),
  (8, 1.0, 2.0),
  (9, 1.6, 2.6),
  (10, 0.7, 1.9),
  (11, 2.4, 3.2),
  (12, 0.9, 1.5),
  (13, 1.8, 2.8),
  (14, 0.4, 1.3),
  (15, 2.0, 3.0),
  (16, 0.8, 1.7),
  (17, 1.7, 2.7),
  (18, 0.6, 1.6),
  (19, 2.2, 3.3),
  (20, 0.5, 1.9);
  ```
- **Notes**: Supports `Sum` and `Avg` for feature stats.

### Dataset 3: training_labels
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Labels for training data, with partial coverage.
- **Schema**:
  ```sql
  CREATE TABLE training_labels (
      id INT PRIMARY KEY,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (15 rows to simulate missing labels):
  ```sql
  INSERT INTO training_labels (id, label) VALUES
  (1, 'positive'),
  (2, 'negative'),
  (3, 'positive'),
  (4, 'negative'),
  (5, 'positive'),
  (6, 'negative'),
  (7, 'positive'),
  (8, 'negative'),
  (9, 'positive'),
  (10, 'negative'),
  (11, 'positive'),
  (12, 'negative'),
  (13, 'positive'),
  (14, 'negative'),
  (15, 'positive');
  ```
- **Notes**: Supports grouping by `label` for aggregations.

### Dataset 4: predictions
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: ML model predictions for max/min analysis.
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
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 102, 0.95, '2025-08-17'),
  (4, 102, 0.78, '2025-08-18'),
  (5, 103, 0.91, '2025-08-19'),
  (6, 103, 0.84, '2025-08-20'),
  (7, 104, 0.96, '2025-08-21'),
  (8, 104, 0.80, '2025-08-22'),
  (9, 105, 0.89, '2025-08-23'),
  (10, 105, 0.93, '2025-08-24'),
  (11, 106, 0.77, '2025-08-25'),
  (12, 106, 0.94, '2025-08-26'),
  (13, 107, 0.85, '2025-08-27'),
  (14, 107, 0.90, '2025-08-28'),
  (15, 108, 0.88, '2025-08-29'),
  (16, 108, 0.97, '2025-08-30'),
  (17, 109, 0.79, '2025-08-31'),
  (18, 109, 0.92, '2025-09-01'),
  (19, 110, 0.86, '2025-09-02'),
  (20, 110, 0.91, '2025-09-03');
  ```
- **Notes**: Supports `Max` and `Min` for score analysis.

### Dataset 5: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for averaging and filtering with `Having Clause`.
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
  (101, 301, 90.0, '2025-08-15'),
  (102, 301, 130.5, '2025-08-16'),
  (103, 302, 20.0, '2025-08-17'),
  (104, 302, 260.0, '2025-08-18'),
  (105, 303, 70.3, '2025-08-19'),
  (106, 303, 410.0, '2025-08-20'),
  (107, 304, 35.0, '2025-08-21'),
  (108, 304, 120.7, '2025-08-22'),
  (109, 305, 80.5, '2025-08-23'),
  (110, 305, 60.0, '2025-08-24'),
  (111, 306, 210.0, '2025-08-25'),
  (112, 306, 25.0, '2025-08-26'),
  (113, 307, 170.0, '2025-08-27'),
  (114, 307, 40.0, '2025-08-28'),
  (115, 308, 100.0, '2025-08-29'),
  (116, 308, 65.5, '2025-08-30'),
  (117, 309, 190.5, '2025-08-31'),
  (118, 309, 50.0, '2025-09-01'),
  (119, 310, 110.0, '2025-09-02'),
  (120, 310, 85.0, '2025-09-03');
  ```
- **Notes**: Supports `Avg` and `Having Clause` for fraud stats.

### Dataset 6: fraud_flags
- **Used In**: Project 4
- **Description**: Fraud flags for aggregating flagged orders.
- **Schema**:
  ```sql
  CREATE TABLE fraud_flags (
      flag_id INT PRIMARY KEY,
      order_id INT,
      flag_reason VARCHAR(100)
  );
  ```
- **Sample Data** (15 rows to simulate partial flags):
  ```sql
  INSERT INTO fraud_flags (flag_id, order_id, flag_reason) VALUES
  (1, 101, 'High amount'),
  (2, 102, 'Suspicious pattern'),
  (3, 103, 'Invalid address'),
  (4, 104, 'High amount'),
  (5, 105, 'Multiple orders'),
  (6, 106, 'High amount'),
  (7, 107, 'Suspicious pattern'),
  (8, 108, 'Invalid address'),
  (9, 109, 'Multiple orders'),
  (10, 110, 'High amount'),
  (11, 111, 'Suspicious pattern'),
  (12, 112, 'Invalid address'),
  (13, 113, 'High amount'),
  (14, 114, 'Multiple orders'),
  (15, 115, 'Suspicious pattern');
  ```
- **Notes**: Supports `Avg` with joins for fraud analysis.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Aggregations**: Use project tasks to perform aggregations and analyze results.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify outputs.
4. **Compatibility**:
   - MySQL: Supports all aggregations (`COUNT`, `SUM`, `AVG`, `MAX`, `MIN`, `GROUP BY`, `HAVING`).
   - PostgreSQL: Full support for all aggregations, including `DATE` functions for grouping.
   - SQL Server: Supports all aggregations. Use `CAST(log_date AS DATE)` for date grouping.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master SQL Aggregations and shine in AI/ML interviews! Happy querying! ✨</p>
</div>