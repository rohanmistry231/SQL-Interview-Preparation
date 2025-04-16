# 📊 Projects - Mastering SQL Triggers

## 🌟 Overview

Welcome to the **Projects** section for **SQL Triggers**! 🚀 These five unique projects are your playground to master four core concepts—`Creating Triggers`, `BEFORE Triggers`, `AFTER Triggers`, and `Dropping Triggers`. Dive into AI/ML-themed challenges like logging model updates automatically or validating fraud data on the fly, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL triggers practical and fun, helping you:
- **Apply Skills**: Automate ML data validation and auditing with triggers.
- **Ace Interviews**: Solve real-time data integrity problems like those in ML pipelines.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Ensure data consistency for model training, fraud detection, or predictions.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key trigger techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Audit** | Creating Triggers, AFTER Triggers | Log model updates automatically. |
| **Dataset Validation** | Creating Triggers, BEFORE Triggers | Validate dataset inputs before insertion. |
| **Prediction Logging** | AFTER Triggers, Creating Triggers | Track prediction changes with audit logs. |
| **Fraud Monitor** | Dropping Triggers, Creating Triggers | Manage fraud detection triggers. |
| **Capstone: Triggers** | All Four | Build a full ML pipeline with triggers. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Audit/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL triggers to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify trigger behavior.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Creating Triggers` and `AFTER Triggers`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Audit
- **Folder**: `Project1_Model_Audit/`
- **Concepts**: `Creating Triggers`, `AFTER Triggers`
- **Description**: Automatically log changes to model logs for auditing.
- **Tasks**:
  - Create an `AFTER INSERT` trigger to log new `model_logs` entries into `model_logs_audit`.
  - Create an `AFTER UPDATE` trigger to record updates to `model_logs` in `model_logs_audit`.
  - Insert a new log and update an existing log to test the triggers.
- **AI/ML Use Case**: Ensures traceability of model training events.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER AfterInsertModelLog
  AFTER INSERT ON model_logs
  FOR EACH ROW
  BEGIN
      INSERT INTO model_logs_audit (log_id, model_id, log_message, action, action_date)
      VALUES (NEW.log_id, NEW.model_id, NEW.log_message, 'INSERT', NOW());
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER AfterUpdateModelLog
  AFTER UPDATE ON model_logs
  FOR EACH ROW
  BEGIN
      INSERT INTO model_logs_audit (log_id, model_id, log_message, action, action_date)
      VALUES (NEW.log_id, NEW.model_id, NEW.log_message, 'UPDATE', NOW());
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO model_logs (log_id, model_id, log_message, log_date)
  VALUES (21, 111, 'Training started', '2025-08-25 09:00:00');

  UPDATE model_logs
  SET log_message = 'Training completed'
  WHERE log_id = 21;
  ```
  </details>

### Project 2: Dataset Validation
- **Folder**: `Project2_Dataset_Validation/`
- **Concepts**: `Creating Triggers`, `BEFORE Triggers`
- **Description**: Validate training data inputs before insertion to ensure quality.
- **Tasks**:
  - Create a `BEFORE INSERT` trigger to prevent negative `feature1` values in `training_data`.
  - Create a `BEFORE UPDATE` trigger to ensure `feature2` stays positive in `training_data`.
  - Test by attempting to insert and update invalid data.
- **AI/ML Use Case**: Maintains dataset integrity for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER BeforeInsertTrainingData
  BEFORE INSERT ON training_data
  FOR EACH ROW
  BEGIN
      IF NEW.feature1 < 0 THEN
          SIGNAL SQLSTATE '45000'
          SET MESSAGE_TEXT = 'Feature1 cannot be negative';
      END IF;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER BeforeUpdateTrainingData
  BEFORE UPDATE ON training_data
  FOR EACH ROW
  BEGIN
      IF NEW.feature2 <= 0 THEN
          SIGNAL SQLSTATE '45000'
          SET MESSAGE_TEXT = 'Feature2 must be positive';
      END IF;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  -- Should fail due to negative feature1
  INSERT INTO training_data (id, feature1, feature2)
  VALUES (21, -0.5, 1.8);

  -- Should fail due to non-positive feature2
  UPDATE training_data
  SET feature2 = 0
  WHERE id = 1;
  ```
  </details>

### Project 3: Prediction Logging
- **Folder**: `Project3_Prediction_Logging/`
- **Concepts**: `AFTER Triggers`, `Creating Triggers`
- **Description**: Track changes to predictions with audit logs for transparency.
- **Tasks**:
  - Create an `AFTER INSERT` trigger to log new `predictions` into `predictions_audit`.
  - Create an `AFTER DELETE` trigger to record deleted `predictions` in `predictions_audit`.
  - Insert and delete a prediction to test the triggers.
- **AI/ML Use Case**: Audits model prediction changes for validation.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER AfterInsertPrediction
  AFTER INSERT ON predictions
  FOR EACH ROW
  BEGIN
      INSERT INTO predictions_audit (prediction_id, model_id, score, action, action_date)
      VALUES (NEW.prediction_id, NEW.model_id, NEW.score, 'INSERT', NOW());
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER AfterDeletePrediction
  AFTER DELETE ON predictions
  FOR EACH ROW
  BEGIN
      INSERT INTO predictions_audit (prediction_id, model_id, score, action, action_date)
      VALUES (OLD.prediction_id, OLD.model_id, OLD.score, 'DELETE', NOW());
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, eval_date)
  VALUES (21, 111, 0.85, '2025-09-04');

  DELETE FROM predictions
  WHERE prediction_id = 21;
  ```
  </details>

### Project 4: Fraud Monitor
- **Folder**: `Project4_Fraud_Monitor/`
- **Concepts**: `Dropping Triggers`, `Creating Triggers`
- **Description**: Manage fraud detection triggers, including cleanup of obsolete ones.
- **Tasks**:
  - Create an `AFTER INSERT` trigger to flag high-amount orders (>200) in `orders` by inserting into `fraud_flags`.
  - Drop an outdated trigger named `OldFraudMonitor`.
  - Insert a high-amount order to test the trigger.
- **AI/ML Use Case**: Automates fraud detection in transaction pipelines.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER AfterInsertOrder
  AFTER INSERT ON orders
  FOR EACH ROW
  BEGIN
      IF NEW.amount > 200 THEN
          INSERT INTO fraud_flags (flag_id, order_id, flag_reason)
          VALUES ((SELECT COALESCE(MAX(flag_id), 0) + 1 FROM fraud_flags), NEW.order_id, 'High amount');
      END IF;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DROP TRIGGER IF EXISTS OldFraudMonitor;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  INSERT INTO orders (order_id, customer_id, amount, order_date)
  VALUES (121, 311, 250.0, '2025-09-04');
  ```
  </details>

### Project 5: Capstone - Triggers
- **Folder**: `Project5_Capstone_Triggers/`
- **Concepts**: All Four (`Creating Triggers`, `BEFORE Triggers`, `AFTER Triggers`, `Dropping Triggers`)
- **Description**: Build a full ML pipeline with triggers for data integrity and auditing.
- **Tasks**:
  - Create a `BEFORE INSERT` trigger to validate `score` (>0) in `predictions`.
  - Create an `AFTER INSERT` trigger to log new `model_logs` into `model_logs_audit`.
  - Drop an outdated trigger named `OldModelTrigger`.
  - Test by inserting a prediction and a model log.
- **AI/ML Use Case**: Ensures data quality and auditability in an ML pipeline.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER BeforeInsertPrediction
  BEFORE INSERT ON predictions
  FOR EACH ROW
  BEGIN
      IF NEW.score <= 0 THEN
          SIGNAL SQLSTATE '45000'
          SET MESSAGE_TEXT = 'Score must be positive';
      END IF;
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  DELIMITER //
  CREATE TRIGGER AfterInsertModelLogCapstone
  AFTER INSERT ON model_logs
  FOR EACH ROW
  BEGIN
      INSERT INTO model_logs_audit (log_id, model_id, log_message, action, action_date)
      VALUES (NEW.log_id, NEW.model_id, NEW.log_message, 'INSERT', NOW());
  END //
  DELIMITER ;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  DROP TRIGGER IF EXISTS OldModelTrigger;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, eval_date)
  VALUES (22, 112, 0.90, '2025-09-05');

  INSERT INTO model_logs (log_id, model_id, log_message, log_date)
  VALUES (22, 112, 'Training started', '2025-09-05 10:00:00');
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Creating Triggers` and `AFTER Triggers`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run triggers in a local database (MySQL, PostgreSQL) to verify behavior.
- **Combine Skills**: Mix triggers with procedures, joins, and aggregations (from `06 Joins and Aggregations`, `07 Stored Procedures`) for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore complex trigger logic or cascading triggers for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for triggers? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses triggers on these tables, testing all four concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: model_logs
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Model training logs for audit triggers.
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
- **Notes**: Supports `AFTER` triggers for audit logging.

### Dataset 2: model_logs_audit
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: Audit table for tracking model log changes.
- **Schema**:
  ```sql
  CREATE TABLE model_logs_audit (
      audit_id INT PRIMARY KEY AUTO_INCREMENT,
      log_id INT,
      model_id INT,
      log_message VARCHAR(255),
      action VARCHAR(50),
      action_date DATETIME
  );
  ```
- **Sample Data**: Initially empty; populated by triggers.
- **Notes**: Captures `INSERT` and `UPDATE` actions from `model_logs`.

### Dataset 3: training_data
- **Used In**: Project 2
- **Description**: ML training data for validation triggers.
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
- **Notes**: Supports `BEFORE` triggers for data validation.

### Dataset 4: predictions
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: ML predictions for audit triggers.
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
- **Notes**: Supports `AFTER` triggers for prediction auditing.

### Dataset 5: predictions_audit
- **Used In**: Project 3
- **Description**: Audit table for tracking prediction changes.
- **Schema**:
  ```sql
  CREATE TABLE predictions_audit (
      audit_id INT PRIMARY KEY AUTO_INCREMENT,
      prediction_id INT,
      model_id INT,
      score FLOAT,
      action VARCHAR(50),
      action_date DATETIME
  );
  ```
- **Sample Data**: Initially empty; populated by triggers.
- **Notes**: Captures `INSERT` and `DELETE` actions from `predictions`.

### Dataset 6: orders
- **Used In**: Project 4
- **Description**: Orders for fraud detection triggers.
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
- **Notes**: Supports `AFTER` triggers for fraud flagging.

### Dataset 7: fraud_flags
- **Used In**: Project 4
- **Description**: Fraud flags populated by triggers.
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
- **Notes**: Populated by `AFTER INSERT` triggers for fraud detection.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Triggers**: Use project tasks to create, test, and drop triggers.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to verify trigger behavior.
4. **Compatibility**:
   - MySQL: Supports triggers with `DELIMITER`. Use `NEW`/`OLD` for row access and `SIGNAL` for errors.
   - PostgreSQL: Supports triggers with `CREATE TRIGGER`. Use `RAISE EXCEPTION` instead of `SIGNAL` for errors.
   - SQL Server: Supports triggers with `CREATE TRIGGER`. Use `RAISERROR` for error handling.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master SQL Triggers and shine in AI/ML interviews! Happy querying! ✨</p>
</div>