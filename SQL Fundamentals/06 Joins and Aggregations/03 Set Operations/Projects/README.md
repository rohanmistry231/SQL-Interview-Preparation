# 📊 Projects - Mastering SQL Set Operations

## 🌟 Overview

Welcome to the **Projects** section for **SQL Set Operations**! 🚀 These five unique projects are your playground to master four core concepts—`Union`, `Union All`, `Intersect`, and `Except`. Dive into AI/ML-themed challenges like combining model results, finding common predictions, or filtering fraud data, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL set operations practical and fun, helping you:
- **Apply Skills**: Merge ML datasets or filter outliers for model training.
- **Ace Interviews**: Solve data combination problems like those in real-world ML pipelines.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Combine predictions, unify datasets, or exclude noise for insights.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key set operation techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Combination** | Union, Union All | Combine model logs from different sources. |
| **Dataset Unification** | Union All, Union | Unify training datasets for ML prep. |
| **Prediction Overlap** | Intersect | Find common predictions across models. |
| **Fraud Filter** | Except | Exclude non-fraudulent orders for analysis. |
| **Capstone: Sets** | All Four | Build a full ML pipeline with set operations. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Combination/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify set operation results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Union` and `Union All`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Combination
- **Folder**: `Project1_Model_Combination/`
- **Concepts**: `Union`, `Union All`
- **Description**: Combine model logs from different sources to unify training records.
- **Tasks**:
  - Use `Union` to combine unique `model_id` and `log_message` from `model_logs_a` and `model_logs_b`.
  - Use `Union All` to combine all logs from `model_logs_a` and `model_logs_b`, including duplicates.
  - Combine logs with `Union` and filter for messages containing 'started'.
- **AI/ML Use Case**: Merges logs from multiple training runs for analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT model_id, log_message
  FROM model_logs_a
  UNION
  SELECT model_id, log_message
  FROM model_logs_b;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT model_id, log_message
  FROM model_logs_a
  UNION ALL
  SELECT model_id, log_message
  FROM model_logs_b;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT model_id, log_message
  FROM model_logs_a
  WHERE log_message LIKE '%started%'
  UNION
  SELECT model_id, log_message
  FROM model_logs_b
  WHERE log_message LIKE '%started%';
  ```
  </details>

### Project 2: Dataset Unification
- **Folder**: `Project2_Dataset_Unification/`
- **Concepts**: `Union All`, `Union`
- **Description**: Unify training datasets from multiple sources for ML preparation.
- **Tasks**:
  - Use `Union All` to combine all records from `training_data_a` and `training_data_b`.
  - Use `Union` to combine unique records from `training_data_a` and `training_data_b`.
  - Combine records with `Union All` and filter for `feature1 > 1.0`.
- **AI/ML Use Case**: Prepares a unified dataset for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT id, feature1, feature2
  FROM training_data_a
  UNION ALL
  SELECT id, feature1, feature2
  FROM training_data_b;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT id, feature1, feature2
  FROM training_data_a
  UNION
  SELECT id, feature1, feature2
  FROM training_data_b;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT id, feature1, feature2
  FROM training_data_a
  WHERE feature1 > 1.0
  UNION ALL
  SELECT id, feature1, feature2
  FROM training_data_b
  WHERE feature1 > 1.0;
  ```
  </details>

### Project 3: Prediction Overlap
- **Folder**: `Project3_Prediction_Overlap/`
- **Concepts**: `Intersect`
- **Description**: Find common predictions across models to identify consensus.
- **Tasks**:
  - Use `Intersect` to find `prediction_id` values common to `predictions_a` and `predictions_b`.
  - Find common `score` values between `predictions_a` and `predictions_b` using `Intersect`.
  - Use `Intersect` to find `prediction_id` values for scores > 0.9 in both tables.
- **AI/ML Use Case**: Identifies shared model predictions for ensemble validation.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT prediction_id
  FROM predictions_a
  INTERSECT
  SELECT prediction_id
  FROM predictions_b;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT score
  FROM predictions_a
  INTERSECT
  SELECT score
  FROM predictions_b;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT prediction_id
  FROM predictions_a
  WHERE score > 0.9
  INTERSECT
  SELECT prediction_id
  FROM predictions_b
  WHERE score > 0.9;
  ```
  </details>

### Project 4: Fraud Filter
- **Folder**: `Project4_Fraud_Filter/`
- **Concepts**: `Except`
- **Description**: Exclude non-fraudulent orders to focus on risky transactions.
- **Tasks**:
  - Use `Except` to find `order_id` values in `orders` not in `fraud_flags`.
  - Find `customer_id` values in `orders` not associated with `fraud_flags` using `Except`.
  - Use `Except` to exclude `order_id` values with amounts < 100 from `orders`.
- **AI/ML Use Case**: Filters out clean transactions for fraud model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT order_id
  FROM orders
  EXCEPT
  SELECT order_id
  FROM fraud_flags;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT customer_id
  FROM orders
  EXCEPT
  SELECT customer_id
  FROM orders
  WHERE order_id IN (SELECT order_id FROM fraud_flags);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT order_id
  FROM orders
  EXCEPT
  SELECT order_id
  FROM orders
  WHERE amount < 100;
  ```
  </details>

### Project 5: Capstone - Sets
- **Folder**: `Project5_Capstone_Sets/`
- **Concepts**: All Four (`Union`, `Union All`, `Intersect`, `Except`)
- **Description**: Build a full ML pipeline by combining and filtering datasets for fraud analysis.
- **Tasks**:
  - Use `Union` to combine unique logs from `model_logs_a` and `model_logs_b`.
  - Use `Union All` to combine all records from `training_data_a` and `training_data_b`.
  - Use `Intersect` to find common `prediction_id` values in `predictions_a` and `predictions_b`.
  - Use `Except` to find `order_id` values in `orders` not in `fraud_flags`.
  - Combine `orders` and `fraud_flags` using `Union All` and `Except` to analyze unique risky orders.
- **AI/ML Use Case**: Integrates datasets for a fraud detection pipeline.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT model_id, log_message
  FROM model_logs_a
  UNION
  SELECT model_id, log_message
  FROM model_logs_b;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT id, feature1, feature2
  FROM training_data_a
  UNION ALL
  SELECT id, feature1, feature2
  FROM training_data_b;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT prediction_id
  FROM predictions_a
  INTERSECT
  SELECT prediction_id
  FROM predictions_b;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  SELECT order_id
  FROM orders
  EXCEPT
  SELECT order_id
  FROM fraud_flags;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  SELECT order_id
  FROM orders
  WHERE amount > 200
  UNION ALL
  SELECT order_id
  FROM fraud_flags
  WHERE order_id IN (
      SELECT order_id
      FROM fraud_flags
      EXCEPT
      SELECT order_id
      FROM orders
      WHERE amount < 100
  );
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Union` and `Union All`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to verify set operation outputs.
- **Combine Skills**: Mix set operations with joins and aggregations (from `01 Joins`, `02 Aggregations`) for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore complex `Except` filters or nested set operations for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for set operations? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses set operations on these tables, testing all four concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs_a
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: First set of model logs for combining with `model_logs_b`.
- **Schema**:
  ```sql
  CREATE TABLE model_logs_a (
      log_id INT PRIMARY KEY,
      model_id INT,
      log_message VARCHAR(255),
      log_date DATETIME
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO model_logs_a (log_id, model_id, log_message, log_date) VALUES
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
  (15, 108, 'Training started', '2025-08-22 12:00:00');
  ```
- **Notes**: Supports `Union` and `Union All` for log combination.

### Dataset 2: model_logs_b
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Second set of model logs for combining with `model_logs_a`.
- **Schema**:
  ```sql
  CREATE TABLE model_logs_b (
      log_id INT PRIMARY KEY,
      model_id INT,
      log_message VARCHAR(255),
      log_date DATETIME
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO model_logs_b (log_id, model_id, log_message, log_date) VALUES
  (16, 102, 'Training completed', '2025-08-16 14:00:00'),
  (17, 103, 'Testing started', '2025-08-17 15:00:00'),
  (18, 108, 'Training started', '2025-08-22 12:00:00'),
  (19, 109, 'Prediction generated', '2025-08-23 09:00:00'),
  (20, 109, 'Model updated', '2025-08-23 17:00:00'),
  (21, 110, 'Error logged', '2025-08-24 11:00:00'),
  (22, 110, 'Training started', '2025-08-24 14:00:00'),
  (23, 111, 'Training started', '2025-08-25 09:00:00'),
  (24, 111, 'Training completed', '2025-08-25 11:00:00'),
  (25, 112, 'Validation error', '2025-08-26 10:00:00'),
  (26, 112, 'Model deployed', '2025-08-26 14:30:00'),
  (27, 113, 'Training started', '2025-08-27 12:00:00'),
  (28, 113, 'Testing started', '2025-08-27 15:00:00'),
  (29, 114, 'Prediction generated', '2025-08-28 08:00:00'),
  (30, 114, 'Model updated', '2025-08-28 16:00:00');
  ```
- **Notes**: Includes some duplicates with `model_logs_a` for testing `Union` vs. `Union All`.

### Dataset 3: training_data_a
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: First ML training dataset for unification.
- **Schema**:
  ```sql
  CREATE TABLE training_data_a (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO training_data_a (id, feature1, feature2) VALUES
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
  (15, 2.0, 3.0);
  ```
- **Notes**: Supports `Union All` and `Union` for dataset prep.

### Dataset 4: training_data_b
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Second ML training dataset for unification.
- **Schema**:
  ```sql
  CREATE TABLE training_data_b (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO training_data_b (id, feature1, feature2) VALUES
  (13, 1.8, 2.8),
  (14, 0.4, 1.3),
  (15, 2.0, 3.0),
  (16, 0.8, 1.7),
  (17, 1.7, 2.7),
  (18, 0.6, 1.6),
  (19, 2.2, 3.3),
  (20, 0.5, 1.9),
  (21, 1.3, 2.4),
  (22, 0.9, 1.8),
  (23, 2.5, 3.5),
  (24, 0.7, 1.5),
  (25, 1.9, 2.9),
  (26, 0.4, 1.2),
  (27, 2.1, 3.1);
  ```
- **Notes**: Includes some duplicates with `training_data_a` for testing `Union` vs. `Union All`.

### Dataset 5: predictions_a
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: First set of ML predictions for finding overlaps.
- **Schema**:
  ```sql
  CREATE TABLE predictions_a (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      eval_date DATE
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO predictions_a (prediction_id, model_id, score, eval_date) VALUES
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
  (15, 108, 0.88, '2025-08-29');
  ```
- **Notes**: Supports `Intersect` for prediction overlap.

### Dataset 6: predictions_b
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Second set of ML predictions for finding overlaps.
- **Schema**:
  ```sql
  CREATE TABLE predictions_b (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      eval_date DATE
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO predictions_b (prediction_id, model_id, score, eval_date) VALUES
  (3, 102, 0.95, '2025-08-17'),
  (5, 103, 0.91, '2025-08-19'),
  (7, 104, 0.96, '2025-08-21'),
  (9, 105, 0.89, '2025-08-23'),
  (11, 106, 0.77, '2025-08-25'),
  (16, 108, 0.97, '2025-08-30'),
  (17, 109, 0.79, '2025-08-31'),
  (18, 109, 0.92, '2025-09-01'),
  (19, 110, 0.86, '2025-09-02'),
  (20, 110, 0.91, '2025-09-03'),
  (21, 111, 0.88, '2025-09-04'),
  (22, 111, 0.93, '2025-09-05'),
  (23, 112, 0.76, '2025-09-06'),
  (24, 112, 0.94, '2025-09-07'),
  (25, 113, 0.85, '2025-09-08');
  ```
- **Notes**: Shares some `prediction_id` values with `predictions_a` for `Intersect`.

### Dataset 7: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for filtering with `Except`.
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
- **Notes**: Supports `Except` for fraud filtering.

### Dataset 8: fraud_flags
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Fraud flags for filtering with `Except`.
- **Schema**:
  ```sql
  CREATE TABLE fraud_flags (
      flag_id INT PRIMARY KEY,
      order_id INT,
      flag_reason VARCHAR(100)
  );
  ```
- **Sample Data** (15 rows):
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
- **Notes**: Supports `Except` for identifying non-flagged orders.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Set Operations**: Use project tasks to perform set operations and analyze results.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify outputs.
4. **Compatibility**:
   - MySQL: Supports `UNION` and `UNION ALL`. `INTERSECT` and `EXCEPT` may require subquery workarounds (e.g., `IN` or `NOT IN`).
   - PostgreSQL: Full support for `UNION`, `UNION ALL`, `INTERSECT`, and `EXCEPT`.
   - SQL Server: Full support for `UNION`, `UNION ALL`, `INTERSECT`, and `EXCEPT`.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master SQL Set Operations and shine in AI/ML interviews! Happy querying! ✨</p>
</div>