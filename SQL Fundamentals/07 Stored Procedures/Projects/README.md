# 📊 Projects - Mastering SQL Stored Procedures

## 🌟 Overview

Welcome to the **Projects** section for **SQL Stored Procedures**! 🚀 These five unique projects are your playground to master four core concepts—`Creating Procedures`, `Parameters`, `Calling Procedures`, and `Dropping Procedures`. Dive into AI/ML-themed challenges like automating model performance reports or parameterizing fraud queries, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL stored procedures practical and fun, helping you:
- **Apply Skills**: Automate ML data pipelines with reusable procedures.
- **Ace Interviews**: Solve data processing problems like those in real-world ML workflows.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Streamline model analysis, fraud detection, or dataset prep with procedures.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key stored procedure techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Reporting** | Creating Procedures, Calling Procedures | Automate model log summaries. |
| **Dataset Analysis** | Parameters, Calling Procedures | Parameterize dataset stats. |
| **Prediction Processor** | Creating Procedures, Parameters | Process predictions dynamically. |
| **Fraud Automation** | Dropping Procedures, Creating Procedures | Manage fraud detection procedures. |
| **Capstone: Procedures** | All Four | Build a full ML pipeline with procedures. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Reporting/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL stored procedures to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify procedure outputs.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Creating Procedures` and `Calling Procedures`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Reporting
- **Folder**: `Project1_Model_Reporting/`
- **Concepts**: `Creating Procedures`, `Calling Procedures`
- **Description**: Automate summaries of model logs for training insights.
- **Tasks**:
  - Create a stored procedure to count logs per `model_id` in `model_logs`.
  - Call the procedure to display the results.
  - Create a procedure to list logs with 'started' messages and call it.
- **AI/ML Use Case**: Automates model training log analysis for pipeline monitoring.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE CountLogsPerModel()
  BEGIN
      SELECT model_id, COUNT(*) AS log_count
      FROM model_logs
      GROUP BY model_id;
  END //
  DELIMITER ;

  CALL CountLogsPerModel();
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL CountLogsPerModel();
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE ListStartLogs()
  BEGIN
      SELECT log_id, model_id, log_message
      FROM model_logs
      WHERE log_message LIKE '%started%';
  END //
  DELIMITER ;

  CALL ListStartLogs();
  ```
  </details>

### Project 2: Dataset Analysis
- **Folder**: `Project2_Dataset_Analysis/`
- **Concepts**: `Parameters`, `Calling Procedures`
- **Description**: Parameterize dataset statistics for flexible analysis.
- **Tasks**:
  - Create a procedure with a parameter to average `feature1` in `training_data` for a given `feature2` threshold.
  - Call the procedure with `feature2 > 2.0`.
  - Call the procedure with `feature2 > 1.5`.
- **AI/ML Use Case**: Enables dynamic dataset exploration for preprocessing.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE AvgFeatureByThreshold(IN feature2_threshold FLOAT)
  BEGIN
      SELECT AVG(feature1) AS avg_feature1
      FROM training_data
      WHERE feature2 > feature2_threshold;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL AvgFeatureByThreshold(2.0);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CALL AvgFeatureByThreshold(1.5);
  ```
  </details>

### Project 3: Prediction Processor
- **Folder**: `Project3_Prediction_Processor/`
- **Concepts**: `Creating Procedures`, `Parameters`
- **Description**: Process predictions dynamically with parameterized procedures.
- **Tasks**:
  - Create a procedure with a parameter to find the max `score` in `predictions` for a given `model_id`.
  - Call the procedure for `model_id = 101`.
  - Create a procedure to count predictions above a score threshold and call it with threshold 0.9.
- **AI/ML Use Case**: Automates model performance evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE MaxScoreByModel(IN input_model_id INT)
  BEGIN
      SELECT MAX(score) AS max_score
      FROM predictions
      WHERE model_id = input_model_id;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL MaxScoreByModel(101);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE CountHighScores(IN score_threshold FLOAT)
  BEGIN
      SELECT COUNT(*) AS high_score_count
      FROM predictions
      WHERE score > score_threshold;
  END //
  DELIMITER ;

  CALL CountHighScores(0.9);
  ```
  </details>

### Project 4: Fraud Automation
- **Folder**: `Project4_Fraud_Automation/`
- **Concepts**: `Dropping Procedures`, `Creating Procedures`
- **Description**: Manage fraud detection procedures, including cleanup.
- **Tasks**:
  - Create a procedure to calculate average `amount` for flagged orders in `orders` joined with `fraud_flags`.
  - Drop an outdated procedure named `OldFraudCheck`.
  - Call the new procedure to verify results.
- **AI/ML Use Case**: Streamlines fraud analysis with maintainable procedures.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE AvgFlaggedAmount()
  BEGIN
      SELECT AVG(o.amount) AS avg_flagged_amount
      FROM orders o
      INNER JOIN fraud_flags ff ON o.order_id = ff.order_id;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DROP PROCEDURE IF EXISTS OldFraudCheck;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CALL AvgFlaggedAmount();
  ```
  </details>

### Project 5: Capstone - Procedures
- **Folder**: `Project5_Capstone_Procedures/`
- **Concepts**: All Four (`Creating Procedures`, `Parameters`, `Calling Procedures`, `Dropping Procedures`)
- **Description**: Build a full ML pipeline with stored procedures for data processing.
- **Tasks**:
  - Create a procedure to count logs in `model_logs` for a given `model_id` parameter.
  - Call the procedure for `model_id = 102`.
  - Create a procedure to average `amount` in `orders` and drop an outdated procedure `OldOrderSummary`.
  - Call the new orders procedure.
- **AI/ML Use Case**: Automates data prep and analysis for a fraud detection pipeline.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE CountLogsByModel(IN input_model_id INT)
  BEGIN
      SELECT COUNT(*) AS log_count
      FROM model_logs
      WHERE model_id = input_model_id;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CALL CountLogsByModel(102);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DELIMITER //
  CREATE PROCEDURE AvgOrderAmount()
  BEGIN
      SELECT AVG(amount) AS avg_amount
      FROM orders;
  END //
  DELIMITER ;

  DROP PROCEDURE IF EXISTS OldOrderSummary;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  CALL AvgOrderAmount();
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Creating Procedures` and `Calling Procedures`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run procedures in a local database (MySQL, PostgreSQL) to verify outputs.
- **Combine Skills**: Mix procedures with joins, aggregations, and set operations (from `06 Joins and Aggregations`) for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore complex parameterized procedures or error handling for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for stored procedures? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses stored procedures on these tables, testing all four concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Model training logs for procedure-based summaries.
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
- **Notes**: Supports procedures for log counting and filtering.

### Dataset 2: training_data
- **Used In**: Project 2
- **Description**: ML training data for parameterized analysis.
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
- **Notes**: Supports parameterized procedures for feature stats.

### Dataset 3: predictions
- **Used In**: Project 3
- **Description**: ML model predictions for dynamic processing.
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
- **Notes**: Supports procedures for score analysis.

### Dataset 4: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for fraud-related procedures.
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
- **Notes**: Supports procedures for order analysis.

### Dataset 5: fraud_flags
- **Used In**: Project 4
- **Description**: Fraud flags for joining in fraud procedures.
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
- **Notes**: Supports procedures for fraud analysis.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Procedures**: Use project tasks to create, call, and drop procedures.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify outputs.
4. **Compatibility**:
   - MySQL: Supports stored procedures with `DELIMITER` for creation. Use `DROP PROCEDURE IF EXISTS` for safety.
   - PostgreSQL: Supports stored procedures (use `CREATE OR REPLACE PROCEDURE` for updates). Adjust `DELIMITER` syntax as needed.
   - SQL Server: Supports stored procedures with `CREATE PROCEDURE` and `DROP PROCEDURE`.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master SQL Stored Procedures and shine in AI/ML interviews! Happy querying! ✨</p>
</div>