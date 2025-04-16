# 🎯 Interview Questions - Cursors to Nail SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Cursors and snag that AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** hub for **Cursors**! 💻 This README is your go-to resource, loaded with tricky, real-world questions covering **four core concepts**: `Declaring Cursors`, `Opening Cursors`, `Fetching Data`, and `Closing Cursors`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, sample data, and solutions (tucked away in `<details>` tags), you’ll hone your row-by-row processing skills, boost your confidence, and make your portfolio shine for recruiters. Let’s loop through those rows and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Cursors**: Perfect your ability to process data iteratively in stored procedures.
- **Power AI/ML Workflows**: Batch-process predictions, compute metrics, and log pipeline events.
- **Shine Under Pressure**: Practice explaining cursor logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Declaring Cursors`).
   - Read the question and try writing the cursor logic in a sandbox (MySQL, PostgreSQL, SQL Server, etc.).
3. **Test Your Cursor**: Run the procedure to verify data processing or output.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your cursor logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Declaring Cursors` to grasp setup, then tackle `Fetching Data` for processing. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to cursor like a pro!

### 1. Declaring Cursors
- **Description**: `DECLARE CURSOR` defines a cursor to iterate over a query result set.
- **Interview Focus**: Tests cursor declaration syntax and query integration.

#### Question 1.1: Declare Prediction Cursor
- **Problem**: Your ML pipeline needs to process predictions. Write a stored procedure that declares a cursor to select all `prediction_id` and `score` from `predictions` where `score > 0.9`.
- **Trick**: Tests if you declare a cursor with a filtered `SELECT` correctly.
- **AI/ML Use Case**: Prepares high-confidence predictions for analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE ProcessHighScores()
  BEGIN
      DECLARE high_score_cursor CURSOR FOR
          SELECT prediction_id, score
          FROM predictions
          WHERE score > 0.9;
  END //
  DELIMITER ;
  ```
  </details>

#### Question 1.2: Declare Model Cursor
- **Problem**: You’re auditing models. Write a stored procedure that declares a cursor to select `model_id` and `model_name` from `models` created after '2025-08-02'.
- **Trick**: Tests if you tie a cursor to a date-filtered query.
- **AI/ML Use Case**: Targets recent models for review.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE AuditNewModels()
  BEGIN
      DECLARE model_cursor CURSOR FOR
          SELECT model_id, model_name
          FROM models
          WHERE created_date > '2025-08-02';
  END //
  DELIMITER ;
  ```
  </details>

---

### 2. Opening Cursors
- **Description**: `OPEN` initializes a cursor to start fetching rows.
- **Interview Focus**: Tests cursor activation and procedure flow.

#### Question 2.1: Open Prediction Cursor
- **Problem**: Using the cursor from Question 1.1, extend the procedure to open the cursor for processing high-score predictions.
- **Trick**: Tests if you pair `DECLARE` with `OPEN` correctly.
- **AI/ML Use Case**: Initiates batch processing of predictions.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE ProcessHighScores()
  BEGIN
      DECLARE high_score_cursor CURSOR FOR
          SELECT prediction_id, score
          FROM predictions
          WHERE score > 0.9;
      OPEN high_score_cursor;
  END //
  DELIMITER ;
  ```
  </details>

#### Question 2.2: Open Event Log Cursor
- **Problem**: You’re analyzing pipeline events. Write a stored procedure that declares and opens a cursor for `log_id` and `event_type` from `event_logs` where `status = 'Completed'`.
- **Trick**: Tests if you combine declaration and opening for filtered data.
- **AI/ML Use Case**: Starts processing successful pipeline events.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE ProcessCompletedEvents()
  BEGIN
      DECLARE event_cursor CURSOR FOR
          SELECT log_id, event_type
          FROM event_logs
          WHERE status = 'Completed';
      OPEN event_cursor;
  END //
  DELIMITER ;
  ```
  </details>

---

### 3. Fetching Data
- **Description**: `FETCH` retrieves the next row from a cursor into variables.
- **Interview Focus**: Tests row-by-row processing and loop control.

#### Question 3.1: Fetch and Log Predictions
- **Problem**: Extend Question 2.1 to fetch each `prediction_id` and `score` from the cursor, logging them into `event_logs` with `event_type='High Score'` until no rows remain.
- **Trick**: Tests if you use `FETCH`, variables, and a loop with exit conditions.
- **AI/ML Use Case**: Logs high-confidence predictions for monitoring.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE ProcessHighScores()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE pred_id INT;
      DECLARE pred_score FLOAT;
      DECLARE high_score_cursor CURSOR FOR
          SELECT prediction_id, score
          FROM predictions
          WHERE score > 0.9;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
      OPEN high_score_cursor;
      read_loop: LOOP
          FETCH high_score_cursor INTO pred_id, pred_score;
          IF done THEN
              LEAVE read_loop;
          END IF;
          INSERT INTO event_logs (log_id, event_type, status)
          VALUES ((SELECT COALESCE(MAX(log_id), 0) + 1 FROM event_logs),
                  'High Score', CONCAT('ID: ', pred_id, ', Score: ', pred_score));
      END LOOP;
      CLOSE high_score_cursor;
  END //
  DELIMITER ;
  ```
  </details>

#### Question 3.2: Fetch and Update Models
- **Problem**: Extend Question 1.2 to fetch each `model_id` and `model_name`, appending '_Reviewed' to `model_name` in `models` if not already present.
- **Trick**: Tests if you fetch data and use `UPDATE` in a cursor loop.
- **AI/ML Use Case**: Marks models as reviewed during auditing.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE AuditNewModels()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE m_id INT;
      DECLARE m_name VARCHAR(100);
      DECLARE model_cursor CURSOR FOR
          SELECT model_id, model_name
          FROM models
          WHERE created_date > '2025-08-02';
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
      OPEN model_cursor;
      read_loop: LOOP
          FETCH model_cursor INTO m_id, m_name;
          IF done THEN
              LEAVE read_loop;
          END IF;
          IF m_name NOT LIKE '%_Reviewed' THEN
              UPDATE models
              SET model_name = CONCAT(m_name, '_Reviewed')
              WHERE model_id = m_id;
          END IF;
      END LOOP;
      CLOSE model_cursor;
  END //
  DELIMITER ;
  ```
  </details>

---

### 4. Closing Cursors
- **Description**: `CLOSE` releases a cursor’s resources after processing.
- **Interview Focus**: Tests resource management and procedure cleanup.

#### Question 4.1: Close Prediction Cursor
- **Problem**: Using the procedure from Question 3.1, ensure the cursor is closed properly after processing. Show the closing part explicitly.
- **Trick**: Tests if you include `CLOSE` to free resources.
- **AI/ML Use Case**: Ensures efficient pipeline processing.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE ProcessHighScores()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE pred_id INT;
      DECLARE pred_score FLOAT;
      DECLARE high_score_cursor CURSOR FOR
          SELECT prediction_id, score
          FROM predictions
          WHERE score > 0.9;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
      OPEN high_score_cursor;
      read_loop: LOOP
          FETCH high_score_cursor INTO pred_id, pred_score;
          IF done THEN
              LEAVE read_loop;
          END IF;
          INSERT INTO event_logs (log_id, event_type, status)
          VALUES ((SELECT COALESCE(MAX(log_id), 0) + 1 FROM event_logs),
                  'High Score', CONCAT('ID: ', pred_id, ', Score: ', pred_score));
      END LOOP;
      CLOSE high_score_cursor;
  END //
  DELIMITER ;
  ```
  </details>

#### Question 4.2: Close Event Cursor
- **Problem**: Write a procedure that declares, opens, fetches `log_id` from `event_logs` where `status = 'Failed'`, logs a count of failed events, and closes the cursor.
- **Trick**: Tests if you complete the cursor lifecycle with `CLOSE`.
- **AI/ML Use Case**: Summarizes pipeline failures for reporting.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE LogFailedEvents()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE e_id INT;
      DECLARE fail_count INT DEFAULT 0;
      DECLARE event_cursor CURSOR FOR
          SELECT log_id
          FROM event_logs
          WHERE status = 'Failed';
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;
      OPEN event_cursor;
      read_loop: LOOP
          FETCH event_cursor INTO e_id;
          IF done THEN
              LEAVE read_loop;
          END IF;
          SET fail_count = fail_count + 1;
      END LOOP;
      INSERT INTO event_logs (log_id, event_type, status)
      VALUES ((SELECT COALESCE(MAX(log_id), 0) + 1 FROM event_logs),
              'Failure Report', CONCAT('Failed Events: ', fail_count));
      CLOSE event_cursor;
  END //
  DELIMITER ;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Basic**: Begin with `Declaring Cursors` to nail syntax.
- **Watch for Traps**: Interviewers test missing `CLOSE`, unhandled `NOT FOUND`, and cursor re-opening errors.
- **Explain Clearly**: Practice justifying cursor use (e.g., row-by-row vs. set-based) for whiteboard rounds.
- **Test Thoroughly**: Run procedures in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Cursors**: Use cursors only when set-based queries won’t do; minimize loop complexity.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test cursor operations. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Declaring Cursors, Opening Cursors, Fetching Data, Closing Cursors
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

### Schema 2: models
- **Used In**: Declaring Cursors, Fetching Data
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
- **Used In**: Opening Cursors, Fetching Data, Closing Cursors
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
  (5, 'Testing', 'Failed');
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Cursors**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to create and run procedures with cursors.
3. **Compatibility**:
   - MySQL: Supports cursors in stored procedures; uses `DELIMITER` and `DECLARE CONTINUE HANDLER` for `NOT FOUND`.
   - PostgreSQL: Supports cursors with `DECLARE`, `OPEN`, `FETCH`, `CLOSE`; no `DELIMITER` needed; uses `LOOP` with `EXIT WHEN`.
   - SQL Server: Supports cursors with `DECLARE`, `OPEN`, `FETCH NEXT`, `CLOSE`, `DEALLOCATE`; uses `WHILE` for loops.
4. **Verify Results**: Call procedures (e.g., `CALL ProcessHighScores();`) and query tables (e.g., `SELECT * FROM event_logs`) to confirm cursor actions.
5. **Data Scale**: Sample data is small (~15 rows total) for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Smash these Cursors questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>