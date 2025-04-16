# 🎯 Interview Questions - SELECT Operations to Crush SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Gear up to dominate SQL interviews with tricky SELECT Operations questions—the heart of DQL for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** arena for **SELECT Operations**! 💻 This README is your ultimate prep tool, packed with real-world, tricky interview questions covering **nine core concepts**: `Select Statement`, `Distinct`, `Where Clause`, `Like Operator`, `Wildcard Operator`, `In Operator`, `Between Operator`, `Is Null`, and `And, Or, Not`. Each section below dives into one concept with 1-2 challenging, ML-themed questions that mirror what you’ll face in coding tests and technical rounds at top companies. With datasets and solutions (hidden in `<details>` tags), you’ll sharpen your skills, build confidence, and make your portfolio shine for recruiters. Let’s get you interview-ready!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused roles.
- **Test SELECT Mastery**: Cover every angle of SELECT Operations, from basic retrieval to complex filtering.
- **Boost AI/ML Skills**: Apply SQL to dataset prep, fraud detection, and model analysis.
- **Prep for Pressure**: Practice explaining logic under interview scrutiny.
- **Enhance Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Dive In**:
   - Pick a concept section (e.g., `Select Statement`).
   - Read the question and try solving it in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it against the datasets to verify results.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Select Statement` for foundational wins, then tackle `Like Operator` or `And, Or, Not` for trickier challenges. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, datasets, and solutions. Get ready to think like a pro!

### 1. Select Statement
- **Description**: The `SELECT` statement retrieves data from tables, forming the backbone of SQL queries.
- **Interview Focus**: Expect questions testing column selection, aliasing, and basic query structure.

#### Question 1.1: Model Data Extraction
- **Problem**: You’re building an ML pipeline and need to extract specific columns from model predictions. Write a query to select `prediction_id`, `score` as `confidence_score`, and `eval_date` from `predictions` for all records.
- **AI/ML Use Case**: Prepares prediction data for model evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score AS confidence_score, eval_date
  FROM predictions;
  ```
  </details>

#### Question 1.2: Feature Selection
- **Problem**: For an ML dataset, you need to retrieve all columns except `id` from `training_data`. Write a query to select `feature1`, `feature2` explicitly, ensuring no other columns are included.
- **Trick**: Tests if you avoid using `SELECT *` in production-like scenarios.
- **AI/ML Use Case**: Selects relevant features for model training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT feature1, feature2
  FROM training_data;
  ```
  </details>

---

### 2. Distinct
- **Description**: `DISTINCT` removes duplicate rows from query results.
- **Interview Focus**: Questions often test deduplication logic and edge cases.

#### Question 2.1: Unique Models
- **Problem**: Your ML team needs to know which models generated predictions. Write a query to select unique `model_id` values from `predictions`.
- **Trick**: Ensures you don’t overcomplicate with unnecessary clauses.
- **AI/ML Use Case**: Identifies distinct models for performance analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT DISTINCT model_id
  FROM predictions;
  ```
  </details>

#### Question 2.2: Unique Fraud Reasons
- **Problem**: To train a fraud detection model, you need unique fraud reasons. Write a query to select distinct `flag_reason` from `fraud_flags`, excluding duplicates.
- **Trick**: Tests if you handle text deduplication correctly.
- **AI/ML Use Case**: Categorizes fraud signals for feature engineering.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT DISTINCT flag_reason
  FROM fraud_flags;
  ```
  </details>

---

### 3. Where Clause
- **Description**: `WHERE` filters rows based on conditions.
- **Interview Focus**: Tests precise condition crafting and optimization.

#### Question 3.1: High-Value Orders
- **Problem**: For a fraud model, filter high-value transactions. Write a query to select `order_id`, `amount` from `orders` where `amount` is greater than 150.
- **Trick**: Checks if you avoid including unnecessary rows.
- **AI/ML Use Case**: Targets outliers for fraud analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount
  FROM orders
  WHERE amount > 150;
  ```
  </details>

#### Question 3.2: Recent Predictions
- **Problem**: You need recent ML predictions for validation. Write a query to select `prediction_id`, `score` from `predictions` where `eval_date` is after August 25, 2025.
- **Trick**: Tests date filtering accuracy.
- **AI/ML Use Case**: Focuses on fresh data for model testing.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE eval_date > '2025-08-25';
  ```
  </details>

---

### 4. Like Operator
- **Description**: `LIKE` matches patterns in text data.
- **Interview Focus**: Questions test pattern-matching precision and case sensitivity.

#### Question 4.1: Error Logs
- **Problem**: Your ML pipeline logs errors. Write a query to select `log_id`, `log_message` from `model_logs` where `log_message` contains the word 'error' (case-insensitive).
- **Trick**: Tests if you handle case sensitivity or wildcards correctly.
- **AI/ML Use Case**: Identifies model training issues for debugging.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT log_id, log_message
  FROM model_logs
  WHERE log_message LIKE '%error%';
  ```
  </details>

#### Question 4.2: Suspicious Flags
- **Problem**: For fraud analysis, find specific fraud signals. Write a query to select `order_id`, `flag_reason` from `fraud_flags` where `flag_reason` starts with 'Suspicious'.
- **Trick**: Ensures proper wildcard placement for prefix matching.
- **AI/ML Use Case**: Filters fraud labels for model training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, flag_reason
  FROM fraud_flags
  WHERE flag_reason LIKE 'Suspicious%';
  ```
  </details>

---

### 5. Wildcard Operator
- **Description**: Wildcards (`%`, `_`) enhance `LIKE` for flexible pattern matching.
- **Interview Focus**: Tests nuanced wildcard usage in complex patterns.

#### Question 5.1: Patterned Logs
- **Problem**: You’re analyzing model logs for specific events. Write a query to select `log_id`, `log_message` from `model_logs` where `log_message` matches 'Training _ompleted' (one character missing).
- **Trick**: Tests single-character wildcard (`_`) knowledge.
- **AI/ML Use Case**: Pinpoints log patterns for pipeline monitoring.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT log_id, log_message
  FROM model_logs
  WHERE log_message LIKE 'Training _ompleted';
  ```
  </details>

#### Question 5.2: Fraud Reason Patterns
- **Problem**: Identify fraud flags with variable text. Write a query to select `flag_id`, `flag_reason` from `fraud_flags` where `flag_reason` matches any text ending with 'amount'.
- **Trick**: Tests if you use `%` correctly for suffix matching.
- **AI/ML Use Case**: Groups fraud signals for feature extraction.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT flag_id, flag_reason
  FROM fraud_flags
  WHERE flag_reason LIKE '%amount';
  ```
  </details>

---

### 6. In Operator
- **Description**: `IN` checks if a value matches any in a list.
- **Interview Focus**: Tests efficient filtering with multiple values.

#### Question 6.1: Selected Models
- **Problem**: Your ML team focuses on specific models. Write a query to select `prediction_id`, `model_id` from `predictions` where `model_id` is one of 101, 103, or 105.
- **Trick**: Checks if you use `IN` instead of multiple `OR` conditions.
- **AI/ML Use Case**: Filters predictions for targeted model analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, model_id
  FROM predictions
  WHERE model_id IN (101, 103, 105);
  ```
  </details>

#### Question 6.2: Customer Focus
- **Problem**: For fraud detection, focus on key customers. Write a query to select `order_id`, `customer_id` from `orders` where `customer_id` is in (301, 302, 303).
- **Trick**: Tests if you avoid redundant conditions.
- **AI/ML Use Case**: Narrows down transactions for fraud modeling.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, customer_id
  FROM orders
  WHERE customer_id IN (301, 302, 303);
  ```
  </details>

---

### 7. Between Operator
- **Description**: `BETWEEN` selects values within a range (inclusive).
- **Interview Focus**: Tests range filtering and edge case handling.

#### Question 7.1: Score Range
- **Problem**: You’re validating ML predictions. Write a query to select `prediction_id`, `score` from `predictions` where `score` is between 0.8 and 0.95 (inclusive).
- **Trick**: Tests if you understand `BETWEEN` inclusivity.
- **AI/ML Use Case**: Filters predictions for performance evaluation.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE score BETWEEN 0.8 AND 0.95;
  ```
  </details>

#### Question 7.2: Amount Range
- **Problem**: For fraud analysis, find mid-range transactions. Write a query to select `order_id`, `amount` from `orders` where `amount` is between 100 and 200.
- **Trick**: Ensures you don’t confuse `BETWEEN` with exclusive ranges.
- **AI/ML Use Case**: Targets transactions for fraud pattern analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount
  FROM orders
  WHERE amount BETWEEN 100 AND 200;
  ```
  </details>

---

### 8. Is Null
- **Description**: `IS NULL` checks for missing values.
- **Interview Focus**: Tests handling of incomplete data.

#### Question 8.1: Missing Scores
- **Problem**: Some ML predictions lack scores. Write a query to select `prediction_id`, `model_id` from `predictions` where `score` is null.
- **Trick**: Tests if you use `IS NULL` instead of `= NULL`.
- **AI/ML Use Case**: Identifies incomplete data for pipeline cleanup.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, model_id
  FROM predictions
  WHERE score IS NULL;
  ```
  </details>

#### Question 8.2: Non-Missing Dates
- **Problem**: Ensure ML predictions have valid dates. Write a query to select `prediction_id`, `eval_date` from `predictions` where `eval_date` is not null.
- **Trick**: Tests `IS NOT NULL` usage under pressure.
- **AI/ML Use Case**: Ensures reliable data for time-based analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, eval_date
  FROM predictions
  WHERE eval_date IS NOT NULL;
  ```
  </details>

---

### 9. And, Or, Not
- **Description**: Logical operators (`AND`, `OR`, `NOT`) combine conditions.
- **Interview Focus**: Tests complex condition logic and precedence.

#### Question 9.1: Complex Fraud Filter
- **Problem**: For a fraud model, filter suspicious orders. Write a query to select `order_id`, `amount` from `orders` where `amount > 200` and `customer_id` is not 301, or `order_date` is after August 30, 2025.
- **Trick**: Tests operator precedence and grouping clarity.
- **AI/ML Use Case**: Builds a fraud detection dataset with nuanced filters.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT order_id, amount
  FROM orders
  WHERE (amount > 200 AND customer_id != 301)
     OR order_date > '2025-08-30';
  ```
  </details>

#### Question 9.2: Prediction Logic
- **Problem**: Validate ML predictions with strict criteria. Write a query to select `prediction_id`, `score` from `predictions` where `score > 0.9` and `model_id` is not in (101, 102), or `eval_date` is August 31, 2025.
- **Trick**: Tests combining `NOT` with `IN` and multiple conditions.
- **AI/ML Use Case**: Filters high-confidence predictions for review.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE (score > 0.9 AND model_id NOT IN (101, 102))
     OR eval_date = '2025-08-31';
  ```
  </details>

---

## 💡 Tips for Success

- **Start with Basics**: Nail `Select Statement` and `Where Clause` questions first.
- **Watch for Tricks**: Interviewers love edge cases (e.g., `IS NULL` vs. `= NULL`, `LIKE` case sensitivity).
- **Explain Clearly**: Practice verbalizing your query logic for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQLite with the datasets below.
- **Optimize Queries**: Write clean, efficient SQL to stand out.
- **Portfolio Power**: Save solutions to your GitHub to impress recruiters.

---

## 📂 Dataset & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or similar). Each question uses these datasets to test SELECT concepts. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Dataset 1: training_data
- **Used In**: Select Statement, Where Clause
- **Description**: ML training data for filtering.
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

### Dataset 2: predictions
- **Used In**: Select Statement, Distinct, Where Clause, Between Operator, Is Null, And, Or, Not
- **Description**: ML model predictions for analysis.
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

### Dataset 3: orders
- **Used In**: Where Clause, Between Operator, In Operator, And, Or, Not
- **Description**: Transaction data for fraud analysis.
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

### Dataset 4: fraud_flags
- **Used In**: Distinct, Like Operator, Wildcard Operator
- **Description**: Fraud flags for transaction analysis.
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

### Dataset 5: model_logs
- **Used In**: Like Operator, Wildcard Operator
- **Description**: Model training logs for debugging.
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

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin) to run your solutions.
3. **Compatibility**:
   - MySQL/PostgreSQL: Supports all syntax (`LIKE`, `BETWEEN`, `IN`).
   - SQL Server: Use `!=` instead of `<>` for `NOT`, and ensure date formats match.
4. **Expand Data**: For up to 100 rows, repeat patterns or check `Datasets/` for full files (coming soon).

---

<div align="center">
  <p>Smash these questions to conquer SQL interviews and power your AI/ML journey! Happy querying! ✨</p>
</div>