# 🎯 Interview Questions - Aggregations to Nail SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Aggregations and snag that AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** zone for **Aggregations**! 💻 This README is your go-to resource, loaded with tricky, real-world questions covering **seven core concepts**: `Count`, `Sum`, `Avg`, `Max`, `Min`, `Group By`, and `Having Clause`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with a challenging, ML-themed question. With schemas, sample data, and solutions (hidden in `<details>` tags), you’ll sharpen your data-summarizing skills, boost your confidence, and make your portfolio shine for recruiters. Let’s crunch those numbers and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Aggregations**: Perfect your ability to summarize and analyze datasets.
- **Power AI/ML Workflows**: Compute metrics, group model outputs, and filter pipeline data.
- **Shine Under Pressure**: Practice explaining aggregation logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Count`).
   - Read the question and try writing the aggregation query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify results against expected outputs.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Count` or `Avg` for basic metrics, then tackle `Group By` and `Having Clause` for grouping mastery. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has a tricky question with an ML-relevant scenario, schema, and solution. Get ready to aggregate like a pro!

### 1. Count
- **Description**: `COUNT` returns the number of rows or non-NULL values in a column.
- **Interview Focus**: Tests row counting and NULL handling.

#### Question 1.1: Prediction Volume
- **Problem**: Your ML team needs to track prediction activity. Write a query to count the total number of predictions in the `predictions` table.
- **Trick**: Tests if you use `COUNT(*)` correctly for total rows.
- **AI/ML Use Case**: Monitors prediction pipeline throughput.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT COUNT(*) AS prediction_count
  FROM predictions;
  ```
  </details>

---

### 2. Sum
- **Description**: `SUM` calculates the total of numeric values in a column.
- **Interview Focus**: Tests numeric aggregation and NULL exclusion.

#### Question 2.1: Total Prediction Scores
- **Problem**: You’re evaluating model performance. Write a query to sum the `score` values in the `predictions` table.
- **Trick**: Tests if you handle `SUM` on a numeric column, ignoring NULLs.
- **AI/ML Use Case**: Aggregates prediction confidence for model comparison.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT SUM(score) AS total_score
  FROM predictions;
  ```
  </details>

---

### 3. Avg
- **Description**: `AVG` computes the average of numeric values in a column.
- **Interview Focus**: Tests mean calculation and decimal precision.

#### Question 3.1: Average Model Score
- **Problem**: Your team needs to assess model quality. Write a query to calculate the average `score` in the `predictions` table.
- **Trick**: Tests if you use `AVG` correctly, handling NULLs implicitly.
- **AI/ML Use Case**: Evaluates average prediction accuracy.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT AVG(score) AS avg_score
  FROM predictions;
  ```
  </details>

---

### 4. Max
- **Description**: `MAX` returns the highest value in a column.
- **Interview Focus**: Tests peak value identification.

#### Question 4.1: Top Prediction Score
- **Problem**: You want to find the best prediction. Write a query to get the maximum `score` from the `predictions` table.
- **Trick**: Tests if you use `MAX` to find the top value without extra rows.
- **AI/ML Use Case**: Identifies the highest-confidence prediction.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT MAX(score) AS max_score
  FROM predictions;
  ```
  </details>

---

### 5. Min
- **Description**: `MIN` returns the lowest value in a column.
- **Interview Focus**: Tests bottom value identification.

#### Question 5.1: Lowest Event Log ID
- **Problem**: You’re auditing pipeline logs. Write a query to find the minimum `log_id` in the `event_logs` table.
- **Trick**: Tests if you use `MIN` on a numeric column correctly.
- **AI/ML Use Case**: Locates the earliest pipeline event.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT MIN(log_id) AS min_log_id
  FROM event_logs;
  ```
  </details>

---

### 6. Group By
- **Description**: `GROUP BY` organizes rows into groups for aggregation.
- **Interview Focus**: Tests grouping logic and column selection.

#### Question 6.1: Predictions by Model
- **Problem**: Your ML pipeline needs per-model stats. Write a query to group `predictions` by `model_id` and show each `model_id` with its count of predictions.
- **Trick**: Tests if you pair `GROUP BY` with `COUNT` and select only grouped columns.
- **AI/ML Use Case**: Summarizes prediction volume per model.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT model_id, COUNT(*) AS prediction_count
  FROM predictions
  GROUP BY model_id;
  ```
  </details>

---

### 7. Having Clause
- **Description**: `HAVING` filters grouped results based on aggregate conditions.
- **Interview Focus**: Tests post-grouping filtering and syntax.

#### Question 7.1: High-Activity Models
- **Problem**: You want to find active models. Write a query to group `predictions` by `model_id`, join with `models` to get `model_name`, and show only groups with more than 2 predictions, including `model_id`, `model_name`, and prediction count.
- **Trick**: Tests if you combine `GROUP BY`, `HAVING`, and `JOIN` correctly, avoiding non-grouped columns.
- **AI/ML Use Case**: Identifies frequently used models for optimization.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT p.model_id, m.model_name, COUNT(*) AS prediction_count
  FROM predictions p
  INNER JOIN models m ON p.model_id = m.model_id
  GROUP BY p.model_id, m.model_name
  HAVING COUNT(*) > 2;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Simple**: Begin with `Count` or `Avg` to nail basic aggregations.
- **Watch for Traps**: Interviewers test NULL handling in `Sum`/`Avg`, non-grouped columns in `Group By`, and `HAVING` vs. `WHERE` confusion.
- **Explain Clearly**: Practice justifying aggregation choices (e.g., `HAVING` for group filters) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Aggregations**: Use indexes on grouped columns; avoid over-aggregating large datasets.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test aggregation operations. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Count, Sum, Avg, Max, Group By, Having Clause
- **Description**: Stores ML predictions.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE
  );
  ```
- **Sample Data** (8 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 101, 0.90, '2025-08-17'),
  (4, 102, 0.95, '2025-08-18'),
  (5, 102, 0.78, '2025-08-19'),
  (6, 103, 0.91, '2025-08-20'),
  (7, 103, 0.85, '2025-08-21'),
  (8, 999, 0.88, '2025-08-22');
  ```

### Schema 2: models
- **Used In**: Having Clause
- **Description**: Stores ML model metadata.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE
  );
  ```
- **Sample Data** (4 rows):
  ```sql
  INSERT INTO models (model_id, model_name, created_date) VALUES
  (101, 'Model A', '2025-08-01'),
  (102, 'Model B', '2025-08-02'),
  (103, 'Model C', '2025-08-03'),
  (104, 'Model D', '2025-08-04');
  ```

### Schema 3: event_logs
- **Used In**: Min
- **Description**: Logs ML pipeline events.
- **Schema**:
  ```sql
  CREATE TABLE event_logs (
      log_id INT PRIMARY KEY,
      event_type VARCHAR(50),
      status VARCHAR(20) DEFAULT 'Pending'
  );
  ```
- **Sample Data** (5 rows):
  ```sql
  INSERT INTO event_logs (log_id, event_type, status) VALUES
  (1, 'Training Start', 'Completed'),
  (2, 'Validation', 'Failed'),
  (3, 'Prediction Run', 'Completed'),
  (4, 'Model Update', 'Pending'),
  (5, 'Testing', 'Completed');
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run aggregation queries.
3. **Compatibility**:
   - MySQL: Supports all aggregations; `HAVING` works post-`GROUP BY`.
   - PostgreSQL: Fully supports all functions; allows flexible `GROUP BY`.
   - SQL Server: Identical syntax; requires grouped or aggregated columns in `SELECT`.
4. **Verify Results**: Query results (e.g., `SELECT COUNT(*) FROM predictions`) to confirm counts, sums, or filtered groups.
5. **Data Scale**: Sample data is small (~17 rows total) for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Crush these Aggregations questions to dominate SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>