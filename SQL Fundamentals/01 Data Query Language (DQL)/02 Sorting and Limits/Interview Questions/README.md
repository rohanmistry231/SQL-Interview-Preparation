# 🎯 Interview Questions - Sorting and Limits to Ace SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Power up your SQL interview game with Sorting and Limits—key DQL skills for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** zone for **Sorting and Limits**! 💻 This README is your go-to resource for mastering **four core concepts**: `Order By`, `Limit`, `Offset`, and `Top`. Packed with tricky, real-world interview questions, it’s designed to prep you for coding tests and technical rounds at top companies. Each section below dives into one concept with 1-2 challenging, ML-themed questions that mimic what you’ll face in interviews. With datasets and solutions (tucked away in `<details>` tags), you’ll hone your skills, boost your confidence, and make your portfolio pop for recruiters. Let’s sort, limit, and conquer those interviews!

---

## 🎯 Why These Questions?

These questions are your ticket to:
- **Nail Real Interviews**: Tackle problems straight out of FAANG, startups, and ML-focused SQL tests.
- **Master Sorting & Limits**: Perfect your ability to rank data and control query outputs.
- **Power AI/ML Workflows**: Sort predictions, paginate datasets, and optimize ML pipelines.
- **Shine Under Pressure**: Practice explaining your logic clearly for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Dive In**:
   - Pick a concept section (e.g., `Order By`).
   - Read the question and try solving it in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it against the datasets to verify results.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to ace interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Order By` to nail sorting basics, then hit `Offset` or `Top` for pagination challenges. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, datasets, and solutions. Get ready to flex your SQL brain!

### 1. Order By
- **Description**: `ORDER BY` sorts query results in ascending (`ASC`) or descending (`DESC`) order.
- **Interview Focus**: Expect questions on multi-column sorting, handling ties, and optimization.

#### Question 1.1: Rank Predictions
- **Problem**: Your ML team needs to evaluate model performance. Write a query to select `prediction_id`, `score`, `model_id` from `predictions`, sorted by `score` in descending order, then by `model_id` in ascending order.
- **Trick**: Tests multi-column sorting and precedence.
- **AI/ML Use Case**: Ranks predictions to identify top-performing models.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score, model_id
  FROM predictions
  ORDER BY score DESC, model_id ASC;
  ```
  </details>

#### Question 1.2: Order Transactions
- **Problem**: For fraud analysis, sort transactions by value and recency. Write a query to select `order_id`, `amount`, `order_date` from `orders`, sorted by `amount` descending, then `order_date` ascending.
- **Trick**: Ensures you handle mixed sort directions correctly.
- **AI/ML Use Case**: Prioritizes high-value, recent transactions for fraud detection.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount, order_date
  FROM orders
  ORDER BY amount DESC, order_date ASC;
  ```
  </details>

---

### 2. Limit
- **Description**: `LIMIT` restricts the number of rows returned by a query.
- **Interview Focus**: Tests precision in output control and combining with sorting.

#### Question 2.1: Top Predictions
- **Problem**: You’re validating an ML model’s best outputs. Write a query to select `prediction_id`, `score` from `predictions`, sorted by `score` descending, and return only the top 5 rows.
- **Trick**: Tests if you pair `LIMIT` with `ORDER BY` correctly.
- **AI/ML Use Case**: Identifies highest-confidence predictions for review.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score
  FROM predictions
  ORDER BY score DESC
  LIMIT 5;
  ```
  </details>

#### Question 2.2: Limited Fraud Flags
- **Problem**: For a fraud model, fetch a small sample of flagged orders. Write a query to select `order_id`, `flag_reason` from `fraud_flags`, sorted by `flag_id` ascending, limiting to 3 rows.
- **Trick**: Checks if you avoid fetching excess data.
- **AI/ML Use Case**: Samples fraud signals for quick analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, flag_reason
  FROM fraud_flags
  ORDER BY flag_id ASC
  LIMIT 3;
  ```
  </details>

---

### 3. Offset
- **Description**: `OFFSET` skips a specified number of rows before returning results, often used with `LIMIT`.
- **Interview Focus**: Tests pagination logic and edge cases (e.g., skipping too many rows).

#### Question 3.1: Paginated Predictions
- **Problem**: Your ML dashboard displays predictions in pages of 5. Write a query to select `prediction_id`, `score` from `predictions`, sorted by `score` descending, skipping the first 5 rows and returning the next 5.
- **Trick**: Tests combining `OFFSET` with `LIMIT` and sorting.
- **AI/ML Use Case**: Supports paginated views for model evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score
  FROM predictions
  ORDER BY score DESC
  LIMIT 5 OFFSET 5;
  ```
  </details>

#### Question 3.2: Skipped Orders
- **Problem**: For fraud analysis, skip low-value transactions. Write a query to select `order_id`, `amount` from `orders`, sorted by `amount` ascending, skipping the first 10 rows and returning the next 5.
- **Trick**: Ensures you handle `OFFSET` without breaking pagination.
- **AI/ML Use Case**: Focuses on mid-range transactions for fraud modeling.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount
  FROM orders
  ORDER BY amount ASC
  LIMIT 5 OFFSET 10;
  ```
  </details>

---

### 4. Top
- **Description**: `TOP` (SQL Server-specific) retrieves a specified number of rows, often with `WITH TIES` for handling ties.
- **Interview Focus**: Tests database-specific syntax and tie-breaking logic.

#### Question 4.1: Top Models
- **Problem**: You’re analyzing top ML models (in SQL Server). Write a query to select the top 3 `prediction_id`, `score` from `predictions`, sorted by `score` descending, including ties for the 3rd score.
- **Trick**: Tests `TOP WITH TIES` usage for equal scores.
- **AI/ML Use Case**: Identifies top-performing predictions, accounting for ties.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT TOP 3 WITH TIES prediction_id, score
  FROM predictions
  ORDER BY score DESC;
  ```
  </details>

#### Question 4.2: Top Transactions
- **Problem**: For fraud detection (in SQL Server), fetch top transactions. Write a query to select the top 4 `order_id`, `amount` from `orders`, sorted by `amount` descending, without ties.
- **Trick**: Tests standard `TOP` without `WITH TIES` and precise row count.
- **AI/ML Use Case**: Highlights high-value transactions for fraud analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT TOP 4 order_id, amount
  FROM orders
  ORDER BY amount DESC;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Begin with `Order By` and `Limit` for quick wins.
- **Watch for Traps**: Interviewers test `OFFSET` edge cases (e.g., skipping past data) and `TOP WITH TIES` nuances.
- **Explain Clearly**: Practice verbalizing sort logic and pagination for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the datasets below.
- **Optimize Queries**: Ensure sorting is efficient to impress interviewers.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Dataset & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these datasets to test sorting and limiting concepts. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Dataset 1: predictions
- **Used In**: Order By, Limit, Offset, Top
- **Description**: ML model predictions for ranking and pagination.
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
- **Used In**: Order By, Offset, Top
- **Description**: Transaction data for sorting and limiting.
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
- **Used In**: Limit
- **Description**: Fraud flags for sampling.
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
   - MySQL/PostgreSQL: Use `LIMIT` and `OFFSET` as shown.
   - SQL Server: Replace `LIMIT n OFFSET m` with `TOP n` or use `OFFSET m ROWS FETCH NEXT n ROWS ONLY` for pagination; use `TOP` for Question 4.
4. **Expand Data**: For up to 100 rows, repeat patterns or check `Datasets/` for full files (coming soon).

---

<div align="center">
  <p>Crush these sorting and limits questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>