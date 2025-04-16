# 📊 Projects - Mastering SET TRANSACTION Controls

## 🌟 Overview

Welcome to the **Projects** section for **SET TRANSACTION Controls**! 🚀 These five unique projects are your playground to master the four core concepts—`SET TRANSACTION READ ONLY`, `SET TRANSACTION READ WRITE`, `SET TRANSACTION ISOLATION LEVEL READ COMMITTED`, and `SET TRANSACTION ISOLATION LEVEL SERIALIZABLE`. Dive into AI/ML-themed challenges like securing analytics queries or isolating model updates, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL SET TRANSACTION controls practical and fun, helping you:
- **Apply Skills**: Control ML data access and consistency for reliable pipelines.
- **Ace Interviews**: Solve transaction isolation problems like those in real-world DB scenarios.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Ensure data integrity for model training, predictions, or fraud detection.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key SET TRANSACTION techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Analytics Safety** | SET TRANSACTION READ ONLY | Set read-only transactions for safe ML analytics. |
| **Model Updates** | SET TRANSACTION READ WRITE | Enable write transactions for model data updates. |
| **Prediction Consistency** | SET TRANSACTION ISOLATION LEVEL READ COMMITTED | Ensure consistent reads for prediction pipelines. |
| **Fraud Isolation** | SET TRANSACTION ISOLATION LEVEL SERIALIZABLE | Isolate fraud detection updates for accuracy. |
| **Capstone: Control** | All Four | Manage a full ML pipeline with controlled transactions. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Analytics_Safety/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify transaction behavior.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `READ ONLY`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Analytics Safety
- **Folder**: `Project1_Analytics_Safety/`
- **Concepts**: `SET TRANSACTION READ ONLY`
- **Description**: Set read-only transactions to safely query ML analytics data without modifications.
- **Tasks**:
  - Start a read-only transaction and query `model_performance` for average scores.
  - Set a read-only transaction to select `training_data` labels and verify no updates are allowed.
  - Use a read-only transaction to count `predictions` by `model_id`.
- **AI/ML Use Case**: Ensures analysts query data without altering ML datasets.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION READ ONLY;
  SELECT AVG(score) AS avg_score
  FROM model_performance;
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION READ ONLY;
  SELECT label, COUNT(*) AS label_count
  FROM training_data
  GROUP BY label;
  -- Attempting UPDATE will fail
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  START TRANSACTION READ ONLY;
  SELECT model_id, COUNT(*) AS prediction_count
  FROM predictions
  GROUP BY model_id;
  COMMIT;
  ```
  </details>

### Project 2: Model Updates
- **Folder**: `Project2_Model_Updates/`
- **Concepts**: `SET TRANSACTION READ WRITE`
- **Description**: Enable read-write transactions to update model-related data safely.
- **Tasks**:
  - Start a read-write transaction, insert a log into `model_logs`, and commit.
  - Set a read-write transaction, update `model_performance` scores, and commit.
  - Use a read-write transaction to delete old logs from `model_logs` and commit.
- **AI/ML Use Case**: Allows controlled updates to model logs and performance metrics.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION READ WRITE;
  INSERT INTO model_logs (log_id, model_id, log_message, log_date)
  VALUES (1001, 101, 'Model retrained', '2025-09-15 10:00:00');
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION READ WRITE;
  UPDATE model_performance
  SET avg_score = avg_score + 0.01
  WHERE model_id = 101;
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  START TRANSACTION READ WRITE;
  DELETE FROM model_logs
  WHERE log_date < '2025-08-15';
  COMMIT;
  ```
  </details>

### Project 3: Prediction Consistency
- **Folder**: `Project3_Prediction_Consistency/`
- **Concepts**: `SET TRANSACTION ISOLATION LEVEL READ COMMITTED`
- **Description**: Ensure consistent reads for prediction pipelines with read-committed isolation.
- **Tasks**:
  - Set read-committed isolation, query `predictions` for recent scores, and commit.
  - Start a read-committed transaction, update `predictions` scores, and verify changes in another session.
  - Use read-committed isolation to select `fraud_stats` and confirm no dirty reads.
- **AI/ML Use Case**: Guarantees consistent prediction data during concurrent ML tasks.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
  START TRANSACTION;
  SELECT score
  FROM predictions
  WHERE eval_date >= '2025-09-01';
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
  START TRANSACTION;
  UPDATE predictions
  SET score = score + 0.02
  WHERE model_id = 102;
  COMMIT;
  -- In another session:
  SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
  START TRANSACTION;
  SELECT score
  FROM predictions
  WHERE model_id = 102;
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
  START TRANSACTION;
  SELECT total_amount
  FROM fraud_stats
  WHERE order_count > 5;
  COMMIT;
  ```
  </details>

### Project 4: Fraud Isolation
- **Folder**: `Project4_Fraud_Isolation/`
- **Concepts**: `SET TRANSACTION ISOLATION LEVEL SERIALIZABLE`
- **Description**: Isolate fraud detection updates with serializable isolation for accuracy.
- **Tasks**:
  - Set serializable isolation, update `fraud_flags` for high-amount orders, and commit.
  - Start a serializable transaction, insert into `orders`, and verify isolation in another session.
  - Use serializable isolation to delete `fraud_stats` entries and confirm no conflicts.
- **AI/ML Use Case**: Ensures strict isolation for fraud detection data updates.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
  START TRANSACTION;
  UPDATE fraud_flags
  SET flag_reason = 'High amount - Reviewed'
  WHERE order_id IN (SELECT order_id FROM orders WHERE amount > 300);
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
  START TRANSACTION;
  INSERT INTO orders (order_id, customer_id, amount, order_date)
  VALUES (121, 321, 450.0, '2025-09-15');
  COMMIT;
  -- In another session:
  SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
  START TRANSACTION;
  SELECT amount
  FROM orders
  WHERE order_id = 121;
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
  START TRANSACTION;
  DELETE FROM fraud_stats
  WHERE order_count < 2;
  COMMIT;
  ```
  </details>

### Project 5: Capstone - Control
- **Folder**: `Project5_Capstone_Control/`
- **Concepts**: All Four (`READ ONLY`, `READ WRITE`, `READ COMMITTED`, `SERIALIZABLE`)
- **Description**: Manage a full ML pipeline with controlled transactions for fraud detection.
- **Tasks**:
  - Set a read-only transaction to query `training_data` statistics.
  - Use a read-write transaction to update `predictions` scores.
  - Set read-committed isolation to insert into `orders` and verify consistency.
  - Use serializable isolation to update `fraud_flags` and commit.
  - Combine read-write and read-committed to log a model event and query `model_logs`.
- **AI/ML Use Case**: Controls a fraud detection pipeline with precise transaction settings.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION READ ONLY;
  SELECT AVG(feature1) AS avg_feature1
  FROM training_data;
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION READ WRITE;
  UPDATE predictions
  SET score = score + 0.03
  WHERE model_id = 103;
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
  START TRANSACTION;
  INSERT INTO orders (order_id, customer_id, amount, order_date)
  VALUES (122, 322, 200.0, '2025-09-16');
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
  START TRANSACTION;
  UPDATE fraud_flags
  SET flag_reason = 'Isolated update'
  WHERE flag_id = 1;
  COMMIT;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  START TRANSACTION READ WRITE;
  INSERT INTO model_logs (log_id, model_id, log_message, log_date)
  VALUES (1002, 103, 'Fraud pipeline updated', '2025-09-16 11:00:00');
  COMMIT;
  SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
  START TRANSACTION;
  SELECT log_message
  FROM model_logs
  WHERE log_id = 1002;
  COMMIT;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `READ ONLY`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database with multiple sessions to verify isolation.
- **Combine Skills**: Mix `READ WRITE` and `SERIALIZABLE` for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore transaction deadlocks or advanced isolation levels for deeper challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for SET TRANSACTION controls? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses transactions on these tables, testing all four SET TRANSACTION concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Model training logs for read-write transactions.
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
  (4, 102, 'Model deployed', '2025-08-16 14:00:00'),
  (5, 103, 'Hyperparameter tuned', '2025-08-17 11:00:00'),
  (6, 103, 'Testing started', '2025-08-17 15:00:00'),
  (7, 104, 'Prediction generated', '2025-08-18 08:00:00'),
  (8, 104, 'Model updated', '2025-08-18 16:00:00'),
  (9, 105, 'Error logged', '2025-08-19 10:30:00'),
  (10, 105, 'Retraining initiated', '2025-08-19 13:00:00'),
  (11, 106, 'Training started', '2025-08-20 09:00:00'),
  (12, 106, 'Training completed', '2025-08-20 11:00:00'),
  (13, 107, 'Validation error', '2025-08-21 10:00:00'),
  (14, 107, 'Model deployed', '2025-08-21 14:30:00'),
  (15, 108, 'Hyperparameter tuned', '2025-08-22 12:00:00'),
  (16, 108, 'Testing started', '2025-08-22 15:00:00'),
  (17, 109, 'Prediction generated', '2025-08-23 09:00:00'),
  (18, 109, 'Model updated', '2025-08-23 17:00:00'),
  (19, 110, 'Error logged', '2025-08-24 11:00:00'),
  (20, 110, 'Retraining initiated', '2025-08-24 14:00:00');
  ```
- **Notes**: Supports `READ WRITE` for log updates.

### Dataset 2: model_performance
- **Used In**: Project 1, Project 2, Project 5 (Capstone)
- **Description**: Model performance metrics for read-only and read-write transactions.
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
- **Notes**: Supports `READ ONLY` and `READ WRITE` for performance analysis.

### Dataset 3: training_data
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML training data for read-only queries.
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
  (1, 0.5, 1.8, 'positive'),
  (2, 1.2, 2.5, 'negative'),
  (3, 2.3, 3.1, 'positive'),
  (4, 0.8, 1.4, 'negative'),
  (5, 1.9, 2.9, 'positive'),
  (6, 0.3, 1.7, 'negative'),
  (7, 2.1, 3.4, 'positive'),
  (8, 1.0, 2.0, 'negative'),
  (9, 1.6, 2.6, 'positive'),
  (10, 0.7, 1.9, 'negative'),
  (11, 2.4, 3.2, 'positive'),
  (12, 0.9, 1.5, 'negative'),
  (13, 1.8, 2.8, 'positive'),
  (14, 0.4, 1.3, 'negative'),
  (15, 2.0, 3.0, 'positive'),
  (16, 0.8, 1.7, 'negative'),
  (17, 1.7, 2.7, 'positive'),
  (18, 0.6, 1.6, 'negative'),
  (19, 2.2, 3.3, 'positive'),
  (20, 0.5, 1.9, 'negative');
  ```
- **Notes**: Supports `READ ONLY` for safe dataset queries.

### Dataset 4: predictions
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: ML model predictions for read-committed isolation.
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
- **Notes**: Supports `READ COMMITTED` for consistent predictions.

### Dataset 5: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for serializable isolation.
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
- **Notes**: Supports `SERIALIZABLE` for order updates.

### Dataset 6: fraud_flags
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Fraud flags for serializable isolation.
- **Schema**:
  ```sql
  CREATE TABLE fraud_flags (
      flag_id INT PRIMARY KEY,
      order_id INT,
      flag_reason VARCHAR(100)
  );
  ```
- **Sample Data** (20 rows):
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
  (15, 115, 'Suspicious pattern'),
  (16, 116, 'Invalid address'),
  (17, 117, 'High amount'),
  (18, 118, 'Multiple orders'),
  (19, 119, 'Suspicious pattern'),
  (20, 120, 'Invalid address');
  ```
- **Notes**: Supports `SERIALIZABLE` for fraud updates.

### Dataset 7: fraud_stats
- **Used In**: Project 3, Project 4, Project 5 (Capstone)
- **Description**: Fraud statistics for read-committed and serializable transactions.
- **Schema**:
  ```sql
  CREATE TABLE fraud_stats (
      customer_id INT PRIMARY KEY,
      order_count INT,
      total_amount FLOAT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO fraud_stats (customer_id, order_count, total_amount) VALUES
  (301, 5, 350.0),
  (302, 3, 280.5),
  (303, 6, 450.0),
  (304, 2, 200.0),
  (305, 4, 320.3),
  (306, 1, 120.0),
  (307, 7, 550.0),
  (308, 3, 260.5),
  (309, 5, 380.0),
  (310, 2, 180.0),
  (311, 4, 400.0),
  (312, 3, 270.0),
  (313, 6, 520.0),
  (314, 1, 100.0),
  (315, 5, 420.3),
  (316, 2, 150.0),
  (317, 4, 390.0),
  (318, 3, 290.0),
  (319, 5, 370.0),
  (320, 2, 230.0);
  ```
- **Notes**: Supports `READ COMMITTED` and `SERIALIZABLE` for stats queries.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Transactions**: Use project tasks to set transaction properties and perform operations.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) with multiple sessions to verify isolation levels.
4. **Compatibility**:
   - MySQL: Supports `READ ONLY`, `READ WRITE` (8.0+), and `READ COMMITTED`, `SERIALIZABLE`. Use `SET TRANSACTION` before `START TRANSACTION`.
   - PostgreSQL: Full support for all modes. `READ WRITE` is default; explicitly set `READ ONLY`. Use `SET TRANSACTION` after `BEGIN`.
   - SQL Server: Supports `READ ONLY` (via `SET TRANSACTION READONLY`), `READ COMMITTED`, `SERIALIZABLE`. Use `SET TRANSACTION ISOLATION LEVEL` before `BEGIN TRANSACTION`.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master SET TRANSACTION Controls and shine in AI/ML interviews! Happy querying! ✨</p>
</div>