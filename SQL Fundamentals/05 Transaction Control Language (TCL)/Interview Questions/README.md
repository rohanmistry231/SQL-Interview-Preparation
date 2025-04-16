# 🎯 Interview Questions - TCL to Dominate SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master TCL and lock in your AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** arena for **Transaction Control Language (TCL)**! 💻 This README is your secret weapon, loaded with tricky, real-world questions covering **four core concepts**: `COMMIT`, `ROLLBACK`, `SET TRANSACTION`, and `SAVEPOINT`. Crafted to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, sample data, and solutions (tucked away in `<details>` tags), you’ll hone your transaction management skills, boost your confidence, and make your portfolio stand out for recruiters. Let’s control those transactions and crush those interviews!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master TCL**: Perfect your ability to manage data integrity through transactions.
- **Power AI/ML Workflows**: Ensure reliable dataset updates, recover from pipeline errors, and isolate critical operations.
- **Shine Under Pressure**: Practice explaining transaction logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `COMMIT`).
   - Read the question and try writing the TCL query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify transaction outcomes (e.g., data saved or reverted).
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `COMMIT` and `ROLLBACK` for transaction basics, then tackle `SAVEPOINT` for advanced control. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to transact like a pro!

### 1. COMMIT
- **Description**: `COMMIT` saves all changes made in a transaction to the database permanently.
- **Interview Focus**: Tests understanding of transaction finalization and data persistence.

#### Question 1.1: Save Model Predictions
- **Problem**: Your ML pipeline inserts new predictions. Write a transaction to insert a prediction (`prediction_id=6, model_id=103, score=0.88, prediction_date='2025-08-20'`) into `predictions` and commit it.
- **Trick**: Tests if you pair `INSERT` with `COMMIT` correctly to ensure data is saved.
- **AI/ML Use Case**: Persists model outputs for analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  BEGIN;
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date)
  VALUES (6, 103, 0.88, '2025-08-20');
  COMMIT;
  ```
  </details>

#### Question 1.2: Log Pipeline Event
- **Problem**: You’re logging a pipeline event. Write a transaction to insert an event (`log_id=4, event_type='Model Update', status='Completed'`) into `event_logs` and commit it.
- **Trick**: Ensures you commit after insertion to avoid data loss.
- **AI/ML Use Case**: Records pipeline milestones permanently.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  BEGIN;
  INSERT INTO event_logs (log_id, event_type, status)
  VALUES (4, 'Model Update', 'Completed');
  COMMIT;
  ```
  </details>

---

### 2. ROLLBACK
- **Description**: `ROLLBACK` undoes all changes made in a transaction, reverting the database to its prior state.
- **Interview Focus**: Tests error recovery and transaction reversal.

#### Question 2.1: Undo Faulty Prediction
- **Problem**: A prediction update contains errors. Write a transaction to update `predictions` by setting `score=0.99` for `model_id=101`, but roll it back due to invalid scores.
- **Trick**: Tests if you use `ROLLBACK` to discard unintended changes.
- **AI/ML Use Case**: Reverts incorrect model output updates.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  BEGIN;
  UPDATE predictions
  SET score = 0.99
  WHERE model_id = 101;
  ROLLBACK;
  ```
  </details>

#### Question 2.2: Revert Event Log Error
- **Problem**: An event log entry was added incorrectly. Write a transaction to insert an event (`log_id=5, event_type='Error Log', status='Failed'`) into `event_logs`, but roll it back due to a duplicate `log_id`.
- **Trick**: Ensures you roll back to prevent duplicate key violations.
- **AI/ML Use Case**: Undoes faulty pipeline logging.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  BEGIN;
  INSERT INTO event_logs (log_id, event_type, status)
  VALUES (5, 'Error Log', 'Failed');
  ROLLBACK;
  ```
  </details>

---

### 3. SET TRANSACTION
- **Description**: `SET TRANSACTION` configures transaction properties (e.g., isolation level, read-only mode) before starting.
- **Interview Focus**: Tests transaction isolation and configuration knowledge.

#### Question 3.1: Isolate Prediction Read
- **Problem**: You need to query predictions without interference. Write a transaction to set the isolation level to `SERIALIZABLE` and select all rows from `predictions` for analysis, then commit.
- **Trick**: Tests if you configure `SET TRANSACTION` for high isolation correctly.
- **AI/ML Use Case**: Ensures consistent data reads for model evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SET TRANSACTION ISOLATION LEVEL SERIALIZABLE;
  BEGIN;
  SELECT * FROM predictions;
  COMMIT;
  ```
  </details>

#### Question 3.2: Read-Only Model Check
- **Problem**: Your ML team needs to inspect models safely. Write a transaction to set a read-only mode and select all rows from `models`, then commit.
- **Trick**: Ensures you use `SET TRANSACTION READ ONLY` to prevent accidental writes.
- **AI/ML Use Case**: Protects model metadata during audits.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SET TRANSACTION READ ONLY;
  BEGIN;
  SELECT * FROM models;
  COMMIT;
  ```
  </details>

---

### 4. SAVEPOINT
- **Description**: `SAVEPOINT` marks a point in a transaction to roll back to without undoing everything.
- **Interview Focus**: Tests partial rollback and transaction control granularity.

#### Question 4.1: Partial Prediction Update
- **Problem**: You’re updating predictions but want to test changes. Write a transaction to insert a prediction (`prediction_id=7, model_id=103, score=0.85, prediction_date='2025-08-21'`), set a savepoint, update its `score` to 0.90, then roll back to the savepoint and commit.
- **Trick**: Tests if you use `SAVEPOINT` and `ROLLBACK TO` for partial control.
- **AI/ML Use Case**: Tests prediction updates before finalizing.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  BEGIN;
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date)
  VALUES (7, 103, 0.85, '2025-08-21');
  SAVEPOINT prediction_insert;
  UPDATE predictions
  SET score = 0.90
  WHERE prediction_id = 7;
  ROLLBACK TO prediction_insert;
  COMMIT;
  ```
  </details>

#### Question 4.2: Event Log Test
- **Problem**: You’re logging events cautiously. Write a transaction to insert an event (`log_id=6, event_type='Test Run', status='Pending'`), set a savepoint, update its `status` to 'Failed', roll back to the savepoint, and commit.
- **Trick**: Ensures you manage savepoints to revert specific changes.
- **AI/ML Use Case**: Safely tests pipeline event logging.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  BEGIN;
  INSERT INTO event_logs (log_id, event_type, status)
  VALUES (6, 'Test Run', 'Pending');
  SAVEPOINT event_insert;
  UPDATE event_logs
  SET status = 'Failed'
  WHERE log_id = 6;
  ROLLBACK TO event_insert;
  COMMIT;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Basic**: Begin with `COMMIT` and `ROLLBACK` to nail transaction outcomes.
- **Watch for Traps**: Interviewers test missing `COMMIT` in transactions, overusing `ROLLBACK`, or incorrect `SET TRANSACTION` settings.
- **Explain Clearly**: Practice justifying transaction choices (e.g., isolation for consistency) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Transactions**: Keep transactions short to avoid locks; use savepoints for complex workflows.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test TCL operations. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: COMMIT, ROLLBACK, SET TRANSACTION, SAVEPOINT
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
- **Used In**: SET TRANSACTION
- **Description**: Stores ML model metadata.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE
  );
  ```
- **Sample Data** (3 rows):
  ```sql
  INSERT INTO models (model_id, model_name, created_date) VALUES
  (101, 'Model A', '2025-08-01'),
  (102, 'Model B', '2025-08-02'),
  (103, 'Model C', '2025-08-03');
  ```

### Schema 3: event_logs
- **Used In**: COMMIT, ROLLBACK, SAVEPOINT
- **Description**: Logs ML pipeline events.
- **Schema**:
  ```sql
  CREATE TABLE event_logs (
      log_id INT PRIMARY KEY,
      event_type VARCHAR(50),
      status VARCHAR(20) DEFAULT 'Pending'
  );
  ```
- **Sample Data** (3 rows):
  ```sql
  INSERT INTO event_logs (log_id, event_type, status) VALUES
  (1, 'Training Start', 'Completed'),
  (2, 'Validation', 'Failed'),
  (3, 'Prediction Run', 'Completed');
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run TCL operations.
3. **Compatibility**:
   - MySQL: Supports `COMMIT`, `ROLLBACK`, `SAVEPOINT`; `SET TRANSACTION` supports limited isolation levels (`REPEATABLE READ` default).
   - PostgreSQL: Fully supports all TCL commands, including `SET TRANSACTION` for all isolation levels.
   - SQL Server: Supports all commands; uses `BEGIN TRANSACTION` instead of `BEGIN`.
4. **Verify Transactions**: Check data before and after (e.g., `SELECT * FROM predictions`) to confirm `COMMIT` or `ROLLBACK` effects.
5. **Data Scale**: Sample data is small for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Smash these TCL questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>