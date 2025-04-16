# 🎯 Interview Questions - Subqueries to Dominate SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Unlock the power of Subqueries and crush SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** hub for **Subqueries**! 💻 This README is your ultimate prep tool, loaded with tricky, real-world questions covering **four core concepts**: `Single-Row Subqueries`, `Multi-Row Subqueries`, `Correlated Subqueries`, and `Nested Subqueries`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With datasets and solutions (hidden in `<details>` tags), you’ll sharpen your subquery skills, boost your confidence, and make your portfolio shine for recruiters. Let’s dive into the query-within-query world and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Subqueries**: Nail advanced querying for complex data retrieval.
- **Power AI/ML Workflows**: Use subqueries to prep datasets, analyze models, and detect fraud.
- **Shine Under Pressure**: Practice explaining nested logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Dive In**:
   - Pick a concept section (e.g., `Single-Row Subqueries`).
   - Read the question and try solving it in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it against the datasets to verify results.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Single-Row Subqueries` for quick wins, then tackle `Correlated Subqueries` or `Nested Subqueries` for brain-bending challenges. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, datasets, and solutions. Get ready to query like a pro!

### 1. Single-Row Subqueries
- **Description**: Single-row subqueries return one row and column, often used with comparison operators (`=`, `>`, etc.).
- **Interview Focus**: Tests precise subquery placement and scalar result handling.

#### Question 1.1: Max Score Filter
- **Problem**: You’re evaluating ML model performance. Write a query to select `prediction_id`, `score` from `predictions` where the `score` equals the maximum `score` in the table.
- **Trick**: Tests if you use a single-row subquery correctly without overcomplicating.
- **AI/ML Use Case**: Identifies the highest-confidence prediction for validation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE score = (SELECT MAX(score) FROM predictions);
  ```
  </details>

#### Question 1.2: Latest Log
- **Problem**: For ML pipeline monitoring, find the latest log entry. Write a query to select `log_id`, `log_message` from `model_logs` where `log_date` equals the most recent `log_date`.
- **Trick**: Ensures you handle date comparisons in subqueries accurately.
- **AI/ML Use Case**: Retrieves the latest log for pipeline status checks.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT log_id, log_message
  FROM model_logs
  WHERE log_date = (SELECT MAX(log_date) FROM model_logs);
  ```
  </details>

---

### 2. Multi-Row Subqueries
- **Description**: Multi-row subqueries return multiple rows, often used with `IN`, `ANY`, or `ALL`.
- **Interview Focus**: Tests handling of list-based comparisons and subquery scope.

#### Question 2.1: Flagged Orders
- **Problem**: For a fraud detection model, find transactions with fraud flags. Write a query to select `order_id`, `amount` from `orders` where `order_id` is in the list of `order_id` values from `fraud_flags`.
- **Trick**: Tests if you use `IN` correctly for multi-row results.
- **AI/ML Use Case**: Filters transactions for fraud model training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount
  FROM orders
  WHERE order_id IN (SELECT order_id FROM fraud_flags);
  ```
  </details>

#### Question 2.2: High-Scoring Models
- **Problem**: You need models with above-average performance. Write a query to select `prediction_id`, `model_id` from `predictions` where `score` is greater than any `score` less than 0.85 in the table.
- **Trick**: Tests `ANY` usage and understanding of comparison logic.
- **AI/ML Use Case**: Identifies strong models for further training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, model_id
  FROM predictions
  WHERE score > ANY (SELECT score FROM predictions WHERE score < 0.85);
  ```
  </details>

---

### 3. Correlated Subqueries
- **Description**: Correlated subqueries reference the outer query, executing for each outer row.
- **Interview Focus**: Tests row-by-row logic and performance considerations.

#### Question 3.1: Model Performance Check
- **Problem**: You’re auditing ML models. Write a query to select `model_id` from `predictions` where the model’s average `score` (from `predictions`) exceeds 0.9.
- **Trick**: Tests correlated subquery syntax and aggregation in subqueries.
- **AI/ML Use Case**: Flags high-performing models for deployment.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT DISTINCT model_id
  FROM predictions p1
  WHERE (SELECT AVG(score) FROM predictions p2 WHERE p2.model_id = p1.model_id) > 0.9;
  ```
  </details>

#### Question 3.2: Fraudulent Customers
- **Problem**: For fraud analysis, find customers with multiple flagged orders. Write a query to select `customer_id` from `orders` where the count of their `order_id` in `fraud_flags` is greater than 1.
- **Trick**: Tests correlated subquery with counting logic.
- **AI/ML Use Case**: Identifies repeat fraud suspects for modeling.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT DISTINCT customer_id
  FROM orders o
  WHERE (SELECT COUNT(*) FROM fraud_flags f WHERE f.order_id = o.order_id) > 1;
  ```
  </details>

---

### 4. Nested Subqueries
- **Description**: Nested subqueries are subqueries within subqueries, often for layered logic.
- **Interview Focus**: Tests complex query structuring and readability.

#### Question 4.1: Top Fraud Orders
- **Problem**: You’re building a fraud detection pipeline. Write a query to select `order_id`, `amount` from `orders` where `amount` exceeds the average `amount` of orders flagged for 'High amount' in `fraud_flags`.
- **Trick**: Tests nesting subqueries with aggregation and filtering.
- **AI/ML Use Case**: Targets high-value fraud candidates for analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount
  FROM orders
  WHERE amount > (
      SELECT AVG(amount)
      FROM orders
      WHERE order_id IN (
          SELECT order_id
          FROM fraud_flags
          WHERE flag_reason = 'High amount'
      )
  );
  ```
  </details>

#### Question 4.2: Error-Prone Models
- **Problem**: For ML debugging, find models with recent errors. Write a query to select `model_id` from `predictions` where the `model_id` has a log in `model_logs` with 'error' in `log_message` after the average `log_date`.
- **Trick**: Tests deep nesting with date and text comparisons.
- **AI/ML Use Case**: Identifies models needing retraining due to errors.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT DISTINCT model_id
  FROM predictions
  WHERE model_id IN (
      SELECT model_id
      FROM model_logs
      WHERE log_message LIKE '%error%'
      AND log_date > (
          SELECT AVG(log_date)
          FROM model_logs
      )
  );
  ```
  </details>

---

## 💡 Tips for Success

- **Start Simple**: Kick off with `Single-Row Subqueries` to build confidence.
- **Watch for Traps**: Interviewers love testing correlated subquery performance and nested query clarity.
- **Explain Clearly**: Practice breaking down subquery logic for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the datasets below.
- **Optimize Queries**: Avoid overly complex subqueries to impress interviewers.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL chops.

---

## 📂 Dataset & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these datasets to test subquery concepts. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Dataset 1: predictions
- **Used In**: Single-Row Subqueries, Multi-Row Subqueries, Correlated Subqueries, Nested Subqueries
- **Description**: ML model predictions for performance analysis.
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
- **Used In**: Multi-Row Subqueries, Correlated Subqueries, Nested Subqueries
- **Description**: Transaction data for fraud analysis.
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

### Dataset 3: fraud_flags
- **Used In**: Multi-Row Subqueries, Correlated Subqueries, Nested Subqueries
- **Description**: Fraud flags for transaction analysis.
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

### Dataset 4: model_logs
- **Used In**: Single-Row Subqueries, Nested Subqueries
- **Description**: Model training logs for debugging.
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

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run solutions.
3. **Compatibility**:
   - MySQL/PostgreSQL: Supports all subquery syntax.
   - SQL Server: Ensure date formats match (e.g., `YYYY-MM-DD`) and use `TOP` if combining with limiting logic.
4. **Expand Data**: For up to 100 rows, repeat patterns or check `Datasets/` for full files (coming soon).

---

<div align="center">
  <p>Smash these subquery questions to rule SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>