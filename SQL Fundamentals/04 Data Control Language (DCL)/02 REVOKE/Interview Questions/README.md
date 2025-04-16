# 🎯 Interview Questions - REVOKE to Master SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Conquer REVOKE operations and secure your AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** zone for **REVOKE**! 💻 This README is your ultimate prep tool, packed with tricky, real-world questions covering **two core concepts**: `Revoke Permissions` and `Revoke Roles`. Designed to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, user setups, and solutions (hidden in `<details>` tags), you’ll sharpen your access control skills, boost your confidence, and make your portfolio shine for recruiters. Let’s tighten security and ace those interviews!

---

## 🎯 Why These Questions?

These questions are built to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master REVOKE**: Perfect your ability to remove permissions and roles safely.
- **Power AI/ML Workflows**: Restrict access to sensitive datasets and manage team privileges.
- **Shine Under Pressure**: Practice explaining revocation logic for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to wow recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, users, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Revoke Permissions`).
   - Read the question and try writing the REVOKE query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify permission or role removal.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Revoke Permissions` for targeted access control, then tackle `Revoke Roles` for team-level changes. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to revoke like a pro!

### 1. Revoke Permissions
- **Description**: `REVOKE` removes specific privileges (e.g., SELECT, INSERT) from users on database objects.
- **Interview Focus**: Tests precision in privilege removal and object targeting.

#### Question 1.1: Restrict Analyst Access
- **Problem**: An analyst no longer needs to query predictions. Write a query to revoke `SELECT` permission on the `predictions` table from the user `ml_analyst`.
- **Trick**: Tests if you remove only the specified privilege without affecting others.
- **AI/ML Use Case**: Limits access to model outputs for security.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  REVOKE SELECT ON predictions FROM ml_analyst;
  ```
  </details>

#### Question 1.2: Limit Developer Privileges
- **Problem**: A developer’s role has changed. Write a query to revoke `INSERT` and `UPDATE` permissions on the `models` table from the user `ml_developer`, leaving `SELECT` intact.
- **Trick**: Ensures you revoke multiple privileges selectively without over-restricting.
- **AI/ML Use Case**: Reduces write access to model metadata after a project phase.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  REVOKE INSERT, UPDATE ON models FROM ml_developer;
  ```
  </details>

---

### 2. Revoke Roles
- **Description**: `REVOKE` removes roles from users, stripping associated privileges.
- **Interview Focus**: Tests role-based access control and hierarchy management.

#### Question 2.1: Remove Analyst Role
- **Problem**: An analyst has left the ML team. Write a query to revoke the `analyst_role` from the user `ml_analyst`, where `analyst_role` includes `SELECT` on `predictions` and `models`.
- **Trick**: Tests if you understand role revocation and its impact on privileges.
- **AI/ML Use Case**: Cleans up access for departed team members.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  REVOKE analyst_role FROM ml_analyst;
  ```
  </details>

#### Question 2.2: Demote Team Lead
- **Problem**: The ML team lead’s admin privileges are being downgraded. Write a query to revoke the `admin_role` from the user `ml_lead`, where `admin_role` has `ALL PRIVILEGES` on `predictions`, `models`, and `event_logs`.
- **Trick**: Ensures you revoke a powerful role carefully, considering its broad scope.
- **AI/ML Use Case**: Adjusts access for role reassignment in the pipeline.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  REVOKE admin_role FROM ml_lead;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Precise**: Begin with `Revoke Permissions` to master selective access removal.
- **Watch for Traps**: Interviewers test over-revoking in `Revoke Permissions` and role dependency issues in `Revoke Roles`.
- **Explain Clearly**: Practice justifying revocation reasons (e.g., security compliance) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the setups below.
- **Secure Access**: Verify revoked permissions to ensure minimal privilege principles.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables, users, and roles in your database (MySQL, PostgreSQL, or SQL Server). Each question tests REVOKE operations, so you’ll remove permissions or roles from users. Below are schemas, user setups, and sample data—copy-paste to test queries or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Revoke Permissions, Revoke Roles
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
- **Used In**: Revoke Permissions, Revoke Roles
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
- **Used In**: Revoke Roles
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

### User and Role Setup
- **Users**:
  ```sql
  CREATE USER 'ml_analyst'@'localhost' IDENTIFIED BY 'securepass';
  CREATE USER 'ml_developer'@'localhost' IDENTIFIED BY 'devpass';
  CREATE USER 'ml_lead'@'localhost' IDENTIFIED BY 'leadpass';
  ```
- **Roles and Initial Grants**:
  ```sql
  CREATE ROLE analyst_role;
  CREATE ROLE admin_role;
  GRANT SELECT ON predictions TO analyst_role;
  GRANT SELECT ON models TO analyst_role;
  GRANT ALL PRIVILEGES ON predictions TO admin_role;
  GRANT ALL PRIVILEGES ON models TO admin_role;
  GRANT ALL PRIVILEGES ON event_logs TO admin_role;
  GRANT analyst_role TO ml_analyst;
  GRANT admin_role TO ml_lead;
  GRANT SELECT, INSERT, UPDATE ON models TO ml_developer;
  GRANT SELECT ON predictions TO ml_analyst;
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Set Up Users and Roles**: Execute the user, role, and GRANT queries to establish initial permissions.
3. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run REVOKE operations.
4. **Compatibility**:
   - MySQL: Supports `REVOKE` for permissions; roles require MySQL 8.0+.
   - PostgreSQL: Fully supports roles and permissions; use `REVOKE` similarly.
   - SQL Server: Uses `REVOKE` for permissions; roles are `DATABASE ROLE`.
5. **Verify Revocation**: Test access (e.g., attempt `SELECT * FROM predictions` as `ml_analyst`) after revoking.
6. **Data Scale**: Sample data is small for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Crush these REVOKE questions to dominate SQL interviews and supercharge your AI/ML journey! Happy querying! ✨</p>
</div>