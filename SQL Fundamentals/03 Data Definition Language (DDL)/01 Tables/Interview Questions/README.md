# 🎯 Interview Questions - Tables to Dominate SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Table operations and crush SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** arena for **Tables**! 💻 This README is your secret weapon, packed with tricky, real-world questions covering **four core concepts**: `Create Table`, `Alter Table`, `Drop Table`, and `Truncate Table`. Crafted to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas and solutions (tucked away in `<details>` tags), you’ll hone your table management skills, boost your confidence, and make your portfolio stand out for recruiters. Let’s build, tweak, and tear down those tables to ace those interviews!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Tables**: Perfect your ability to define, modify, and remove table structures.
- **Power AI/ML Workflows**: Set up schemas for datasets, adapt tables for new features, and clear data efficiently.
- **Shine Under Pressure**: Practice explaining DDL logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to understand table structures and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Create Table`).
   - Read the question and try writing the DDL query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify table creation, modification, or deletion.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Create Table` to build schema confidence, then tackle `Alter Table` or `Truncate Table` for trickier DDL challenges. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to shape tables like a pro!

### 1. Create Table
- **Description**: `CREATE TABLE` defines a new table with specified columns and data types.
- **Interview Focus**: Tests schema design and data type selection.

#### Question 1.1: Prediction Storage
- **Problem**: Your ML pipeline needs a table to store model predictions. Write a query to create a table named `model_predictions` with columns: `prediction_id` (integer, primary key), `model_id` (integer), `score` (float), and `prediction_date` (date).
- **Trick**: Tests if you define a primary key and choose appropriate data types.
- **AI/ML Use Case**: Sets up storage for model outputs.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE TABLE model_predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE
  );
  ```
  </details>

#### Question 1.2: Training Metadata
- **Problem**: You’re tracking ML training runs. Write a query to create a table named `training_runs` with columns: `run_id` (integer, primary key), `model_id` (integer), `start_time` (datetime), and `status` (varchar, max 50 characters).
- **Trick**: Ensures you handle string length and datetime types correctly.
- **AI/ML Use Case**: Stores metadata for training pipeline analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE TABLE training_runs (
      run_id INT PRIMARY KEY,
      model_id INT,
      start_time DATETIME,
      status VARCHAR(50)
  );
  ```
  </details>

---

### 2. Alter Table
- **Description**: `ALTER TABLE` modifies an existing table’s structure (e.g., adding/dropping columns).
- **Interview Focus**: Tests schema evolution and syntax accuracy.

#### Question 2.1: Add Feature Column
- **Problem**: Your ML dataset needs a new feature. Write a query to alter the `model_predictions` table to add a column `feature_version` (varchar, max 20 characters).
- **Trick**: Tests if you use `ADD` correctly without breaking the table.
- **AI/ML Use Case**: Adapts table for new feature tracking.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  ALTER TABLE model_predictions
  ADD feature_version VARCHAR(20);
  ```
  </details>

#### Question 2.2: Drop Obsolete Column
- **Problem**: An outdated column is cluttering your schema. Write a query to alter the `training_runs` table to drop the `status` column.
- **Trick**: Ensures you use `DROP COLUMN` safely, considering dependencies.
- **AI/ML Use Case**: Removes unused metadata to streamline analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  ALTER TABLE training_runs
  DROP COLUMN status;
  ```
  </details>

---

### 3. Drop Table
- **Description**: `DROP TABLE` removes a table and its data permanently.
- **Interview Focus**: Tests caution with destructive operations and syntax.

#### Question 3.1: Remove Old Predictions
- **Problem**: An obsolete prediction table is no longer needed. Write a query to drop the `model_predictions` table.
- **Trick**: Tests if you understand the permanent nature of `DROP` and use it confidently.
- **AI/ML Use Case**: Clears outdated dataset storage.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP TABLE model_predictions;
  ```
  </details>

#### Question 3.2: Eliminate Temporary Logs
- **Problem**: A temporary log table is clogging your database. Write a query to drop the `temp_logs` table.
- **Trick**: Ensures you specify the correct table without affecting others.
- **AI/ML Use Case**: Removes interim logging for pipeline cleanup.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP TABLE temp_logs;
  ```
  </details>

---

### 4. Truncate Table
- **Description**: `TRUNCATE TABLE` removes all rows but keeps the table structure, often faster than `DELETE`.
- **Interview Focus**: Tests understanding of `TRUNCATE` vs. `DELETE` and its no-rollback nature.

#### Question 4.1: Reset Training Runs
- **Problem**: Your ML pipeline needs to clear old training data. Write a query to truncate the `training_runs` table.
- **Trick**: Tests if you choose `TRUNCATE` over `DELETE` for efficiency and understand its implications.
- **AI/ML Use Case**: Resets training metadata for a new experiment.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  TRUNCATE TABLE training_runs;
  ```
  </details>

#### Question 4.2: Clear Error Logs
- **Problem**: Error logs from an ML run are no longer needed. Write a query to truncate the `error_logs` table.
- **Trick**: Ensures you apply `TRUNCATE` correctly, avoiding `DELETE` for speed.
- **AI/ML Use Case**: Clears error tracking for a fresh debugging cycle.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  TRUNCATE TABLE error_logs;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Simple**: Begin with `Create Table` to nail schema basics.
- **Watch for Traps**: Interviewers test data type choices in `Create Table`, dependency issues in `Alter Table`, and `TRUNCATE` vs. `DELETE` differences.
- **Explain Clearly**: Practice justifying schema changes or deletions for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Schemas**: Choose efficient data types and confirm operations before dropping tables.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, use the following table schemas in your database (MySQL, PostgreSQL, or SQL Server). Each question tests DDL operations, so you’ll create, alter, drop, or truncate these tables as needed. Below are schemas and sample setups—copy-paste to test queries or save as `.sql` files.

### Schema 1: model_predictions
- **Used In**: Create Table, Alter Table, Drop Table
- **Description**: Stores ML model predictions.
- **Schema**:
  ```sql
  CREATE TABLE model_predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE
  );
  ```

### Schema 2: training_runs
- **Used In**: Create Table, Alter Table, Truncate Table
- **Description**: Tracks ML training metadata.
- **Schema**:
  ```sql
  CREATE TABLE training_runs (
      run_id INT PRIMARY KEY,
      model_id INT,
      start_time DATETIME,
      status VARCHAR(50)
  );
  ```

### Schema 3: temp_logs
- **Used In**: Drop Table
- **Description**: Temporary logs for ML pipeline events.
- **Schema**:
  ```sql
  CREATE TABLE temp_logs (
      log_id INT PRIMARY KEY,
      event VARCHAR(100),
      event_time DATETIME
  );
  ```

### Schema 4: error_logs
- **Used In**: Truncate Table
- **Description**: Logs errors from ML runs.
- **Schema**:
  ```sql
  CREATE TABLE error_logs (
      log_id INT PRIMARY KEY,
      model_id INT,
      error_message VARCHAR(255),
      log_date DATETIME
  );
  ```

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` statements above for testing (e.g., for `Create Table` and `Alter Table` questions).
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run DDL operations.
3. **Compatibility**:
   - MySQL/PostgreSQL: Supports all DDL syntax.
   - SQL Server: Identical syntax; use `NVARCHAR` instead of `VARCHAR` if needed for Unicode.
4. **No Initial Data**: Most questions don’t require data, as they focus on structure. For `Truncate Table`, assume tables exist with rows to clear.
5. **Sample Data (Optional)**: If testing `TRUNCATE`, use prior tables like `predictions` (from **02 DML**):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, eval_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16');
  ```

---

<div align="center">
  <p>Smash these Table questions to rule SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>