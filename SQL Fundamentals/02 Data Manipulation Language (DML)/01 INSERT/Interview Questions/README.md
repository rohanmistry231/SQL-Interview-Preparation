# 🎯 Interview Questions - INSERT to Nail SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master INSERT operations and crush SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** zone for **INSERT**! 💻 This README is your ultimate prep tool, loaded with tricky, real-world questions covering **three core concepts**: `Single Row Insert`, `Multiple Row Insert`, and `Insert from Select`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With datasets and solutions (hidden in `<details>` tags), you’ll sharpen your data insertion skills, boost your confidence, and make your portfolio shine for recruiters. Let’s populate those tables and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master INSERT**: Perfect your ability to add data efficiently and accurately.
- **Power AI/ML Workflows**: Insert training data, log model outputs, and prep datasets.
- **Shine Under Pressure**: Practice explaining insertion logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Dive In**:
   - Pick a concept section (e.g., `Single Row Insert`).
   - Read the question and try writing the INSERT query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it against the datasets to verify results.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Single Row Insert` for quick wins, then tackle `Insert from Select` for complex data transfer challenges. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, datasets, and solutions. Get ready to insert like a pro!

### 1. Single Row Insert
- **Description**: `INSERT` adds a single row with specified values to a table.
- **Interview Focus**: Tests precision in column mapping and default value handling.

#### Question 1.1: Log New Prediction
- **Problem**: Your ML pipeline generates a new prediction. Write a query to insert a single row into `predictions` with `prediction_id = 21`, `model_id = 111`, `score = 0.88`, and `eval_date = '2025-09-04'`.
- **Trick**: Tests if you specify all required columns accurately.
- **AI/ML Use Case**: Logs a new model prediction for analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, eval_date)
  VALUES (21, 111, 0.88, '2025-09-04');
  ```
  </details>

#### Question 1.2: Add Model Log
- **Problem**: An ML model starts training. Write a query to insert a single row into `model_logs` with `log_id = 21`, `model_id = 111`, `log_message = 'Training initiated'`, and `log_date = '2025-09-04 08:00:00'`.
- **Trick**: Ensures you handle datetime formats correctly.
- **AI/ML Use Case**: Records a training event for pipeline tracking.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  INSERT INTO model_logs (log_id, model_id, log_message, log_date)
  VALUES (21, 111, 'Training initiated', '2025-09-04 08:00:00');
  ```
  </details>

---

### 2. Multiple Row Insert
- **Description**: `INSERT` adds multiple rows in a single query, improving efficiency.
- **Interview Focus**: Tests syntax for bulk inserts and data consistency.

#### Question 2.1: Batch Prediction Insert
- **Problem**: Your ML model outputs three new predictions. Write a query to insert three rows into `predictions` with the following data:
  - `prediction_id = 22`, `model_id = 112`, `score = 0.85`, `eval_date = '2025-09-05'`
  - `prediction_id = 23`, `model_id = 112`, `score = 0.90`, `eval_date = '2025-09-05'`
  - `prediction_id = 24`, `model_id = 112`, `score = 0.87`, `eval_date = '2025-09-05'`
- **Trick**: Tests if you use multi-row syntax correctly without errors.
- **AI/ML Use Case**: Logs a batch of predictions for performance analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, eval_date)
  VALUES
      (22, 112, 0.85, '2025-09-05'),
      (23, 112, 0.90, '2025-09-05'),
      (24, 112, 0.87, '2025-09-05');
  ```
  </details>

#### Question 2.2: Bulk Order Insert
- **Problem**: A new customer places multiple orders. Write a query to insert two rows into `orders` with:
  - `order_id = 121`, `customer_id = 311`, `amount = 95.0`, `order_date = '2025-09-04'`
  - `order_id = 122`, `customer_id = 311`, `amount = 150.0`, `order_date = '2025-09-04'`
- **Trick**: Checks if you maintain column order and data types in bulk inserts.
- **AI/ML Use Case**: Adds transaction data for fraud detection modeling.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  INSERT INTO orders (order_id, customer_id, amount, order_date)
  VALUES
      (121, 311, 95.0, '2025-09-04'),
      (122, 311, 150.0, '2025-09-04');
  ```
  </details>

---

### 3. Insert from Select
- **Description**: `INSERT ... SELECT` copies data from a query into a table.
- **Interview Focus**: Tests combining SELECT logic with insertion and column alignment.

#### Question 3.1: Archive High Scores
- **Problem**: You’re archiving top ML predictions. Write a query to insert rows into `prediction_archive` (same schema as `predictions`) from `predictions` where `score` is greater than 0.95.
- **Trick**: Tests if you align columns between source and target tables.
- **AI/ML Use Case**: Archives high-confidence predictions for historical analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  INSERT INTO prediction_archive (prediction_id, model_id, score, eval_date)
  SELECT prediction_id, model_id, score, eval_date
  FROM predictions
  WHERE score > 0.95;
  ```
  </details>

#### Question 3.2: Log Error Flags
- **Problem**: Your ML pipeline flags errors for review. Write a query to insert rows into `error_logs` (columns: `log_id`, `model_id`, `error_message`, `log_date`) from `model_logs` where `log_message` contains 'error', setting `error_message` as `log_message`.
- **Trick**: Tests if you handle string filtering and column renaming in `INSERT ... SELECT`.
- **AI/ML Use Case**: Extracts error logs for debugging ML models.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  INSERT INTO error_logs (log_id, model_id, error_message, log_date)
  SELECT log_id, model_id, log_message AS error_message, log_date
  FROM model_logs
  WHERE log_message LIKE '%error%';
  ```
  </details>

---

## 💡 Tips for Success

- **Start Simple**: Begin with `Single Row Insert` to nail basic syntax.
- **Watch for Traps**: Interviewers test column mismatches in `Insert from Select` and data type errors in bulk inserts.
- **Explain Clearly**: Practice breaking down insertion logic for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the datasets below.
- **Optimize Queries**: Use `Insert from Select` for efficiency in large datasets.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Dataset & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these datasets to test INSERT concepts. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Dataset 1: predictions
- **Used In**: Single Row Insert, Multiple Row Insert, Insert from Select
- **Description**: ML model predictions for logging new data.
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

### Dataset 2: orders
- **Used In**: Multiple Row Insert
- **Description**: Transaction data for adding new orders.
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

### Dataset 3: model_logs
- **Used In**: Single Row Insert, Insert from Select
- **Description**: Model training logs for event tracking.
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

### Dataset 4: prediction_archive
- **Used In**: Insert from Select
- **Description**: Archive table for high-confidence predictions.
- **Schema**:
  ```sql
  CREATE TABLE prediction_archive (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      eval_date DATE
  );
  ```
- **Sample Data**: Initially empty; populated by Question 3.1.

### Dataset 5: error_logs
- **Used In**: Insert from Select
- **Description**: Log table for error messages.
- **Schema**:
  ```sql
  CREATE TABLE error_logs (
      log_id INT PRIMARY KEY,
      model_id INT,
      error_message VARCHAR(255),
      log_date DATETIME
  );
  ```
- **Sample Data**: Initially empty; populated by Question 3.2.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements above for `predictions`, `orders`, and `model_logs`. Create `prediction_archive` and `error_logs` without initial data.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run solutions.
3. **Compatibility**:
   - MySQL/PostgreSQL: Supports all `INSERT` syntax.
   - SQL Server: Identical syntax; ensure date formats match (e.g., `YYYY-MM-DD`).
4. **Expand Data**: For up to 100 rows, repeat patterns or check `Datasets/` for full files (coming soon).

---

<div align="center">
  <p>Smash these INSERT questions to rule SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>