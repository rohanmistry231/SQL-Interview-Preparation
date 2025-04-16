# 🎯 Interview Questions - UPDATE to Ace SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master UPDATE operations and dominate SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** hub for **UPDATE**! 💻 This README is your go-to resource, packed with tricky, real-world questions covering **three core concepts**: `Single Column Update`, `Multiple Column Update`, and `Update with Conditions`. Crafted to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With datasets and solutions (tucked away in `<details>` tags), you’ll hone your data updating skills, boost your confidence, and make your portfolio stand out for recruiters. Let’s tweak those tables and crush those interviews!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master UPDATE**: Perfect your ability to modify data precisely and efficiently.
- **Power AI/ML Workflows**: Update model outputs, correct datasets, and manage logs.
- **Shine Under Pressure**: Practice explaining update logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Dive In**:
   - Pick a concept section (e.g., `Single Column Update`).
   - Read the question and try writing the UPDATE query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it against the datasets to verify results.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Single Column Update` for quick wins, then tackle `Update with Conditions` for complex filtering challenges. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, datasets, and solutions. Get ready to update like a pro!

### 1. Single Column Update
- **Description**: `UPDATE` modifies a single column for specified rows.
- **Interview Focus**: Tests precision in targeting columns and rows without side effects.

#### Question 1.1: Correct Prediction Score
- **Problem**: An ML model’s score was miscalculated. Write a query to update the `score` column in `predictions` to 0.99 for `prediction_id = 7`.
- **Trick**: Tests if you target a specific row and column without affecting others.
- **AI/ML Use Case**: Corrects a single prediction for model validation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  UPDATE predictions
  SET score = 0.99
  WHERE prediction_id = 7;
  ```
  </details>

#### Question 1.2: Update Log Message
- **Problem**: A training log needs clarification. Write a query to update the `log_message` column in `model_logs` to 'Training failed - retry scheduled' for `log_id = 9`.
- **Trick**: Ensures you handle string updates and primary key targeting correctly.
- **AI/ML Use Case**: Updates a log entry for pipeline debugging.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  UPDATE model_logs
  SET log_message = 'Training failed - retry scheduled'
  WHERE log_id = 9;
  ```
  </details>

---

### 2. Multiple Column Update
- **Description**: `UPDATE` modifies multiple columns in a single query.
- **Interview Focus**: Tests column coordination and data consistency.

#### Question 2.1: Adjust Prediction Details
- **Problem**: A model’s prediction needs multiple fixes. Write a query to update `predictions` for `prediction_id = 16`, setting `score = 0.98` and `eval_date = '2025-09-01'`.
- **Trick**: Tests if you update multiple columns accurately in one query.
- **AI/ML Use Case**: Corrects prediction metadata for reporting.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  UPDATE predictions
  SET score = 0.98, eval_date = '2025-09-01'
  WHERE prediction_id = 16;
  ```
  </details>

#### Question 2.2: Revise Order Record
- **Problem**: A transaction was recorded incorrectly. Write a query to update `orders` for `order_id = 106`, setting `amount = 400.0` and `order_date = '2025-08-21'`.
- **Trick**: Checks if you maintain data type consistency across columns.
- **AI/ML Use Case**: Fixes transaction data for fraud model training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  UPDATE orders
  SET amount = 400.0, order_date = '2025-08-21'
  WHERE order_id = 106;
  ```
  </details>

---

### 3. Update with Conditions
- **Description**: `UPDATE` modifies rows based on complex conditions, often with `WHERE` clauses or subqueries.
- **Interview Focus**: Tests conditional logic and safe updates.

#### Question 3.1: Flag Low Scores
- **Problem**: You’re auditing ML model performance. Write a query to update `predictions`, setting `score = 0.75` for all rows where `score` is less than 0.8 and `model_id = 102`.
- **Trick**: Tests combining multiple conditions to avoid over-updating.
- **AI/ML Use Case**: Standardizes low-confidence scores for a specific model.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  UPDATE predictions
  SET score = 0.75
  WHERE score < 0.8 AND model_id = 102;
  ```
  </details>

#### Question 3.2: Update Flagged Orders
- **Problem**: For fraud analysis, mark high-value orders. Write a query to update `orders`, setting `amount = amount * 1.1` for orders where `order_id` is in `fraud_flags` with `flag_reason = 'High amount'`.
- **Trick**: Tests subquery integration in `UPDATE` for conditional filtering.
- **AI/ML Use Case**: Adjusts flagged transactions for fraud model recalibration.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  UPDATE orders
  SET amount = amount * 1.1
  WHERE order_id IN (
      SELECT order_id
      FROM fraud_flags
      WHERE flag_reason = 'High amount'
  );
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Begin with `Single Column Update` to nail basic syntax.
- **Watch for Traps**: Interviewers test over-updating in `Update with Conditions` and column mismatches in multi-column updates.
- **Explain Clearly**: Practice breaking down update logic and conditions for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the datasets below.
- **Optimize Queries**: Use precise `WHERE` clauses to avoid unnecessary updates.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Dataset & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these datasets to test UPDATE concepts. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Dataset 1: predictions
- **Used In**: Single Column Update, Multiple Column Update, Update with Conditions
- **Description**: ML model predictions for score and metadata updates.
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

### Dataset 2: orders
- **Used In**: Multiple Column Update, Update with Conditions
- **Description**: Transaction data for amount and date corrections.
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

### Dataset 3: model_logs
- **Used In**: Single Column Update
- **Description**: Model training logs for message updates.
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

### Dataset 4: fraud_flags
- **Used In**: Update with Conditions
- **Description**: Fraud flags for transaction adjustments.
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

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run solutions.
3. **Compatibility**:
   - MySQL/PostgreSQL: Supports all `UPDATE` syntax.
   - SQL Server: Identical syntax; ensure date formats match (e.g., `YYYY-MM-DD`).
4. **Expand Data**: For up to 100 rows, repeat patterns or check `Datasets/` for full files (coming soon).

---

<div align="center">
  <p>Smash these UPDATE questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>