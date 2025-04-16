# 🎯 Interview Questions - Constraints to Nail SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Constraints and dominate SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** hub for **Constraints**! 💻 This README is your go-to resource, loaded with tricky, real-world questions covering **six core concepts**: `Primary Key`, `Foreign Key`, `Unique`, `Not Null`, `Check`, and `Default`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with a challenging, ML-themed question. With schemas and solutions (hidden in `<details>` tags), you’ll sharpen your data integrity skills, boost your confidence, and make your portfolio shine for recruiters. Let’s lock down those tables and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Constraints**: Perfect your ability to enforce data integrity and consistency.
- **Power AI/ML Workflows**: Ensure clean datasets, validate model outputs, and streamline pipelines.
- **Shine Under Pressure**: Practice explaining constraint logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to understand table structures and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Primary Key`).
   - Read the question and try writing the DDL query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify constraint creation or modification.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Primary Key` for foundational integrity, then tackle `Check` or `Foreign Key` for trickier constraints. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has a tricky question with an ML-relevant scenario, schema, and solution. Get ready to constrain like a pro!

### 1. Primary Key
- **Description**: `PRIMARY KEY` ensures unique, non-null identifiers for each row.
- **Interview Focus**: Tests key selection and uniqueness enforcement.

#### Question 1.1: Unique Model IDs
- **Problem**: Your ML pipeline needs a table for model metadata. Write a query to create a table named `models` with columns `model_id` (integer, primary key), `model_name` (varchar, max 100), and `created_date` (date).
- **Trick**: Tests if you define `PRIMARY KEY` correctly at creation.
- **AI/ML Use Case**: Ensures unique model identifiers for tracking.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE
  );
  ```
  </details>

---

### 2. Foreign Key
- **Description**: `FOREIGN KEY` enforces referential integrity between tables.
- **Interview Focus**: Tests relationships and dependency handling.

#### Question 2.1: Link Predictions to Models
- **Problem**: You’re storing ML predictions. Write a query to create a table named `predictions` with columns `prediction_id` (integer, primary key), `model_id` (integer, foreign key referencing `models(model_id)`), `score` (float), and `prediction_date` (date).
- **Trick**: Tests if you set up `FOREIGN KEY` with correct referencing.
- **AI/ML Use Case**: Links predictions to their generating models.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE,
      FOREIGN KEY (model_id) REFERENCES models(model_id)
  );
  ```
  </details>

---

### 3. Unique
- **Description**: `UNIQUE` ensures no duplicate values in a column or set of columns.
- **Interview Focus**: Tests non-key uniqueness enforcement.

#### Question 3.1: Unique Experiment Names
- **Problem**: Your ML team tracks experiments. Write a query to create a table named `experiments` with columns `experiment_id` (integer, primary key), `experiment_name` (varchar, max 50, unique), and `start_date` (date).
- **Trick**: Tests if you apply `UNIQUE` to a non-primary key column.
- **AI/ML Use Case**: Prevents duplicate experiment names in records.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE TABLE experiments (
      experiment_id INT PRIMARY KEY,
      experiment_name VARCHAR(50) UNIQUE,
      start_date DATE
  );
  ```
  </details>

---

### 4. Not Null
- **Description**: `NOT NULL` ensures a column cannot have null values.
- **Interview Focus**: Tests mandatory field enforcement.

#### Question 4.1: Mandatory Prediction Scores
- **Problem**: You need reliable prediction data. Write a query to alter the `predictions` table to add a `NOT NULL` constraint to the `score` column.
- **Trick**: Tests if you use `ALTER TABLE` to enforce `NOT NULL` correctly.
- **AI/ML Use Case**: Ensures all predictions have valid scores.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  ALTER TABLE predictions
  MODIFY score FLOAT NOT NULL;
  ```
  </details>

---

### 5. Check
- **Description**: `CHECK` enforces a condition on column values.
- **Interview Focus**: Tests custom validation logic.

#### Question 5.1: Valid Score Range
- **Problem**: Your ML predictions need validation. Write a query to create a table named `validated_predictions` with columns `prediction_id` (integer, primary key), `score` (float, must be between 0 and 1), and `prediction_date` (date).
- **Trick**: Tests if you implement `CHECK` for range validation.
- **AI/ML Use Case**: Ensures prediction scores are within a valid range.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE TABLE validated_predictions (
      prediction_id INT PRIMARY KEY,
      score FLOAT CHECK (score >= 0 AND score <= 1),
      prediction_date DATE
  );
  ```
  </details>

---

### 6. Default
- **Description**: `DEFAULT` sets a default value for a column when no value is specified.
- **Interview Focus**: Tests fallback value handling.

#### Question 6.1: Default Log Status
- **Problem**: Your ML pipeline logs events. Write a query to create a table named `event_logs` with columns `log_id` (integer, primary key), `event_type` (varchar, max 50), and `status` (varchar, max 20, default 'Pending').
- **Trick**: Tests if you apply `DEFAULT` correctly for new rows.
- **AI/ML Use Case**: Sets a default status for pipeline event tracking.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE TABLE event_logs (
      log_id INT PRIMARY KEY,
      event_type VARCHAR(50),
      status VARCHAR(20) DEFAULT 'Pending'
  );
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Begin with `Primary Key` to nail uniqueness basics.
- **Watch for Traps**: Interviewers test `FOREIGN KEY` dependencies, `CHECK` syntax, and `NOT NULL` retrofitting.
- **Explain Clearly**: Practice justifying constraint choices for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Constraints**: Ensure constraints don’t overcomplicate schemas (e.g., avoid redundant `UNIQUE`).
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, use the following table schemas in your database (MySQL, PostgreSQL, or SQL Server). Each question tests constraint operations, so you’ll create or modify these tables as needed. Below are schemas—copy-paste to test queries or save as `.sql` files.

### Schema 1: models
- **Used In**: Primary Key, Foreign Key
- **Description**: Stores ML model metadata.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE
  );
  ```

### Schema 2: predictions
- **Used In**: Foreign Key, Not Null
- **Description**: Stores ML predictions linked to models.
- **Schema** (Base for modification):
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE
  );
  ```

### Schema 3: experiments
- **Used In**: Unique
- **Description**: Tracks ML experiments.
- **Schema**:
  ```sql
  CREATE TABLE experiments (
      experiment_id INT PRIMARY KEY,
      experiment_name VARCHAR(50),
      start_date DATE
  );
  ```

### Schema 4: validated_predictions
- **Used In**: Check
- **Description**: Stores validated ML predictions.
- **Schema**:
  ```sql
  CREATE TABLE validated_predictions (
      prediction_id INT PRIMARY KEY,
      score FLOAT,
      prediction_date DATE
  );
  ```

### Schema 5: event_logs
- **Used In**: Default
- **Description**: Logs ML pipeline events.
- **Schema**:
  ```sql
  CREATE TABLE event_logs (
      log_id INT PRIMARY KEY,
      event_type VARCHAR(50),
      status VARCHAR(20)
  );
  ```

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` statements above for testing (e.g., for `Primary Key`, `Foreign Key` questions).
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run DDL operations.
3. **Compatibility**:
   - MySQL: Use `MODIFY` for `NOT NULL` changes; `CHECK` support varies (use PostgreSQL for full `CHECK` compatibility).
   - PostgreSQL: Supports all constraints fully.
   - SQL Server: Use `ALTER COLUMN` for `NOT NULL`; supports all other constraints.
4. **No Initial Data**: Questions focus on structure, so data isn’t needed unless testing constraints (e.g., insert to verify `CHECK`).
5. **Sample Data (Optional)**: For constraint testing, use minimal inserts:
  ```sql
  INSERT INTO models (model_id, model_name, created_date) VALUES
  (1, 'Model A', '2025-08-15');
  ```

---

<div align="center">
  <p>Crush these Constraints questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>