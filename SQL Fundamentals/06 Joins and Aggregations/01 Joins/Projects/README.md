# 📊 Projects - Mastering SQL Joins

## 🌟 Overview

Welcome to the **Projects** section for **SQL Joins**! 🚀 These five unique projects are your playground to master six core concepts—`Inner Join`, `Left Join`, `Right Join`, `Full Outer Join`, `Self-Join`, and `Cross-Join`. Dive into AI/ML-themed challenges like merging model data, analyzing fraud, or generating feature pairs, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL joins practical and fun, helping you:
- **Apply Skills**: Combine ML datasets for training, evaluation, or feature engineering.
- **Ace Interviews**: Solve data merging problems like those in real-world ML pipelines.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Merge model outputs, generate combinations, or trace fraud patterns.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key join techniques, with a capstone combining multiple concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Analysis** | Inner Join, Self-Join | Analyze model logs and hierarchies. |
| **Dataset Prep** | Left Join, Right Join | Merge training data and predictions. |
| **Prediction Insights** | Right Join, Cross-Join | Combine predictions and generate pairs. |
| **Fraud Patterns** | Full Outer Join, Inner Join | Link orders with fraud flags. |
| **Capstone: Pipeline** | All Six | Build a full ML pipeline with joins. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Analysis/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify join results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all six concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Inner Join` and `Self-Join`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Analysis
- **Folder**: `Project1_Model_Analysis/`
- **Concepts**: `Inner Join`, `Self-Join`
- **Description**: Analyze model logs and their hierarchies using joins.
- **Tasks**:
  - Use an inner join to combine `model_logs` and `model_performance` by `model_id`.
  - Perform a self-join on `model_logs` to pair related logs (e.g., training and completion).
  - Join `model_logs` with `model_performance` to find high-scoring models (`avg_score > 0.9`) with logs.
- **AI/ML Use Case**: Links training logs to metrics and traces model event sequences.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT ml.log_id, ml.log_message, mp.avg_score
  FROM model_logs ml
  INNER JOIN model_performance mp ON ml.model_id = mp.model_id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT ml1.log_id AS log_id1, ml1.log_message AS msg1, ml2.log_id AS log_id2, ml2.log_message AS msg2
  FROM model_logs ml1
  INNER JOIN model_logs ml2 ON ml1.model_id = ml2.model_id AND ml1.log_id < ml2.log_id
  WHERE ml1.log_message LIKE '%started%' AND ml2.log_message LIKE '%completed%';
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT ml.log_id, ml.log_message, mp.avg_score
  FROM model_logs ml
  INNER JOIN model_performance mp ON ml.model_id = mp.model_id
  WHERE mp.avg_score > 0.9;
  ```
  </details>

### Project 2: Dataset Prep
- **Folder**: `Project2_Dataset_Prep/`
- **Concepts**: `Left Join`, `Right Join`
- **Description**: Merge training data and predictions for ML dataset preparation.
- **Tasks**:
  - Use a left join to combine `training_data` with `training_labels` by `id`.
  - Perform a right join to merge `predictions` with `model_performance` by `model_id`.
  - Join `training_data` and `training_labels` to find unlabeled records using a left join.
- **AI/ML Use Case**: Prepares datasets with all features or includes all model metrics.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT td.id, td.feature1, td.feature2, tl.label
  FROM training_data td
  LEFT JOIN training_labels tl ON td.id = tl.id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT p.prediction_id, p.score, mp.avg_score
  FROM predictions p
  RIGHT JOIN model_performance mp ON p.model_id = mp.model_id;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT td.id, td.feature1, td.feature2
  FROM training_data td
  LEFT JOIN training_labels tl ON td.id = tl.id
  WHERE tl.label IS NULL;
  ```
  </details>

### Project 3: Prediction Insights
- **Folder**: `Project3_Prediction_Insights/`
- **Concepts**: `Right Join`, `Cross-Join`
- **Description**: Combine predictions and generate feature pairs for analysis.
- **Tasks**:
  - Use a right join to include all `model_performance` rows with `predictions`.
  - Perform a cross-join on `features` to generate all possible feature pairs.
  - Join `predictions` and `model_performance` to list models without predictions using a right join.
- **AI/ML Use Case**: Analyzes predictions and creates feature combinations for modeling.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT p.prediction_id, p.score, mp.avg_score
  FROM predictions p
  RIGHT JOIN model_performance mp ON p.model_id = mp.model_id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT f1.feature_name AS feature1, f2.feature_name AS feature2
  FROM features f1
  CROSS JOIN features f2
  WHERE f1.feature_name < f2.feature_name;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT mp.model_id, mp.avg_score
  FROM predictions p
  RIGHT JOIN model_performance mp ON p.model_id = mp.model_id
  WHERE p.prediction_id IS NULL;
  ```
  </details>

### Project 4: Fraud Patterns
- **Folder**: `Project4_Fraud_Patterns/`
- **Concepts**: `Full Outer Join`, `Inner Join`
- **Description**: Link orders with fraud flags to uncover patterns.
- **Tasks**:
  - Use a full outer join to combine `orders` and `fraud_flags` by `order_id`.
  - Perform an inner join to find flagged orders with high amounts (>200).
  - Join `orders` and `fraud_flags` to count unmatched records using a full outer join.
- **AI/ML Use Case**: Combines transaction and fraud data for detection models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT o.order_id, o.amount, ff.flag_reason
  FROM orders o
  FULL OUTER JOIN fraud_flags ff ON o.order_id = ff.order_id;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT o.order_id, o.amount, ff.flag_reason
  FROM orders o
  INNER JOIN fraud_flags ff ON o.order_id = ff.order_id
  WHERE o.amount > 200;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT 
      SUM(CASE WHEN o.order_id IS NULL THEN 1 ELSE 0 END) AS flags_without_orders,
      SUM(CASE WHEN ff.order_id IS NULL THEN 1 ELSE 0 END) AS orders_without_flags
  FROM orders o
  FULL OUTER JOIN fraud_flags ff ON o.order_id = ff.order_id;
  ```
  </details>

### Project 5: Capstone - Pipeline
- **Folder**: `Project5_Capstone_Pipeline/`
- **Concepts**: All Six (`Inner Join`, `Left Join`, `Right Join`, `Full Outer Join`, `Self-Join`, `Cross-Join`)
- **Description**: Build a full ML pipeline by joining datasets for fraud analysis and feature engineering.
- **Tasks**:
  - Use an inner join to combine `model_logs` and `model_performance` for active models.
  - Perform a left join to merge `training_data` with `training_labels` for dataset prep.
  - Use a right join to combine `predictions` with `model_performance` for all models.
  - Perform a full outer join to analyze `orders` and `fraud_flags`.
  - Use a self-join on `model_logs` and cross-join on `features` for sequence and feature pair analysis.
- **AI/ML Use Case**: Integrates datasets for a fraud detection pipeline with feature engineering.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT ml.log_id, ml.log_message, mp.avg_score
  FROM model_logs ml
  INNER JOIN model_performance mp ON ml.model_id = mp.model_id
  WHERE ml.log_date >= '2025-08-20';
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT td.id, td.feature1, td.feature2, tl.label
  FROM training_data td
  LEFT JOIN training_labels tl ON td.id = tl.id;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT p.prediction_id, p.score, mp.avg_score
  FROM predictions p
  RIGHT JOIN model_performance mp ON p.model_id = mp.model_id;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  SELECT o.order_id, o.amount, ff.flag_reason
  FROM orders o
  FULL OUTER JOIN fraud_flags ff ON o.order_id = ff.order_id;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  SELECT ml1.log_id AS log_id1, ml1.log_message AS msg1, f1.feature_name AS feature1, f2.feature_name AS feature2
  FROM model_logs ml1
  INNER JOIN model_logs ml2 ON ml1.model_id = ml2.model_id AND ml1.log_id < ml2.log_id
  CROSS JOIN features f1
  CROSS JOIN features f2
  WHERE ml1.log_message LIKE '%started%' AND f1.feature_name < f2.feature_name;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Inner Join` and `Self-Join`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to verify join outputs.
- **Combine Skills**: Mix joins with filters for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore multi-table joins or join optimization for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for joins? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses joins on these tables, testing all six join types. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Model training logs for inner joins and self-joins.
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
- **Notes**: Supports `Inner Join` and `Self-Join` for log analysis.

### Dataset 2: model_performance
- **Used In**: Project 1, Project 3, Project 5 (Capstone)
- **Description**: Model performance metrics for joins.
- **Schema**:
  ```sql
  CREATE TABLE model_performance (
      model_id INT PRIMARY KEY,
      avg_score FLOAT,
      prediction_count INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO model_performance (model_id, avg_score, prediction_count) VALUES
  (101, 0.90, 12),
  (102, 0.88, 10),
  (103, 0.92, 9),
  (104, 0.94, 14),
  (105, 0.89, 11),
  (106, 0.91, 8),
  (107, 0.87, 13),
  (108, 0.93, 7),
  (109, 0.86, 15),
  (110, 0.95, 10),
  (111, 0.88, 9),
  (112, 0.90, 11),
  (113, 0.92, 8),
  (114, 0.89, 12),
  (115, 0.91, 7),
  (116, 0.93, 10),
  (117, 0.87, 14),
  (118, 0.94, 6),
  (119, 0.90, 13),
  (120, 0.92, 9);
  ```
- **Notes**: Supports `Inner Join` and `Right Join`.

### Dataset 3: training_data
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: ML training data for left joins.
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
- **Notes**: Supports `Left Join` for dataset prep.

### Dataset 4: training_labels
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
- **Notes**: Supports `Left Join` for incomplete data.

### Dataset 5: predictions
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: ML model predictions for right joins.
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
- **Notes**: Supports `Right Join` and `Cross-Join`.

### Dataset 6: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for full outer joins.
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
  (102, 302, 130.5, '2025-08-16'),
  (103, 303, 20.0, '2025-08-17'),
  (104, 304, 260.0, '2025-08-18'),
  (105, 305, 70.3, '2025-08-19'),
  (106, 306, 410.0, '2025-08-20'),
  (107, 307, 35.0, '2025-08-21'),
  (108, 308, 120.7, '2025-08-22'),
  (109, 309, 80.5, '2025-08-23'),
  (110, 310, 60.0, '2025-08-24'),
  (111, 311, 210.0, '2025-08-25'),
  (112, 312, 25.0, '2025-08-26'),
  (113, 313, 170.0, '2025-08-27'),
  (114, 314, 40.0, '2025-08-28'),
  (115, 315, 100.0, '2025-08-29'),
  (116, 316, 65.5, '2025-08-30'),
  (117, 317, 190.5, '2025-08-31'),
  (118, 318, 50.0, '2025-09-01'),
  (119, 319, 110.0, '2025-09-02'),
  (120, 320, 85.0, '2025-09-03');
  ```
- **Notes**: Supports `Full Outer Join`.

### Dataset 7: fraud_flags
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Fraud flags for full outer joins.
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
- **Notes**: Supports `Full Outer Join`.

### Dataset 8: features
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Features for cross-joins to generate pairs.
- **Schema**:
  ```sql
  CREATE TABLE features (
      feature_id INT PRIMARY KEY,
      feature_name VARCHAR(50)
  );
  ```
- **Sample Data** (10 rows):
  ```sql
  INSERT INTO features (feature_id, feature_name) VALUES
  (1, 'age'),
  (2, 'income'),
  (3, 'transaction_count'),
  (4, 'login_frequency'),
  (5, 'session_duration'),
  (6, 'purchase_amount'),
  (7, 'device_type'),
  (8, 'location'),
  (9, 'time_of_day'),
  (10, 'browser');
  ```
- **Notes**: Supports `Cross-Join` for feature engineering.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Joins**: Use project tasks to perform joins and analyze results.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify join outputs.
4. **Compatibility**:
   - MySQL: Supports `INNER`, `LEFT`, `RIGHT`, `CROSS`. Use `FULL OUTER JOIN` for `FULL OUTER JOIN` (MySQL 8.0+ may require workarounds like `UNION`).
   - PostgreSQL: Full support for all joins, including `FULL OUTER JOIN` and `CROSS JOIN`.
   - SQL Server: Supports all joins. Use `FULL OUTER JOIN` and `CROSS JOIN` as needed.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master SQL Joins and shine in AI/ML interviews! Happy querying! ✨</p>
</div>