# 🎯 Interview Questions - Stored Procedures to Crush SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Stored Procedures and land that AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** arena for **Stored Procedures**! 💻 This README is your secret weapon, loaded with tricky, real-world questions covering **four core concepts**: `Creating Procedures`, `Parameters`, `Calling Procedures`, and `Dropping Procedures`. Crafted to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, sample data, and solutions (hidden in `<details>` tags), you’ll hone your automation skills, boost your confidence, and make your portfolio shine for recruiters. Let’s script those procedures and ace those interviews!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Stored Procedures**: Perfect your ability to automate and manage complex database tasks.
- **Power AI/ML Workflows**: Streamline prediction analysis, parameterize pipeline queries, and clean up routines.
- **Shine Under Pressure**: Practice explaining procedure logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Creating Procedures`).
   - Read the question and try writing the procedure in a sandbox (MySQL, PostgreSQL, SQL Server, etc.).
3. **Test Your Procedure**: Create and call it to verify results or behavior.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Creating Procedures` to grasp syntax, then tackle `Parameters` and `Calling Procedures` for dynamic use. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to script like a pro!

### 1. Creating Procedures
- **Description**: `CREATE PROCEDURE` defines reusable SQL routines for automation.
- **Interview Focus**: Tests syntax accuracy and logic encapsulation.

#### Question 1.1: Log Prediction Count
- **Problem**: Your ML team needs to track prediction volume. Write a stored procedure to count rows in `predictions` and insert the count with a timestamp into `event_logs` as a 'Prediction Count' event.
- **Trick**: Tests if you create a procedure with `INSERT` and `SELECT COUNT` logic.
- **AI/ML Use Case**: Automates prediction activity logging.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE LogPredictionCount()
  BEGIN
      DECLARE pred_count INT;
      SELECT COUNT(*) INTO pred_count FROM predictions;
      INSERT INTO event_logs (log_id, event_type, status)
      VALUES ((SELECT COALESCE(MAX(log_id), 0) + 1 FROM event_logs), 'Prediction Count', CONCAT('Count: ', pred_count));
  END //
  DELIMITER ;
  ```
  </details>

#### Question 1.2: Archive Old Predictions
- **Problem**: You want to clean up old data. Write a stored procedure to move predictions older than '2025-08-18' from `predictions` to `archive_predictions`.
- **Trick**: Tests if you handle `INSERT` and `DELETE` in a single procedure.
- **AI/ML Use Case**: Manages prediction data lifecycle.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE ArchiveOldPredictions()
  BEGIN
      INSERT INTO archive_predictions (prediction_id, model_id, score, prediction_date)
      SELECT prediction_id, model_id, score, prediction_date
      FROM predictions
      WHERE prediction_date < '2025-08-18';
      DELETE FROM predictions WHERE prediction_date < '2025-08-18';
  END //
  DELIMITER ;
  ```
  </details>

---

### 2. Parameters
- **Description**: Parameters make procedures dynamic by accepting input values.
- **Interview Focus**: Tests parameter syntax and dynamic query building.

#### Question 2.1: Filter Predictions by Model
- **Problem**: Your team needs model-specific stats. Write a stored procedure with a `model_id` parameter to return the average `score` for predictions of that `model_id`.
- **Trick**: Tests if you use an `IN` parameter and aggregate correctly.
- **AI/ML Use Case**: Analyzes performance for a specific model.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE GetModelAvgScore(IN input_model_id INT)
  BEGIN
      SELECT AVG(score) AS avg_score
      FROM predictions
      WHERE model_id = input_model_id;
  END //
  DELIMITER ;
  ```
  </details>

#### Question 2.2: Update Event Status
- **Problem**: You’re managing pipeline events. Write a stored procedure with `log_id` and `new_status` parameters to update the `status` of an event in `event_logs`.
- **Trick**: Tests if you use multiple parameters and `UPDATE` safely.
- **AI/ML Use Case**: Updates pipeline event statuses dynamically.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE UpdateEventStatus(IN input_log_id INT, IN new_status VARCHAR(20))
  BEGIN
      UPDATE event_logs
      SET status = new_status
      WHERE log_id = input_log_id;
  END //
  DELIMITER ;
  ```
  </details>

---

### 3. Calling Procedures
- **Description**: `CALL` executes stored procedures, passing parameters if needed.
- **Interview Focus**: Tests procedure invocation and result handling.

#### Question 3.1: Run Prediction Count
- **Problem**: You’ve created `LogPredictionCount`. Write a query to call it and then select the latest `event_logs` entry to verify the result.
- **Trick**: Tests if you call a procedure and check its effect.
- **AI/ML Use Case**: Verifies automated logging in the pipeline.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CALL LogPredictionCount();
  SELECT * FROM event_logs
  ORDER BY log_id DESC
  LIMIT 1;
  ```
  </details>

#### Question 3.2: Get Model Score
- **Problem**: You’ve created `GetModelAvgScore`. Write a query to call it for `model_id=101` and display the result.
- **Trick**: Tests if you pass parameters correctly in a `CALL`.
- **AI/ML Use Case**: Fetches model-specific metrics on demand.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CALL GetModelAvgScore(101);
  ```
  </details>

---

### 4. Dropping Procedures
- **Description**: `DROP PROCEDURE` removes a stored procedure from the database.
- **Interview Focus**: Tests cleanup syntax and safety checks.

#### Question 4.1: Remove Old Procedure
- **Problem**: Your team no longer needs `LogPredictionCount`. Write a query to drop it safely.
- **Trick**: Tests if you use `DROP PROCEDURE` with optional safety checks.
- **AI/ML Use Case**: Cleans up obsolete pipeline automation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP PROCEDURE IF EXISTS LogPredictionCount;
  ```
  </details>

#### Question 4.2: Drop Unused Model Procedure
- **Problem**: `GetModelAvgScore` is outdated. Write a query to drop it securely.
- **Trick**: Tests if you ensure the procedure exists before dropping.
- **AI/ML Use Case**: Maintains a lean database environment.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP PROCEDURE IF EXISTS GetModelAvgScore;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Basic**: Begin with `Creating Procedures` to nail syntax.
- **Watch for Traps**: Interviewers test delimiter issues in `Creating`, parameter mismatches in `Parameters`, and missing `CALL` arguments.
- **Explain Clearly**: Practice justifying procedure use (e.g., automation benefits) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Procedures**: Keep logic simple; use parameters for flexibility.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test stored procedures. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Creating Procedures, Parameters, Calling Procedures
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
  (6, 103, 0.85, '2025-08-20');
  ```

### Schema 2: archive_predictions
- **Used In**: Creating Procedures
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
- **Sample Data** (3 rows):
  ```sql
  INSERT INTO archive_predictions (prediction_id, model_id, score, prediction_date) VALUES
  (101, 101, 0.89, '2025-07-01'),
  (102, 102, 0.93, '2025-07-02'),
  (103, 103, 0.86, '2025-07-03');
  ```

### Schema 3: event_logs
- **Used In**: Creating Procedures, Parameters, Calling Procedures
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
2. **Test Procedures**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to create, call, and drop procedures.
3. **Compatibility**:
   - MySQL: Uses `DELIMITER` for procedures; supports `IN` parameters; `DROP PROCEDURE IF EXISTS` for safety.
   - PostgreSQL: Uses `CREATE OR REPLACE PROCEDURE`; `CALL` syntax; no `DELIMITER` needed.
   - SQL Server: Uses `CREATE PROCEDURE`; supports `EXEC` or `EXECUTE` for calling; similar `DROP` syntax.
4. **Verify Results**: Query tables (e.g., `SELECT * FROM event_logs`) after calling procedures to confirm changes.
5. **Data Scale**: Sample data is small (~13 rows total) for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Smash these Stored Procedures questions to rule SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>