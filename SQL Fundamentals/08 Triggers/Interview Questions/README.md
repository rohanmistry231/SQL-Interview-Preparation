# 🎯 Interview Questions - Triggers to Dominate SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Triggers and secure that AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** zone for **Triggers**! 💻 This README is your ultimate prep tool, packed with tricky, real-world questions covering **four core concepts**: `Creating Triggers`, `BEFORE Triggers`, `AFTER Triggers`, and `Dropping Triggers`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, sample data, and solutions (hidden in `<details>` tags), you’ll sharpen your automation and integrity skills, boost your confidence, and make your portfolio shine for recruiters. Let’s fire up those triggers and crush those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Triggers**: Perfect your ability to enforce rules and automate database actions.
- **Power AI/ML Workflows**: Validate prediction data, log pipeline changes, and maintain data integrity.
- **Shine Under Pressure**: Practice explaining trigger logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Creating Triggers`).
   - Read the question and try writing the trigger in a sandbox (MySQL, PostgreSQL, SQL Server, etc.).
3. **Test Your Trigger**: Perform `INSERT`, `UPDATE`, or `DELETE` to verify trigger behavior.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your trigger logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Creating Triggers` to grasp syntax, then tackle `BEFORE` and `AFTER Triggers` for timing. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to trigger like a pro!

### 1. Creating Triggers
- **Description**: `CREATE TRIGGER` defines automated actions for `INSERT`, `UPDATE`, or `DELETE` events.
- **Interview Focus**: Tests syntax and event handling.

#### Question 1.1: Log New Predictions
- **Problem**: Your ML pipeline needs to track new predictions. Write a trigger to insert a log entry into `event_logs` with `event_type='New Prediction'` and `status='Completed'` after each `INSERT` on `predictions`.
- **Trick**: Tests if you create an `AFTER INSERT` trigger with correct logging logic.
- **AI/ML Use Case**: Automates pipeline activity tracking.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER after_prediction_insert
  AFTER INSERT ON predictions
  FOR EACH ROW
  BEGIN
      INSERT INTO event_logs (log_id, event_type, status)
      VALUES ((SELECT COALESCE(MAX(log_id), 0) + 1 FROM event_logs), 'New Prediction', 'Completed');
  END //
  DELIMITER ;
  ```
  </details>

#### Question 1.2: Track Model Updates
- **Problem**: You want to monitor model metadata changes. Write a trigger to log an `event_type='Model Updated'` entry in `event_logs` after each `UPDATE` on `models`.
- **Trick**: Tests if you handle `AFTER UPDATE` events correctly.
- **AI/ML Use Case**: Tracks model versioning changes.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER after_model_update
  AFTER UPDATE ON models
  FOR EACH ROW
  BEGIN
      INSERT INTO event_logs (log_id, event_type, status)
      VALUES ((SELECT COALESCE(MAX(log_id), 0) + 1 FROM event_logs), 'Model Updated', 'Completed');
  END //
  DELIMITER ;
  ```
  </details>

---

### 2. BEFORE Triggers
- **Description**: `BEFORE` triggers execute before the triggering event, allowing data modification.
- **Interview Focus**: Tests data validation and pre-event logic.

#### Question 2.1: Validate Prediction Score
- **Problem**: Your pipeline requires valid scores. Write a `BEFORE INSERT` trigger on `predictions` to set `score` to 0 if it’s negative.
- **Trick**: Tests if you modify `NEW` values in a `BEFORE INSERT` trigger.
- **AI/ML Use Case**: Ensures prediction data integrity.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER before_prediction_insert
  BEFORE INSERT ON predictions
  FOR EACH ROW
  BEGIN
      IF NEW.score < 0 THEN
          SET NEW.score = 0;
      END IF;
  END //
  DELIMITER ;
  ```
  </details>

#### Question 2.2: Standardize Model Name
- **Problem**: Model names must be uppercase. Write a `BEFORE UPDATE` trigger on `models` to convert `model_name` to uppercase before saving.
- **Trick**: Tests if you manipulate `NEW` fields in a `BEFORE UPDATE` trigger.
- **AI/ML Use Case**: Enforces consistent model naming.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER before_model_update
  BEFORE UPDATE ON models
  FOR EACH ROW
  BEGIN
      SET NEW.model_name = UPPER(NEW.model_name);
  END //
  DELIMITER ;
  ```
  </details>

---

### 3. AFTER Triggers
- **Description**: `AFTER` triggers execute after the triggering event, ideal for logging or cascading actions.
- **Interview Focus**: Tests post-event automation and data consistency.

#### Question 3.1: Archive Deleted Predictions
- **Problem**: You need to retain deleted predictions. Write an `AFTER DELETE` trigger on `predictions` to insert deleted rows into `archive_predictions`.
- **Trick**: Tests if you use `OLD` values in an `AFTER DELETE` trigger.
- **AI/ML Use Case**: Preserves prediction history for audits.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER after_prediction_delete
  AFTER DELETE ON predictions
  FOR EACH ROW
  BEGIN
      INSERT INTO archive_predictions (prediction_id, model_id, score, prediction_date)
      VALUES (OLD.prediction_id, OLD.model_id, OLD.score, OLD.prediction_date);
  END //
  DELIMITER ;
  ```
  </details>

#### Question 3.2: Log Prediction Score Changes
- **Problem**: You want to track score updates. Write an `AFTER UPDATE` trigger on `predictions` to log the old and new `score` in `event_logs` when `score` changes.
- **Trick**: Tests if you compare `OLD` and `NEW` in an `AFTER UPDATE` trigger.
- **AI/ML Use Case**: Monitors prediction metric adjustments.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER after_prediction_score_update
  AFTER UPDATE ON predictions
  FOR EACH ROW
  BEGIN
      IF OLD.score != NEW.score THEN
          INSERT INTO event_logs (log_id, event_type, status)
          VALUES ((SELECT COALESCE(MAX(log_id), 0) + 1 FROM event_logs),
                  CONCAT('Score Updated: ', OLD.score, ' to ', NEW.score), 'Completed');
      END IF;
  END //
  DELIMITER ;
  ```
  </details>

---

### 4. Dropping Triggers
- **Description**: `DROP TRIGGER` removes a trigger from the database.
- **Interview Focus**: Tests cleanup syntax and safety practices.

#### Question 4.1: Remove Prediction Log Trigger
- **Problem**: Your team no longer needs `after_prediction_insert`. Write a query to drop it safely.
- **Trick**: Tests if you use `DROP TRIGGER` with safety checks.
- **AI/ML Use Case**: Cleans up obsolete pipeline automation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP TRIGGER IF EXISTS after_prediction_insert;
  ```
  </details>

#### Question 4.2: Drop Model Name Trigger
- **Problem**: `before_model_update` is outdated. Write a query to drop it securely.
- **Trick**: Tests if you ensure the trigger exists before dropping.
- **AI/ML Use Case**: Maintains a lean database environment.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP TRIGGER IF EXISTS before_model_update;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Simple**: Begin with `Creating Triggers` to nail syntax.
- **Watch for Traps**: Interviewers test `OLD` vs. `NEW` misuse, missing `FOR EACH ROW`, and unsafe `DROP` calls.
- **Explain Clearly**: Practice justifying trigger use (e.g., data validation vs. logging) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Triggers**: Keep logic lightweight to avoid performance hits; test for recursive trigger risks.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test trigger operations. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Creating Triggers, BEFORE Triggers, AFTER Triggers
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
- **Sample Data** (5 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 102, 0.95, '2025-08-17'),
  (4, 102, 0.78, '2025-08-18'),
  (5, 103, 0.91, '2025-08-19');
  ```

### Schema 2: models
- **Used In**: Creating Triggers, BEFORE Triggers
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
- **Used In**: Creating Triggers, AFTER Triggers
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

### Schema 4: archive_predictions
- **Used In**: AFTER Triggers
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

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Triggers**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to create, test, and drop triggers.
3. **Compatibility**:
   - MySQL: Uses `DELIMITER` for triggers; supports `BEFORE`/`AFTER` for `INSERT`, `UPDATE`, `DELETE`; `DROP TRIGGER IF EXISTS` for safety.
   - PostgreSQL: Uses `CREATE OR REPLACE TRIGGER` with functions; `FOR EACH ROW` syntax; no `DELIMITER` needed.
   - SQL Server: Uses `CREATE TRIGGER`; supports `AFTER` (or `FOR`) and `INSTEAD OF`; similar `DROP` syntax.
4. **Verify Results**: Perform `INSERT`, `UPDATE`, or `DELETE` on tables (e.g., `INSERT INTO predictions ...`) and query `event_logs` or `archive_predictions` to confirm trigger actions.
5. **Data Scale**: Sample data is small (~16 rows total) for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Crush these Triggers questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>