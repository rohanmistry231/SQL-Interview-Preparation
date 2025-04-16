# 🎯 Interview Questions - DELETE to Crush SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master DELETE operations and rule SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** zone for **DELETE**! 💻 This README is your ultimate prep tool, loaded with tricky, real-world questions covering **two core concepts**: `Delete with Conditions` and `Delete All Rows`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With datasets and solutions (hidden in `<details>` tags), you’ll sharpen your data deletion skills, boost your confidence, and make your portfolio shine for recruiters. Let’s clear those tables and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master DELETE**: Perfect your ability to remove data safely and precisely.
- **Power AI/ML Workflows**: Clean datasets, prune logs, and manage model outputs.
- **Shine Under Pressure**: Practice explaining deletion logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Dive In**:
   - Pick a concept section (e.g., `Delete with Conditions`).
   - Read the question and try writing the DELETE query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it against the datasets to verify results.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Delete with Conditions` to nail targeted deletions, then tackle `Delete All Rows` for table-clearing scenarios. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, datasets, and solutions. Get ready to delete like a pro!

### 1. Delete with Conditions
- **Description**: `DELETE` removes rows based on specific conditions, often using `WHERE` clauses or subqueries.
- **Interview Focus**: Tests precision in targeting rows and avoiding accidental data loss.

#### Question 1.1: Remove Low-Confidence Predictions
- **Problem**: Your ML model has unreliable predictions. Write a query to delete rows from `predictions` where `score` is less than 0.8.
- **Trick**: Tests if you use `WHERE` to safely target rows without wiping the table.
- **AI/ML Use Case**: Cleans datasets by removing low-confidence predictions.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELETE FROM predictions
  WHERE score < 0.8;
  ```
  </details>

#### Question 1.2: Clear Flagged Orders
- **Problem**: For fraud analysis, remove flagged transactions. Write a query to delete rows from `orders` where `order_id` is in `fraud_flags` with `flag_reason = 'Invalid address'`.
- **Trick**: Tests subquery integration to ensure precise deletion.
- **AI/ML Use Case**: Prunes invalid transactions for fraud model training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELETE FROM orders
  WHERE order_id IN (
      SELECT order_id
      FROM fraud_flags
      WHERE flag_reason = 'Invalid address'
  );
  ```
  </details>

---

### 2. Delete All Rows
- **Description**: `DELETE` without conditions or `TRUNCATE` removes all rows from a table.
- **Interview Focus**: Tests understanding of full-table deletion and its implications (e.g., no rollback with `TRUNCATE`).

#### Question 2.1: Clear Old Logs
- **Problem**: Your ML pipeline needs a fresh start for logs. Write a query to delete all rows from `model_logs`.
- **Trick**: Tests if you use `DELETE` without conditions safely and understand its rollback capability.
- **AI/ML Use Case**: Resets logs before a new training cycle.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELETE FROM model_logs;
  ```
  </details>

#### Question 2.2: Reset Fraud Flags
- **Problem**: After fraud analysis, clear the fraud flags table. Write a query to delete all rows from `fraud_flags`.
- **Trick**: Ensures you avoid `TRUNCATE` in interviews unless explicitly allowed, focusing on `DELETE` for safety.
- **AI/ML Use Case**: Clears processed flags for the next analysis batch.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELETE FROM fraud_flags;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Safe**: Begin with `Delete with Conditions` to master targeted removals.
- **Watch for Traps**: Interviewers test over-deletion in `Delete with Conditions` and ask about `DELETE` vs. `TRUNCATE` for full-table clears.
- **Explain Clearly**: Practice justifying your `WHERE` clauses or full-table deletion for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the datasets below.
- **Optimize Queries**: Use precise conditions to avoid performance issues with large datasets.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Dataset & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these datasets to test DELETE concepts. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Dataset 1: predictions
- **Used In**: Delete with Conditions
- **Description**: ML model predictions for cleaning low-confidence data.
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
- **Used In**: Delete with Conditions
- **Description**: Transaction data for removing flagged records.
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
- **Used In**: Delete All Rows
- **Description**: Model training logs for resetting data.
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

### Dataset 4: fraud_flags
- **Used In**: Delete with Conditions, Delete All Rows
- **Description**: Fraud flags for clearing specific or all records.
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

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run solutions.
3. **Compatibility**:
   - MySQL/PostgreSQL: Supports all `DELETE` syntax.
   - SQL Server: Identical syntax; ensure date formats match if extended (e.g., `YYYY-MM-DD`).
4. **Expand Data**: For up to 100 rows, repeat patterns or check `Datasets/` for full files (coming soon).

---

<div align="center">
  <p>Crush these DELETE questions to dominate SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>