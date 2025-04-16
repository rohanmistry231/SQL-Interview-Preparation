# 🎯 Interview Questions - GRANT to Ace SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master GRANT operations and secure your spot in AI/ML roles! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** hub for **GRANT**! 💻 This README is your go-to resource, loaded with tricky, real-world questions covering **two core concepts**: `Grant Permissions` and `Grant Roles`. Crafted to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, user setups, and solutions (tucked away in `<details>` tags), you’ll hone your permission management skills, boost your confidence, and make your portfolio stand out for recruiters. Let’s lock down access and crush those interviews!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master GRANT**: Perfect your ability to assign permissions and roles securely.
- **Power AI/ML Workflows**: Control access to datasets, protect model outputs, and manage team privileges.
- **Shine Under Pressure**: Practice explaining access control for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, users, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Grant Permissions`).
   - Read the question and try writing the GRANT query in a sandbox (MySQL, PostgreSQL, etc.).
3. **Test Your Query**: Run it to verify permissions or role assignments.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your query logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Grant Permissions` for direct access control, then tackle `Grant Roles` for team-level management. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to grant like a pro!

### 1. Grant Permissions
- **Description**: `GRANT` assigns specific privileges (e.g., SELECT, INSERT) to users on database objects.
- **Interview Focus**: Tests precision in privilege assignment and object targeting.

#### Question 1.1: Analyst Data Access
- **Problem**: Your ML team’s analyst needs to query predictions. Write a query to grant `SELECT` permission on the `predictions` table to the user `ml_analyst`.
- **Trick**: Tests if you assign only the required privilege without over-privileging.
- **AI/ML Use Case**: Enables analysts to view model outputs securely.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  GRANT SELECT ON predictions TO ml_analyst;
  ```
  </details>

#### Question 1.2: Developer Write Access
- **Problem**: An ML developer needs to update model metadata. Write a query to grant `SELECT`, `INSERT`, and `UPDATE` permissions on the `models` table to the user `ml_developer`.
- **Trick**: Ensures you grant multiple privileges correctly for a single object.
- **AI/ML Use Case**: Allows developers to manage model records.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  GRANT SELECT, INSERT, UPDATE ON models TO ml_developer;
  ```
  </details>

---

### 2. Grant Roles
- **Description**: `GRANT` assigns roles to users, bundling privileges for easier management.
- **Interview Focus**: Tests role-based access control and hierarchy understanding.

#### Question 2.1: Assign Analyst Role
- **Problem**: Your ML pipeline uses a role for analysts. Write a query to grant the `analyst_role` to the user `ml_analyst`, assuming `analyst_role` has `SELECT` on `predictions` and `models`.
- **Trick**: Tests if you understand role assignment without needing to redefine privileges.
- **AI/ML Use Case**: Streamlines access for the analytics team.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  GRANT analyst_role TO ml_analyst;
  ```
  </details>

#### Question 2.2: Admin Role for Team Lead
- **Problem**: The ML team lead needs full control. Write a query to grant the `admin_role` to the user `ml_lead`, assuming `admin_role` has `ALL PRIVILEGES` on `predictions`, `models`, and `event_logs`.
- **Trick**: Ensures you assign a powerful role carefully, understanding its scope.
- **AI/ML Use Case**: Empowers the lead to manage all pipeline data.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  GRANT admin_role TO ml_lead;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Simple**: Begin with `Grant Permissions` to nail specific privileges.
- **Watch for Traps**: Interviewers test over-privileging in `Grant Permissions` and role scope in `Grant Roles`.
- **Explain Clearly**: Practice justifying permission choices (e.g., least privilege principle) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the setups below.
- **Optimize Access**: Use roles for teams to simplify management; avoid blanket `ALL PRIVILEGES`.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables, users, and roles in your database (MySQL, PostgreSQL, or SQL Server). Each question tests GRANT operations, so you’ll assign permissions or roles to users. Below are schemas, user setups, and sample data—copy-paste to test queries or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Grant Permissions, Grant Roles
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
- **Used In**: Grant Permissions, Grant Roles
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
- **Used In**: Grant Roles
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
- **Roles**:
  ```sql
  CREATE ROLE analyst_role;
  CREATE ROLE admin_role;
  GRANT SELECT ON predictions TO analyst_role;
  GRANT SELECT ON models TO analyst_role;
  GRANT ALL PRIVILEGES ON predictions TO admin_role;
  GRANT ALL PRIVILEGES ON models TO admin_role;
  GRANT ALL PRIVILEGES ON event_logs TO admin_role;
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Set Up Users and Roles**: Execute the user and role creation queries.
3. **Test Queries**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to run GRANT operations.
4. **Compatibility**:
   - MySQL: Supports `GRANT` for permissions; roles require MySQL 8.0+.
   - PostgreSQL: Fully supports roles and permissions; use `GRANT` similarly.
   - SQL Server: Uses `GRANT` for permissions; roles are `DATABASE ROLE`.
5. **Verify Permissions**: Test access (e.g., `SELECT * FROM predictions` as `ml_analyst`) after granting.
6. **Data Scale**: Sample data is small for testing; scale to 100 rows by repeating patterns if needed.

---

<div align="center">
  <p>Smash these GRANT questions to rule SQL interviews and turbocharge your AI/ML journey! Happy querying! ✨</p>
</div>