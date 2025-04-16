# 📊 Projects - Mastering SQL Cursors

## 🌟 Overview

Welcome to the **Projects** section for **SQL Cursors**! 🚀 These five unique projects are your playground to master four core concepts—`Declaring Cursors`, `Opening Cursors`, `Fetching Data`, and `Closing Cursors`. Dive into AI/ML-themed challenges like processing model logs row-by-row or generating fraud reports, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL cursors practical and fun, helping you:
- **Apply Skills**: Iterate over ML datasets for validation or reporting.
- **Ace Interviews**: Solve row-by-row processing problems like those in ML pipelines.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Process predictions, logs, or fraud data with precision for insights.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key cursor techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Processor** | Declaring Cursors, Fetching Data | Process model logs row-by-row. |
| **Dataset Iterator** | Opening Cursors, Fetching Data | Iterate over training data for stats. |
| **Prediction Validator** | Declaring Cursors, Closing Cursors | Validate predictions with cursors. |
| **Fraud Reporter** | All Four | Generate fraud reports with cursors. |
| **Capstone: Cursors** | All Four | Build a full ML pipeline with cursors. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Processor/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL cursor logic (inside stored procedures) to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify cursor outputs.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Declaring Cursors` and `Fetching Data`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Processor
- **Folder**: `Project1_Model_Processor/`
- **Concepts**: `Declaring Cursors`, `Fetching Data`
- **Description**: Process model logs row-by-row to count 'started' messages.
- **Tasks**:
  - Create a stored procedure that declares a cursor to iterate over `model_logs` and counts logs with 'started' in `log_message`.
  - Call the procedure to display the count.
- **AI/ML Use Case**: Analyzes model training events for pipeline monitoring.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE CountStartedLogs()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE log_msg VARCHAR(255);
      DECLARE start_count INT DEFAULT 0;
      DECLARE log_cursor CURSOR FOR
          SELECT log_message FROM model_logs;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

      OPEN log_cursor;
      read_loop: LOOP
          FETCH log_cursor INTO log_msg;
          IF done THEN
              LEAVE read_loop;
          END IF;
          IF log_msg LIKE '%started%' THEN
              SET start_count = start_count + 1;
          END IF;
      END LOOP;
      CLOSE log_cursor;

      SELECT start_count AS started_logs;
  END //
  DELIMITER ;

  CALL CountStartedLogs();
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL CountStartedLogs();
  ```
  </details>

### Project 2: Dataset Iterator
- **Folder**: `Project2_Dataset_Iterator/`
- **Concepts**: `Opening Cursors`, `Fetching Data`
- **Description**: Iterate over training data to calculate average `feature1` for rows where `feature2 > 2.0`.
- **Tasks**:
  - Create a stored procedure that opens a cursor to iterate over `training_data` and computes the average `feature1` for qualifying rows.
  - Call the procedure to display the average.
- **AI/ML Use Case**: Prepares dataset statistics for model preprocessing.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE AvgFeature1()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE f1 FLOAT;
      DECLARE f2 FLOAT;
      DECLARE total_f1 FLOAT DEFAULT 0;
      DECLARE count_f1 INT DEFAULT 0;
      DECLARE data_cursor CURSOR FOR
          SELECT feature1, feature2 FROM training_data;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

      OPEN data_cursor;
      read_loop: LOOP
          FETCH data_cursor INTO f1, f2;
          IF done THEN
              LEAVE read_loop;
          END IF;
          IF f2 > 2.0 THEN
              SET total_f1 = total_f1 + f1;
              SET count_f1 = count_f1 + 1;
          END IF;
      END LOOP;
      CLOSE data_cursor;

      IF count_f1 > 0 THEN
          SELECT total_f1 / count_f1 AS avg_feature1;
      ELSE
          SELECT 'No qualifying rows' AS avg_feature1;
      END IF;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL AvgFeature1();
  ```
  </details>

### Project 3: Prediction Validator
- **Folder**: `Project3_Prediction_Validator/`
- **Concepts**: `Declaring Cursors`, `Closing Cursors`
- **Description**: Validate predictions by flagging scores below 0.8.
- **Tasks**:
  - Create a stored procedure that declares a cursor to iterate over `predictions` and inserts low scores into `prediction_flags`.
  - Call the procedure to execute and verify flags.
- **AI/ML Use Case**: Identifies weak predictions for model retraining.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE FlagLowScores()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE pred_id INT;
      DECLARE score_val FLOAT;
      DECLARE pred_cursor CURSOR FOR
          SELECT prediction_id, score FROM predictions;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

      OPEN pred_cursor;
      read_loop: LOOP
          FETCH pred_cursor INTO pred_id, score_val;
          IF done THEN
              LEAVE read_loop;
          END IF;
          IF score_val < 0.8 THEN
              INSERT INTO prediction_flags (flag_id, prediction_id, flag_reason)
              VALUES ((SELECT COALESCE(MAX(flag_id), 0) + 1 FROM prediction_flags), pred_id, 'Low score');
          END IF;
      END LOOP;
      CLOSE pred_cursor;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL FlagLowScores();
  SELECT * FROM prediction_flags;
  ```
  </details>

### Project 4: Fraud Reporter
- **Folder**: `Project4_Fraud_Reporter/`
- **Concepts**: All Four (`Declaring Cursors`, `Opening Cursors`, `Fetching Data`, `Closing Cursors`)
- **Description**: Generate a fraud report by iterating over `orders` and `fraud_flags`.
- **Tasks**:
  - Create a stored procedure that uses a cursor to match `orders` with `fraud_flags` and outputs flagged order details.
  - Call the procedure to display the report.
- **AI/ML Use Case**: Produces fraud analysis reports for model evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE FraudReport()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE ord_id INT;
      DECLARE ord_amount FLOAT;
      DECLARE flag_reason VARCHAR(100);
      DECLARE fraud_cursor CURSOR FOR
          SELECT o.order_id, o.amount, ff.flag_reason
          FROM orders o
          INNER JOIN fraud_flags ff ON o.order_id = ff.order_id;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

      CREATE TEMPORARY TABLE IF NOT EXISTS fraud_report (
          order_id INT,
          amount FLOAT,
          flag_reason VARCHAR(100)
      );

      OPEN fraud_cursor;
      read_loop: LOOP
          FETCH fraud_cursor INTO ord_id, ord_amount, flag_reason;
          IF done THEN
              LEAVE read_loop;
          END IF;
          INSERT INTO fraud_report (order_id, amount, flag_reason)
          VALUES (ord_id, ord_amount, flag_reason);
      END LOOP;
      CLOSE fraud_cursor;

      SELECT * FROM fraud_report;
      DROP TEMPORARY TABLE IF EXISTS fraud_report;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL FraudReport();
  ```
  </details>

### Project 5: Capstone - Cursors
- **Folder**: `Project5_Capstone_Cursors/`
- **Concepts**: All Four (`Declaring Cursors`, `Opening Cursors`, `Fetching Data`, `Closing Cursors`)
- **Description**: Build a full ML pipeline with cursors to process logs and predictions.
- **Tasks**:
  - Create a stored procedure that uses a cursor to count `model_logs` with 'error' messages.
  - Create a stored procedure that uses a cursor to flag predictions with scores > 0.9 in `prediction_flags`.
  - Call both procedures to verify results.
- **AI/ML Use Case**: Automates error tracking and high-confidence prediction flagging.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE CountErrorLogs()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE log_msg VARCHAR(255);
      DECLARE error_count INT DEFAULT 0;
      DECLARE log_cursor CURSOR FOR
          SELECT log_message FROM model_logs;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

      OPEN log_cursor;
      read_loop: LOOP
          FETCH log_cursor INTO log_msg;
          IF done THEN
              LEAVE read_loop;
          END IF;
          IF log_msg LIKE '%error%' THEN
              SET error_count = error_count + 1;
          END IF;
      END LOOP;
      CLOSE log_cursor;

      SELECT error_count AS error_logs;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE FlagHighScores()
  BEGIN
      DECLARE done INT DEFAULT FALSE;
      DECLARE pred_id INT;
      DECLARE score_val FLOAT;
      DECLARE pred_cursor CURSOR FOR
          SELECT prediction_id, score FROM predictions;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = TRUE;

      OPEN pred_cursor;
      read_loop: LOOP
          FETCH pred_cursor INTO pred_id, score_val;
          IF done THEN
              LEAVE read_loop;
          END IF;
          IF score_val > 0.9 THEN
              INSERT INTO prediction_flags (flag_id, prediction_id, flag_reason)
              VALUES ((SELECT COALESCE(MAX(flag_id), 0) + 1 FROM prediction_flags), pred_id, 'High score');
          END IF;
      END LOOP;
      CLOSE pred_cursor;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CALL CountErrorLogs();
  CALL FlagHighScores();
  SELECT * FROM prediction_flags;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Declaring Cursors` and `Fetching Data`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run cursor procedures in a local database (MySQL, PostgreSQL) to verify outputs.
- **Combine Skills**: Mix cursors with triggers, procedures, and joins (from `06 Joins and Aggregations`, `07 Stored Procedures`, `08 Triggers`) for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore nested cursors or error handling for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for cursors? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses cursors on these tables, testing all four concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Model training logs for cursor-based processing.
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
- **Notes**: Supports cursor iteration for log analysis.

### Dataset 2: training_data
- **Used In**: Project 2
- **Description**: ML training data for cursor-based stats.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO training_data (id, feature1, feature2) VALUES
  (1, 0.5, 1.8),
  (2, 1.2, 2.5),
  (3, 2.3, 3.1),
  (4, 0.8, 1.4),
  (5, 1.9, 2.9),
  (6, 0.3, 1.7),
  (7, 2.1, 3.4),
  (8, 1.0, 2.0),
  (9, 1.6, 2.6),
  (10, 0.7, 1.9),
  (11, 2.4, 3.2),
  (12, 0.9, 1.5),
  (13, 1.8, 2.8),
  (14, 0.4, 1.3),
  (15, 2.0, 3.0),
  (16, 0.8, 1.7),
  (17, 1.7, 2.7),
  (18, 0.6, 1.6),
  (19, 2.2, 3.3),
  (20, 0.5, 1.9);
  ```
- **Notes**: Supports cursor iteration for feature calculations.

### Dataset 3: predictions
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: ML predictions for cursor-based validation.
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
- **Notes**: Supports cursor iteration for score flagging.

### Dataset 4: prediction_flags
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Flags for predictions processed by cursors.
- **Schema**:
  ```sql
  CREATE TABLE prediction_flags (
      flag_id INT PRIMARY KEY,
      prediction_id INT,
      flag_reason VARCHAR(100)
  );
  ```
- **Sample Data**: Initially empty; populated by cursors.
- **Notes**: Captures flags for low or high scores.

### Dataset 5: orders
- **Used In**: Project 4
- **Description**: Orders for fraud reporting with cursors.
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
- **Notes**: Supports cursor-based fraud reporting.

### Dataset 6: fraud_flags
- **Used In**: Project 4
- **Description**: Fraud flags for joining in cursor reports.
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
- **Notes**: Joined with `orders` for cursor-based reporting.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Cursor Logic**: Use project tasks to create and call cursor-based procedures.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify outputs.
4. **Compatibility**:
   - MySQL: Supports cursors within stored procedures. Use `DELIMITER` and `DECLARE CONTINUE HANDLER` for control flow.
   - PostgreSQL: Supports cursors with `DECLARE CURSOR` and `FETCH`. Adjust syntax for `PERFORM` in procedures.
   - SQL Server: Supports cursors with `DECLARE CURSOR` and `FETCH NEXT`. Use `DEALLOCATE` for closing.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master SQL Cursors and shine in AI/ML interviews! Happy querying! ✨</p>
</div>