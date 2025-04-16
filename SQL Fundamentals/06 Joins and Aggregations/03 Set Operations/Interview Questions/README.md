# 🎯 Interview Questions - Set Operations to Ace SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Set Operations and lock in that AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** hub for **Set Operations**! 💻 This README is your ultimate prep tool, packed with tricky, real-world questions covering **four core concepts**: `Union`, `Union All`, `Intersect`, and `Except`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with a challenging, ML-themed question. With schemas, sample data, and solutions (tucked away in `<details>` tags), you’ll sharpen your dataset-combining skills, boost your confidence, and make your portfolio shine for recruiters. Let’s merge those results and crush those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Set Operations**: Perfect your ability to combine, compare, and filter datasets.
- **Power AI/ML Workflows**: Deduplicate logs, find common metrics, and isolate unique data points.
- **Shine Under Pressure**: Practice explaining set logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Union`).
   - Read the question and try writing the set operation query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify results against expected outputs.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Union All` for speed, then tackle `Intersect` or `Except` for trickier comparisons. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has a tricky question with an ML-relevant scenario, schema, and solution. Get ready to operate like a pro!

### 1. Union
- **Description**: `UNION` combines results from two queries, removing duplicates.
- **Interview Focus**: Tests deduplication and result merging.

#### Question 1.1: Combine Prediction Logs
- **Problem**: Your ML pipeline logs predictions in two tables. Write a query to use `UNION` to combine `model_id` and `score` from `predictions` and `archive_predictions`, showing unique combinations.
- **Trick**: Tests if you use `UNION` to eliminate duplicates correctly.
- **AI/ML Use Case**: Merges current and archived prediction data for analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT model_id, score
  FROM predictions
  UNION
  SELECT model_id, score
  FROM archive_predictions;
  ```
  </details>

---

### 2. Union All
- **Description**: `UNION ALL` combines results from two queries, keeping duplicates.
- **Interview Focus**: Tests performance awareness and result inclusion.

#### Question 2.1: Merge Event Logs
- **Problem**: You’re consolidating pipeline events. Write a query to use `UNION ALL` to combine `log_id` and `event_type` from `event_logs` and `archive_event_logs`, keeping all rows.
- **Trick**: Tests if you choose `UNION ALL` for speed and preserve duplicates.
- **AI/ML Use Case**: Combines active and archived event logs for auditing.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT log_id, event_type
  FROM event_logs
  UNION ALL
  SELECT log_id, event_type
  FROM archive_event_logs;
  ```
  </details>

---

### 3. Intersect
- **Description**: `INTERSECT` returns rows common to both queries.
- **Interview Focus**: Tests identification of shared data.

#### Question 3.1: Common Model IDs
- **Problem**: You need to find models in both datasets. Write a query to use `INTERSECT` to show `model_id` values present in both `predictions` and `archive_predictions`.
- **Trick**: Tests if you use `INTERSECT` to find overlapping data accurately.
- **AI/ML Use Case**: Identifies models with predictions in both current and archived tables.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT model_id
  FROM predictions
  INTERSECT
  SELECT model_id
  FROM archive_predictions;
  ```
  </details>

---

### 4. Except
- **Description**: `EXCEPT` returns rows in the first query not in the second.
- **Interview Focus**: Tests difference detection and order sensitivity.

#### Question 4.1: Unique Current Predictions
- **Problem**: You want predictions exclusive to the current dataset. Write a query to use `EXCEPT` to show `model_id` and `score` from `predictions` that aren’t in `archive_predictions`.
- **Trick**: Tests if you use `EXCEPT` to isolate unique rows, handling column alignment.
- **AI/ML Use Case**: Finds new predictions not yet archived.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT model_id, score
  FROM predictions
  EXCEPT
  SELECT model_id, score
  FROM archive_predictions;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Fast**: Begin with `Union All` for quick merges.
- **Watch for Traps**: Interviewers test `UNION` vs. `UNION ALL` performance, column mismatches in `INTERSECT`, and `EXCEPT` order errors.
- **Explain Clearly**: Practice justifying set operation choices (e.g., `UNION` for unique rows) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Operations**: Ensure compatible column types; use `UNION ALL` unless duplicates must be removed.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test set operations. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Union, Intersect, Except
- **Description**: Stores current ML predictions.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE
  );
  ```
- **Sample Data** (5 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 102, 0.95, '2025-08-17'),
  (4, 103, 0.91, '2025-08-18'),
  (5, 104, 0.88, '2025-08-19');
  ```

### Schema 2: archive_predictions
- **Used In**: Union, Intersect, Except
- **Description**: Stores archived ML predictions.
- **Schema**:
  ```sql
  CREATE TABLE archive_predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE
  );
  ```
- **Sample Data** (5 rows):
  ```sql
  INSERT INTO archive_predictions (prediction_id, model_id, score, prediction_date) VALUES
  (101, 101, 0.92, '2025-07-01'),
  (102, 101, 0.85, '2025-07-02'),
  (103, 102, 0.95, '2025-07-03'),
  (104, 105, 0.89, '2025-07-04'),
  (105, 106, 0.90, '2025-07-05');
  ```

### Schema 3: event_logs
- **Used In**: Union All
- **Description**: Stores current ML pipeline events.
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

### Schema 4: archive_event_logs
- **Used In**: Union All
- **Description**: Stores archived ML pipeline events.
- **Schema**:
  ```sql
  CREATE TABLE archive_event_logs (
      log_id INT PRIMARY KEY,
      event_type VARCHAR(50),
      status VARCHAR(20) DEFAULT 'Pending'
  );
  ```
- **Sample Data** (4 rows):
  ```sql
  INSERT INTO archive_event_logs (log_id, event_type, status) VALUES
  (101, 'Training Start', 'Completed'),
  (102, 'Prediction Run', 'Completed'),
  (103, 'Validation', 'Completed'),
  (104, 'Testing', 'Failed');
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run set operation queries.
3. **Compatibility**:
   - MySQL: Supports `UNION` and `UNION ALL`; `INTERSECT` and `EXCEPT` require workarounds (e.g., `JOIN` or `NOT IN`).
   - PostgreSQL: Fully supports all operations (`UNION`, `UNION ALL`, `INTERSECT`, `EXCEPT`).
   - SQL Server: Supports all operations; `EXCEPT` is equivalent to `MINUS` in other systems.
4. **Verify Results**: Query results to confirm row counts, duplicates, or exclusions (e.g., `SELECT model_id FROM predictions INTERSECT ...`).
5. **Data Scale**: Sample data is small (~18 rows total) for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Smash these Set Operations questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>