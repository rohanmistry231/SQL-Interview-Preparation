# 📊 Projects - Mastering ROLLBACK Transactions

## 🌟 Overview

Welcome to the **Projects** section for **ROLLBACK Transactions**! 🚀 These five unique projects are your playground to master the four core concepts—`Basic ROLLBACK`, `ROLLBACK After INSERT`, `ROLLBACK After UPDATE`, and `ROLLBACK After DELETE`. Dive into AI/ML-themed challenges like undoing faulty model logs or reverting dataset changes, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL ROLLBACK transactions practical and fun, helping you:
- **Apply Skills**: Recover ML data from errors to maintain pipeline integrity.
- **Ace Interviews**: Solve transaction recovery problems like those in real-world DB scenarios.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Undo faulty changes to model predictions, logs, or datasets.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key ROLLBACK techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Recovery** | Basic ROLLBACK | Undo simple transactions for model training logs. |
| **Dataset Restore** | ROLLBACK After INSERT | Revert new dataset records to maintain data quality. |
| **Prediction Revert** | ROLLBACK After UPDATE | Undo updates to prediction scores for models. |
| **Fraud Undo** | ROLLBACK After DELETE | Restore deleted fraudulent orders for review. |
| **Capstone: Recovery** | All Four | Recover an ML pipeline from multiple faulty changes. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Recovery/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify rollbacks.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Basic ROLLBACK`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Recovery
- **Folder**: `Project1_Model_Recovery/`
- **Concepts**: `Basic ROLLBACK`
- **Description**: Undo simple transactions to recover model training logs from errors.
- **Tasks**:
  - Start a transaction, insert a log entry into `model_logs`, and rollback.
  - Begin a transaction, update a log entry in `model_logs`, and rollback.
  - Perform a transaction with a delete from `model_logs` and rollback.
- **AI/ML Use Case**: Reverts faulty log entries to maintain accurate training records.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION;
  INSERT INTO model_logs (log_id, model_id, log_message, log_date)
  VALUES (1001, 101, 'Faulty training log', '2025-09-15 10:00:00');
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION;
  UPDATE model_logs
  SET log_message = 'Incorrect update'
  WHERE log_id = 1;
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  START TRANSACTION;
  DELETE FROM model_logs
  WHERE log_id = 1;
  ROLLBACK;
  ```
  </details>

### Project 2: Dataset Restore
- **Folder**: `Project2_Dataset_Restore/`
- **Concepts**: `ROLLBACK After INSERT`
- **Description**: Revert new dataset records to maintain data quality for ML training.
- **Tasks**:
  - Insert 5 new rows into `training_data` and rollback.
  - Insert a batch of 3 records into `training_data` with invalid features and rollback.
  - Insert a single faulty record into `training_data` and rollback.
- **AI/ML Use Case**: Undoes erroneous training data to prevent model corruption.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION;
  INSERT INTO training_data (id, feature1, feature2, label) VALUES
  (101, 0.6, 1.9, 'positive'),
  (102, 1.3, 2.6, 'negative'),
  (103, 2.4, 3.2, 'positive'),
  (104, 0.9, 1.5, 'negative'),
  (105, 1.7, 2.8, 'positive');
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION;
  INSERT INTO training_data (id, feature1, feature2, label) VALUES
  (106, -1.0, 0.0, 'invalid'),
  (107, 99.9, 0.0, 'invalid'),
  (108, 0.0, -99.9, 'invalid');
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  START TRANSACTION;
  INSERT INTO training_data (id, feature1, feature2, label)
  VALUES (109, NULL, NULL, 'error');
  ROLLBACK;
  ```
  </details>

### Project 3: Prediction Revert
- **Folder**: `Project3_Prediction_Revert/`
- **Concepts**: `ROLLBACK After UPDATE`
- **Description**: Undo updates to prediction scores to preserve model output integrity.
- **Tasks**:
  - Update scores in `predictions` for `model_id = 101` and rollback.
  - Adjust `eval_date` for predictions before '2025-09-01' and rollback.
  - Update `score` to 0.0 for low-scoring predictions (`score < 0.8`) and rollback.
- **AI/ML Use Case**: Reverts faulty prediction updates to ensure reliable analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION;
  UPDATE predictions
  SET score = 0.0
  WHERE model_id = 101;
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION;
  UPDATE predictions
  SET eval_date = '2025-01-01'
  WHERE eval_date < '2025-09-01';
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  START TRANSACTION;
  UPDATE predictions
  SET score = 0.0
  WHERE score < 0.8;
  ROLLBACK;
  ```
  </details>

### Project 4: Fraud Undo
- **Folder**: `Project4_Fraud_Undo/`
- **Concepts**: `ROLLBACK After DELETE`
- **Description**: Restore deleted fraudulent orders for further review.
- **Tasks**:
  - Delete orders with `amount > 300` from `orders` and rollback.
  - Remove orders before '2025-08-20' from `orders` and rollback.
  - Delete flagged orders (via `fraud_flags`) and rollback.
- **AI/ML Use Case**: Recovers deleted fraud data for analysis or model retraining.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION;
  DELETE FROM orders
  WHERE amount > 300;
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION;
  DELETE FROM orders
  WHERE order_date < '2025-08-20';
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  START TRANSACTION;
  DELETE FROM orders
  WHERE order_id IN (SELECT order_id FROM fraud_flags);
  ROLLBACK;
  ```
  </details>

### Project 5: Capstone - Recovery
- **Folder**: `Project5_Capstone_Recovery/`
- **Concepts**: All Four (`Basic ROLLBACK`, `ROLLBACK After INSERT`, `ROLLBACK After UPDATE`, `ROLLBACK After DELETE`)
- **Description**: Recover an ML pipeline from multiple faulty changes in a fraud detection system.
- **Tasks**:
  - Insert a faulty log entry into `model_logs` and rollback.
  - Insert 3 invalid orders into `orders` and rollback.
  - Update `score` in `predictions` with incorrect values and rollback.
  - Delete fraudulent orders from `orders` and rollback.
  - Perform a basic transaction to update `fraud_stats` incorrectly and rollback.
- **AI/ML Use Case**: Restores a fraud detection pipeline after errors.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  START TRANSACTION;
  INSERT INTO model_logs (log_id, model_id, log_message, log_date)
  VALUES (1002, 102, 'Invalid fraud log', '2025-09-20 09:00:00');
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  START TRANSACTION;
  INSERT INTO orders (order_id, customer_id, amount, order_date) VALUES
  (121, 321, -50.0, '2025-09-20'),
  (122, 322, 9999.9, '2025-09-21'),
  (123, 323, 0.0, '2025-09-22');
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  START TRANSACTION;
  UPDATE predictions
  SET score = -1.0
  WHERE prediction_id IN (SELECT order_id FROM orders WHERE amount > 200);
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  START TRANSACTION;
  DELETE FROM orders
  WHERE order_id IN (SELECT order_id FROM fraud_flags WHERE flag_reason = 'High amount');
  ROLLBACK;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  START TRANSACTION;
  UPDATE fraud_stats
  SET order_count = -1
  WHERE customer_id = 321;
  ROLLBACK;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Basic ROLLBACK`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to verify rolled-back data.
- **Combine Skills**: Mix `INSERT` and `UPDATE` rollbacks for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore transaction error handling or isolation levels for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for ROLLBACK transactions? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses transactions on these tables, testing all four ROLLBACK concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Model training logs for transaction rollbacks.
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
- **Notes**: Supports `Basic ROLLBACK` for log recovery.

### Dataset 2: training_data
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: ML training data for rollback after inserts.
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
- **Notes**: Supports `ROLLBACK After INSERT` for dataset recovery.

### Dataset 3: predictions
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: ML model predictions for rollback after updates.
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
- **Notes**: Supports `ROLLBACK After UPDATE` for prediction recovery.

### Dataset 4: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for rollback after deletions.
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
- **Notes**: Supports `ROLLBACK After DELETE` for order recovery.

### Dataset 5: fraud_flags
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Fraud flags for deletion rollbacks.
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
- **Notes**: Supports `ROLLBACK After DELETE` for fraud-related recovery.

### Dataset 6: fraud_stats
- **Used In**: Project 5 (Capstone)
- **Description**: Fraud statistics for transaction rollbacks.
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
- **Notes**: Supports `Basic ROLLBACK` for stats recovery.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Transactions**: Use project tasks to perform transactions and rollback changes.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify rolled-back data.
4. **Compatibility**:
   - MySQL: Supports `START TRANSACTION` and `ROLLBACK`. Use `BEGIN` as alternative.
   - PostgreSQL: Full support for `START TRANSACTION` and `ROLLBACK`. Use `BEGIN` for transactions.
   - SQL Server: Uses `BEGIN TRANSACTION` and `ROLLBACK TRANSACTION`. Replace `START TRANSACTION` accordingly.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master ROLLBACK Transactions and shine in AI/ML interviews! Happy querying! ✨</p>
</div>