# 🎯 Interview Questions - Views to Crush SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Views and rule SQL interviews for AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** zone for **Views**! 💻 This README is your ultimate prep tool, packed with tricky, real-world questions covering **three core concepts**: `Create View`, `Alter View`, and `Drop View`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, sample data, and solutions (hidden in `<details>` tags), you’ll sharpen your view management skills, boost your confidence, and make your portfolio shine for recruiters. Let’s simplify queries and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Views**: Perfect your ability to create, modify, and remove virtual tables.
- **Power AI/ML Workflows**: Summarize model metrics, streamline dashboards, and optimize data access.
- **Shine Under Pressure**: Practice explaining view logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Create View`).
   - Read the question and try writing the DDL query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify view creation, modification, or deletion.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Create View` to nail query simplification, then tackle `Alter View` for trickier updates. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to view like a pro!

### 1. Create View
- **Description**: `CREATE VIEW` defines a virtual table based on a query.
- **Interview Focus**: Tests query design and data summarization.

#### Question 1.1: Model Performance Summary
- **Problem**: Your ML team needs a dashboard for model performance. Write a query to create a view named `model_performance` that shows `model_id`, `model_name`, and average `score` from `predictions` joined with `models`, grouped by `model_id` and `model_name`.
- **Trick**: Tests if you combine joins and aggregations correctly in a view.
- **AI/ML Use Case**: Simplifies model performance tracking for reports.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE VIEW model_performance AS
  SELECT m.model_id, m.model_name, AVG(p.score) AS avg_score
  FROM models m
  JOIN predictions p ON m.model_id = p.model_id
  GROUP BY m.model_id, m.model_name;
  ```
  </details>

#### Question 1.2: Recent Event Logs
- **Problem**: You’re monitoring ML pipeline events. Write a query to create a view named `recent_events` that shows `log_id`, `event_type`, and `status` from `event_logs` where `status` is 'Completed', ordered by `log_id`.
- **Trick**: Tests if you filter and order data effectively in a view.
- **AI/ML Use Case**: Provides a quick view of completed pipeline events.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE VIEW recent_events AS
  SELECT log_id, event_type, status
  FROM event_logs
  WHERE status = 'Completed'
  ORDER BY log_id;
  ```
  </details>

---

### 2. Alter View
- **Description**: `ALTER VIEW` or `CREATE OR REPLACE VIEW` modifies an existing view’s query.
- **Interview Focus**: Tests view updates and syntax accuracy.

#### Question 2.1: Update Performance Metrics
- **Problem**: The ML team wants additional metrics in `model_performance`. Write a query to alter the `model_performance` view to include `model_id`, `model_name`, average `score`, and count of predictions, grouped by `model_id` and `model_name`.
- **Trick**: Tests if you use `CREATE OR REPLACE VIEW` to update aggregations correctly.
- **AI/ML Use Case**: Enhances model performance dashboard with new metrics.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE OR REPLACE VIEW model_performance AS
  SELECT m.model_id, m.model_name, AVG(p.score) AS avg_score, COUNT(p.prediction_id) AS prediction_count
  FROM models m
  JOIN predictions p ON m.model_id = p.model_id
  GROUP BY m.model_id, m.model_name;
  ```
  </details>

#### Question 2.2: Expand Event Filters
- **Problem**: The `recent_events` view needs broader filtering. Write a query to alter `recent_events` to show `log_id`, `event_type`, and `status` from `event_logs` where `status` is either 'Completed' or 'Failed', ordered by `log_id` descending.
- **Trick**: Ensures you modify filtering logic without breaking the view.
- **AI/ML Use Case**: Updates event monitoring to include failures.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE OR REPLACE VIEW recent_events AS
  SELECT log_id, event_type, status
  FROM event_logs
  WHERE status IN ('Completed', 'Failed')
  ORDER BY log_id DESC;
  ```
  </details>

---

### 3. Drop View
- **Description**: `DROP VIEW` removes a view from the database.
- **Interview Focus**: Tests caution with destructive operations and syntax.

#### Question 3.1: Remove Outdated View
- **Problem**: The `model_performance` view is no longer needed. Write a query to drop the `model_performance` view.
- **Trick**: Tests if you use `DROP VIEW` correctly without affecting tables.
- **AI/ML Use Case**: Cleans up obsolete dashboard views.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP VIEW model_performance;
  ```
  </details>

#### Question 3.2: Eliminate Temporary View
- **Problem**: A temporary view for event analysis is cluttering the database. Write a query to drop the `recent_events` view.
- **Trick**: Ensures you specify the correct view for removal.
- **AI/ML Use Case**: Removes interim views after pipeline analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  DROP VIEW recent_events;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Simple**: Begin with `Create View` to master query-based tables.
- **Watch for Traps**: Interviewers test complex joins in `Create View`, query mismatches in `Alter View`, and accidental table drops in `Drop View`.
- **Explain Clearly**: Practice justifying view purposes (e.g., performance vs. security) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Views**: Keep view queries efficient to avoid performance hits on large datasets.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test view operations. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: models
- **Used In**: Create View, Alter View
- **Description**: Stores ML model metadata.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE
  );
  ```
- **Sample Data** (5 rows):
  ```sql
  INSERT INTO models (model_id, model_name, created_date) VALUES
  (101, 'Model A', '2025-08-01'),
  (102, 'Model B', '2025-08-02'),
  (103, 'Model C', '2025-08-03'),
  (104, 'Model D', '2025-08-04'),
  (105, 'Model E', '2025-08-05');
  ```

### Schema 2: predictions
- **Used In**: Create View, Alter View
- **Description**: Stores ML predictions linked to models.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE,
      FOREIGN KEY (model_id) REFERENCES models(model_id)
  );
  ```
- **Sample Data** (10 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 102, 0.95, '2025-08-17'),
  (4, 102, 0.78, '2025-08-18'),
  (5, 103, 0.91, '2025-08-19'),
  (6, 103, 0.84, '2025-08-20'),
  (7, 104, 0.96, '2025-08-21'),
  (8, 104, 0.80, '2025-08-22'),
  (9, 105, 0.89, '2025-08-23'),
  (10, 105, 0.93, '2025-08-24');
  ```

### Schema 3: event_logs
- **Used In**: Create View, Alter View
- **Description**: Logs ML pipeline events.
- **Schema**:
  ```sql
  CREATE TABLE event_logs (
      log_id INT PRIMARY KEY,
      event_type VARCHAR(50),
      status VARCHAR(20) DEFAULT 'Pending'
  );
  ```
- **Sample Data** (8 rows):
  ```sql
  INSERT INTO event_logs (log_id, event_type, status) VALUES
  (1, 'Training Start', 'Completed'),
  (2, 'Validation', 'Failed'),
  (3, 'Prediction Run', 'Completed'),
  (4, 'Model Update', 'Pending'),
  (5, 'Testing', 'Completed'),
  (6, 'Training Start', 'Failed'),
  (7, 'Prediction Run', 'Completed'),
  (8, 'Validation', 'Pending');
  ```

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run view operations.
3. **Compatibility**:
   - MySQL: Use `CREATE OR REPLACE VIEW` for `Alter View`; views are read-only by default.
   - PostgreSQL: Supports all syntax; allows updatable views with rules (not covered here).
   - SQL Server: Identical syntax; use `DROP VIEW` carefully to avoid errors.
4. **Data Scale**: Sample data is small for testing; scale to 100 rows by repeating patterns if needed.
5. **Verify Views**: Query views after creation (e.g., `SELECT * FROM model_performance`) to check results.

---

<div align="center">
  <p>Smash these Views questions to dominate SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>