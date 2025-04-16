# 🎯 Interview Questions - Joins to Crush SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Joins and land that AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** hub for **Joins**! 💻 This README is your ultimate prep tool, packed with tricky, real-world questions covering **six core concepts**: `Inner Join`, `Left Join`, `Right Join`, `Full Outer Join`, `Self-Join`, and `Cross-Join`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with a challenging, ML-themed question. With schemas, sample data, and solutions (hidden in `<details>` tags), you’ll sharpen your data-combining skills, boost your confidence, and make your portfolio shine for recruiters. Let’s merge those tables and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Joins**: Perfect your ability to combine datasets for analysis.
- **Power AI/ML Workflows**: Merge model outputs, analyze relationships, and prep data for training.
- **Shine Under Pressure**: Practice explaining join logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Inner Join`).
   - Read the question and try writing the JOIN query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify results against expected outputs.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Inner Join` for core merging skills, then tackle `Self-Join` or `Cross-Join` for trickier scenarios. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has a tricky question with an ML-relevant scenario, schema, and solution. Get ready to join like a pro!

### 1. Inner Join
- **Description**: `INNER JOIN` returns only matching rows from both tables.
- **Interview Focus**: Tests precise data matching and join condition accuracy.

#### Question 1.1: Model Prediction Matches
- **Problem**: Your ML team needs to analyze predictions with model details. Write a query to join `predictions` and `models` to show `prediction_id`, `model_name`, and `score` for matching `model_id` values.
- **Trick**: Tests if you define the join condition correctly to avoid missing matches.
- **AI/ML Use Case**: Combines model metadata with predictions for reporting.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT p.prediction_id, m.model_name, p.score
  FROM predictions p
  INNER JOIN models m ON p.model_id = m.model_id;
  ```
  </details>

---

### 2. Left Join
- **Description**: `LEFT JOIN` returns all rows from the left table, with matching rows from the right (NULL if no match).
- **Interview Focus**: Tests handling of unmatched data from the primary table.

#### Question 2.1: Models with Optional Predictions
- **Problem**: You want to list all models, including those without predictions. Write a query to join `models` (left) with `predictions` to show `model_id`, `model_name`, and `prediction_id` (NULL if no predictions).
- **Trick**: Tests if you preserve all left table rows, handling NULLs correctly.
- **AI/ML Use Case**: Identifies models yet to produce predictions.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT m.model_id, m.model_name, p.prediction_id
  FROM models m
  LEFT JOIN predictions p ON m.model_id = p.model_id;
  ```
  </details>

---

### 3. Right Join
- **Description**: `RIGHT JOIN` returns all rows from the right table, with matching rows from the left (NULL if no match).
- **Interview Focus**: Tests understanding of right-table priority and rare use cases.

#### Question 3.1: Predictions with Model Details
- **Problem**: You need all predictions, even if model details are missing. Write a query to join `predictions` (right) with `models` to show `prediction_id`, `score`, and `model_name` (NULL if no model).
- **Trick**: Tests if you prioritize the right table, handling NULLs for unmatched rows.
- **AI/ML Use Case**: Analyzes predictions with potentially incomplete model data.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT p.prediction_id, p.score, m.model_name
  FROM models m
  RIGHT JOIN predictions p ON m.model_id = p.model_id;
  ```
  </details>

---

### 4. Full Outer Join
- **Description**: `FULL OUTER JOIN` returns all rows from both tables, with NULLs for non-matching rows.
- **Interview Focus**: Tests comprehensive data inclusion and edge case handling.

#### Question 4.1: Complete Model-Prediction Map
- **Problem**: Your team wants a complete view of models and predictions. Write a query to join `models` and `predictions` to show `model_id`, `model_name`, `prediction_id`, and `score`, including non-matching rows from both tables.
- **Trick**: Tests if you capture all data, managing NULLs on both sides.
- **AI/ML Use Case**: Audits model and prediction coverage for pipeline gaps.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT m.model_id, m.model_name, p.prediction_id, p.score
  FROM models m
  FULL OUTER JOIN predictions p ON m.model_id = p.model_id;
  ```
  </details>

---

### 5. Self-Join
- **Description**: `SELF JOIN` joins a table to itself to explore relationships within the same table.
- **Interview Focus**: Tests hierarchical or relational logic within one dataset.

#### Question 5.1: Model Version Pairs
- **Problem**: You’re tracking model versions in `models`. Write a query to self-join `models` to show pairs of `model_name` values (as `model1`, `model2`) where `model1`’s `created_date` is earlier than `model2`’s, for the same `base_model_id`.
- **Trick**: Tests if you use aliases and conditions to compare rows within the same table.
- **AI/ML Use Case**: Analyzes model version progression.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT m1.model_name AS model1, m2.model_name AS model2
  FROM models m1
  INNER JOIN models m2 ON m1.base_model_id = m2.base_model_id
  WHERE m1.created_date < m2.created_date;
  ```
  </details>

---

### 6. Cross-Join
- **Description**: `CROSS JOIN` combines every row from one table with every row from another, creating a Cartesian product.
- **Interview Focus**: Tests understanding of combinatorial logic and performance implications.

#### Question 6.1: Event-Model Combinations
- **Problem**: Your ML pipeline needs to test all possible event-model pairings. Write a query to cross-join `event_logs` and `models` to show `log_id`, `event_type`, `model_id`, and `model_name` for all combinations.
- **Trick**: Tests if you apply `CROSS JOIN` intentionally, managing large result sets.
- **AI/ML Use Case**: Generates test scenarios for pipeline events across models.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT e.log_id, e.event_type, m.model_id, m.model_name
  FROM event_logs e
  CROSS JOIN models m;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Core**: Begin with `Inner Join` to nail matching logic.
- **Watch for Traps**: Interviewers test NULL handling in `Left`/`Right` joins, over-fetching in `Full Outer`, alias errors in `Self-Join`, and performance issues in `Cross-Join`.
- **Explain Clearly**: Practice justifying join choices (e.g., `Left Join` for optional data) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Joins**: Use conditions to limit rows; avoid unnecessary `Cross-Join` explosions.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test join operations. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Inner Join, Left Join, Right Join, Full Outer Join
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
- **Sample Data** (6 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 102, 0.95, '2025-08-17'),
  (4, 102, 0.78, '2025-08-18'),
  (5, 103, 0.91, '2025-08-19'),
  (6, 999, 0.85, '2025-08-20');
  ```

### Schema 2: models
- **Used In**: Inner Join, Left Join, Right Join, Full Outer Join, Self-Join, Cross-Join
- **Description**: Stores ML model metadata with versioning.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE,
      base_model_id INT
  );
  ```
- **Sample Data** (5 rows):
  ```sql
  INSERT INTO models (model_id, model_name, created_date, base_model_id) VALUES
  (101, 'Model A v1', '2025-08-01', 1),
  (102, 'Model B', '2025-08-02', 2),
  (103, 'Model A v2', '2025-08-03', 1),
  (104, 'Model C', '2025-08-04', 3),
  (105, 'Model A v3', '2025-08-05', 1);
  ```

### Schema 3: event_logs
- **Used In**: Cross-Join
- **Description**: Logs ML pipeline events.
- **Schema**:
  ```sql
  CREATE TABLE event_logs (
      log_id INT PRIMARY KEY,
      event_type VARCHAR(50),
      status VARCHAR(20) DEFAULT 'Pending'
  );
  ```
- **Sample Data** (4 rows):
  ```sql
  INSERT INTO event_logs (log_id, event_type, status) VALUES
  (1, 'Training Start', 'Completed'),
  (2, 'Validation', 'Failed'),
  (3, 'Prediction Run', 'Completed'),
  (4, 'Model Update', 'Pending');
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run JOIN queries.
3. **Compatibility**:
   - MySQL: Supports all joins; `FULL OUTER JOIN` may require `UNION` of `LEFT` and `RIGHT` joins.
   - PostgreSQL: Fully supports all joins, including `FULL OUTER JOIN`.
   - SQL Server: Supports all joins; syntax identical to PostgreSQL.
4. **Verify Results**: Query results (e.g., `SELECT * FROM predictions p INNER JOIN models m`) to confirm row counts and NULLs.
5. **Data Scale**: Sample data is small (~15 rows total) for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Smash these Joins questions to rule SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>