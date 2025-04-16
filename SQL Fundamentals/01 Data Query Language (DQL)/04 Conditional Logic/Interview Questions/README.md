# 🎯 Interview Questions - Conditional Logic to Conquer SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Conditional Logic and dominate SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** arena for **Conditional Logic**! 💻 This README is your secret weapon, packed with tricky, real-world questions covering **three core concepts**: `Case Statements`, `Coalesce`, and `Nullif`. Crafted to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With datasets and solutions (tucked away in `<details>` tags), you’ll sharpen your conditional logic skills, boost your confidence, and make your portfolio stand out for recruiters. Let’s tackle these logic puzzles and ace those interviews!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems straight from FAANG, startups, and ML-focused SQL challenges.
- **Master Conditional Logic**: Perfect your ability to categorize data and handle nulls.
- **Power AI/ML Workflows**: Apply logic to label predictions, clean datasets, and analyze models.
- **Shine Under Pressure**: Practice explaining complex conditions for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Dive In**:
   - Pick a concept section (e.g., `Case Statements`).
   - Read the question and try solving it in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it against the datasets to verify results.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Case Statements` for categorization wins, then hit `Coalesce` or `Nullif` for null-handling challenges. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, datasets, and solutions. Get ready to logic like a pro!

### 1. Case Statements
- **Description**: `CASE` statements apply conditional logic to categorize or transform data.
- **Interview Focus**: Tests complex condition chains and output clarity.

#### Question 1.1: Prediction Buckets
- **Problem**: You’re analyzing ML model performance. Write a query to select `prediction_id`, `score`, and a new column `score_category` from `predictions`, where `score_category` is:
  - 'High' if `score` >= 0.9
  - 'Medium' if `score` >= 0.8 but < 0.9
  - 'Low' if `score` < 0.8
- **Trick**: Tests multi-condition `CASE` logic and precedence.
- **AI/ML Use Case**: Categorizes predictions for model evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score,
         CASE
             WHEN score >= 0.9 THEN 'High'
             WHEN score >= 0.8 THEN 'Medium'
             ELSE 'Low'
         END AS score_category
  FROM predictions;
  ```
  </details>

#### Question 1.2: Order Risk Levels
- **Problem**: For a fraud detection model, label transaction risk. Write a query to select `order_id`, `amount`, and a new column `risk_level` from `orders`, where `risk_level` is:
  - 'Critical' if `amount` > 300
  - 'Moderate' if `amount` > 100
  - 'Safe' otherwise
- **Trick**: Ensures you handle `CASE` without overlapping conditions.
- **AI/ML Use Case**: Labels transactions for fraud model training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount,
         CASE
             WHEN amount > 300 THEN 'Critical'
             WHEN amount > 100 THEN 'Moderate'
             ELSE 'Safe'
         END AS risk_level
  FROM orders;
  ```
  </details>

---

### 2. Coalesce
- **Description**: `COALESCE` returns the first non-null value in a list of expressions.
- **Interview Focus**: Tests null handling and default value logic.

#### Question 2.1: Default Scores
- **Problem**: Your ML pipeline has missing prediction scores. Write a query to select `prediction_id`, `model_id`, and a new column `adjusted_score` from `predictions`, where `adjusted_score` is the `score` if non-null, otherwise 0.5.
- **Trick**: Tests if you use `COALESCE` efficiently for single fallback.
- **AI/ML Use Case**: Fills missing scores for model analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, model_id,
         COALESCE(score, 0.5) AS adjusted_score
  FROM predictions;
  ```
  </details>

#### Question 2.2: Log Message Fallback
- **Problem**: ML logs sometimes lack detail. Write a query to select `log_id`, `model_id`, and a new column `display_message` from `model_logs`, where `display_message` is `log_message` if non-null, otherwise 'No message available'.
- **Trick**: Tests `COALESCE` with string defaults under pressure.
- **AI/ML Use Case**: Ensures readable logs for pipeline debugging.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT log_id, model_id,
         COALESCE(log_message, 'No message available') AS display_message
  FROM model_logs;
  ```
  </details>

---

### 3. Nullif
- **Description**: `NULLIF` returns null if two expressions are equal, otherwise the first expression.
- **Interview Focus**: Tests edge-case nullification and data cleaning.

#### Question 3.1: Zero Score Cleanup
- **Problem**: Your ML dataset has invalid zero scores. Write a query to select `prediction_id`, `model_id`, and a new column `cleaned_score` from `predictions`, where `cleaned_score` is `score` unless it’s 0, in which case it’s null.
- **Trick**: Tests `NULLIF` usage for specific value replacement.
- **AI/ML Use Case**: Cleans datasets by nullifying invalid scores.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, model_id,
         NULLIF(score, 0) AS cleaned_score
  FROM predictions;
  ```
  </details>

#### Question 3.2: Invalid Amount Reset
- **Problem**: For fraud analysis, negative transaction amounts are errors. Write a query to select `order_id`, `customer_id`, and a new column `valid_amount` from `orders`, where `valid_amount` is `amount` unless it’s negative, then null.
- **Trick**: Tests combining `NULLIF` with conditional checks.
- **AI/ML Use Case**: Prepares clean transaction data for modeling.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, customer_id,
         CASE
             WHEN amount < 0 THEN NULL
             ELSE amount
         END AS valid_amount
  FROM orders;
  ```
  *Note*: `NULLIF` alone can’t directly handle `amount < 0`, so `CASE` is used for clarity, as it’s a common interview expectation for range-based nullification.
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Begin with `Case Statements` for quick categorization wins.
- **Watch for Traps**: Interviewers test `CASE` condition order, `COALESCE` efficiency, and `NULLIF` edge cases.
- **Explain Clearly**: Practice breaking down conditional logic for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the datasets below.
- **Optimize Queries**: Keep `CASE` and `COALESCE` lean to impress interviewers.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Dataset & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these datasets to test conditional logic concepts. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Dataset 1: predictions
- **Used In**: Case Statements, Coalesce, Nullif
- **Description**: ML model predictions for scoring and cleanup.
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
  (15, 108, NULL, '2025-08-29'),
  (16, 108, 0.97, '2025-08-30'),
  (17, 109, 0.79, '2025-08-31'),
  (18, 109, 0.0, '2025-09-01'),
  (19, 110, 0.86, '2025-09-02'),
  (20, 110, 0.91, '2025-09-03');
  ```

### Dataset 2: orders
- **Used In**: Case Statements, Nullif
- **Description**: Transaction data for risk labeling and cleanup.
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
  (116, 308, -10.0, '2025-08-30'),
  (117, 309, 190.5, '2025-08-31'),
  (118, 309, 50.0, '2025-09-01'),
  (119, 310, 110.0, '2025-09-02'),
  (120, 310, 85.0, '2025-09-03');
  ```

### Dataset 3: model_logs
- **Used In**: Coalesce
- **Description**: Model training logs for message handling.
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
  (3, 102, NULL, '2025-08-16 09:30:00'),
  (4, 102, 'Training completed', '2025-08-16 14:00:00'),
  (5, 103, 'Training started', '2025-08-17 11:00:00'),
  (6, 103, 'Testing started', '2025-08-17 15:00:00'),
  (7, 104, 'Prediction generated', '2025-08-18 08:00:00'),
  (8, 104, 'Model updated', '2025-08-18 16:00:00'),
  (9, 105, 'Error logged', '2025-08-19 10:30:00'),
  (10, 105, 'Retraining initiated', '2025-08-19 13:00:00'),
  (11, 106, NULL, '2025-08-20 09:00:00'),
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
   - MySQL/PostgreSQL: Supports all syntax (`CASE`, `COALESCE`, `NULLIF`).
   - SQL Server: Identical syntax for these functions; ensure date formats match (e.g., `YYYY-MM-DD`).
4. **Expand Data**: For up to 100 rows, repeat patterns or check `Datasets/` for full files (coming soon).

---

<div align="center">
  <p>Crush these conditional logic questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>