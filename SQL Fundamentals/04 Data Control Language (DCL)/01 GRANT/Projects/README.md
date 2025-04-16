# 📊 Projects - Mastering GRANT Permissions

## 🌟 Overview

Welcome to the **Projects** section for **GRANT Permissions**! 🚀 These five unique projects are your playground to master the four core concepts—`GRANT SELECT`, `GRANT INSERT/UPDATE/DELETE`, `GRANT ALL PRIVILEGES`, and `GRANT WITH GRANT OPTION`. Dive into AI/ML-themed challenges like securing dataset access or managing model pipelines, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL GRANT permissions practical and fun, helping you:
- **Apply Skills**: Secure ML datasets and pipelines with precise permissions.
- **Ace Interviews**: Solve access control problems like those in real-world DB admin scenarios.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Control data access for model training, analysis, or deployment.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key GRANT techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Dataset Access** | GRANT SELECT | Grant read-only access to ML datasets for analysts. |
| **Model Management** | GRANT INSERT/UPDATE/DELETE | Assign data modification permissions for model logs. |
| **Analyst Permissions** | GRANT ALL PRIVILEGES | Provide full access to reporting tables for data scientists. |
| **Delegated Access** | GRANT WITH GRANT OPTION | Enable team leads to delegate permissions for ML pipelines. |
| **Capstone: Permissions** | All Four | Design a permission model for an ML fraud detection system. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables, load data, and set up users.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Dataset_Access/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) with admin privileges to verify permissions.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `GRANT SELECT`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Dataset Access
- **Folder**: `Project1_Dataset_Access/`
- **Concepts**: `GRANT SELECT`
- **Description**: Grant read-only access to ML datasets for data analysts to explore model inputs.
- **Tasks**:
  - Grant `SELECT` on `training_data` to user `analyst1`.
  - Grant `SELECT` on `predictions` to role `data_team`.
  - Grant `SELECT` on specific columns (`feature1`, `label`) of `training_data` to user `intern`.
- **AI/ML Use Case**: Ensures analysts can query datasets without modifying them.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  GRANT SELECT ON training_data TO analyst1;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  GRANT SELECT ON predictions TO data_team;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  GRANT SELECT (feature1, label) ON training_data TO intern;
  ```
  </details>

### Project 2: Model Management
- **Folder**: `Project2_Model_Management/`
- **Concepts**: `GRANT INSERT/UPDATE/DELETE`
- **Description**: Assign data modification permissions for model logs to ML engineers.
- **Tasks**:
  - Grant `INSERT` and `UPDATE` on `model_logs` to user `engineer1`.
  - Grant `DELETE` on `predictions` to role `ml_team`.
  - Grant `INSERT` on `model_versions` to user `developer`.
- **AI/ML Use Case**: Allows engineers to manage model outputs and logs.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  GRANT INSERT, UPDATE ON model_logs TO engineer1;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  GRANT DELETE ON predictions TO ml_team;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  GRANT INSERT ON model_versions TO developer;
  ```
  </details>

### Project 3: Analyst Permissions
- **Folder**: `Project3_Analyst_Permissions/`
- **Concepts**: `GRANT ALL PRIVILEGES`
- **Description**: Provide full access to reporting tables for data scientists to build ML dashboards.
- **Tasks**:
  - Grant `ALL PRIVILEGES` on `sales_summary` to user `scientist1`.
  - Grant `ALL PRIVILEGES` on `model_performance` to role `reporting_team`.
  - Grant `ALL PRIVILEGES` on `customer_stats` to user `bi_analyst`.
- **AI/ML Use Case**: Enables unrestricted access for reporting and analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  GRANT ALL PRIVILEGES ON sales_summary TO scientist1;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  GRANT ALL PRIVILEGES ON model_performance TO reporting_team;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  GRANT ALL PRIVILEGES ON customer_stats TO bi_analyst;
  ```
  </details>

### Project 4: Delegated Access
- **Folder**: `Project4_Delegated_Access/`
- **Concepts**: `GRANT WITH GRANT OPTION`
- **Description**: Enable team leads to delegate permissions for ML pipelines to their teams.
- **Tasks**:
  - Grant `SELECT` on `orders` to user `lead1` with `WITH GRANT OPTION`.
  - Grant `INSERT`, `UPDATE` on `fraud_flags` to role `fraud_team` with `WITH GRANT OPTION`.
  - Grant `ALL PRIVILEGES` on `training_data` to user `manager` with `WITH GRANT OPTION`.
- **AI/ML Use Case**: Supports collaborative ML workflows with delegated access.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  GRANT SELECT ON orders TO lead1 WITH GRANT OPTION;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  GRANT INSERT, UPDATE ON fraud_flags TO fraud_team WITH GRANT OPTION;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  GRANT ALL PRIVILEGES ON training_data TO manager WITH GRANT OPTION;
  ```
  </details>

### Project 5: Capstone - Permissions
- **Folder**: `Project5_Capstone_Permissions/`
- **Concepts**: All Four (`GRANT SELECT`, `GRANT INSERT/UPDATE/DELETE`, `GRANT ALL PRIVILEGES`, `GRANT WITH GRANT OPTION`)
- **Description**: Design a permission model for an ML fraud detection system with varied access levels.
- **Tasks**:
  - Grant `SELECT` on `orders` to user `fraud_analyst`.
  - Grant `INSERT`, `UPDATE` on `fraud_flags` to user `fraud_engineer`.
  - Grant `ALL PRIVILEGES` on `fraud_stats` to role `fraud_report_team`.
  - Grant `SELECT`, `INSERT` on `order_logs` to user `team_lead` with `WITH GRANT OPTION`.
  - Grant `DELETE` on `fraud_flags` to user `admin`.
- **AI/ML Use Case**: Secures a fraud detection pipeline with role-based access.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  GRANT SELECT ON orders TO fraud_analyst;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  GRANT INSERT, UPDATE ON fraud_flags TO fraud_engineer;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  GRANT ALL PRIVILEGES ON fraud_stats TO fraud_report_team;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  GRANT SELECT, INSERT ON order_logs TO team_lead WITH GRANT OPTION;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  GRANT DELETE ON fraud_flags TO admin;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `GRANT SELECT`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries with admin privileges in a local database to verify permissions.
- **Combine Skills**: Mix `WITH GRANT OPTION` and `ALL PRIVILEGES` for realistic scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore role-based access control (RBAC) in DB admin guides or interview questions.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for GRANT permissions? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables, data, and users in your database (MySQL, PostgreSQL, or similar). Each project applies `GRANT` permissions to these tables, testing all four concepts. Below are schemas, sample data, and user/role setups—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: training_data
- **Used In**: Project 1, Project 4, Project 5 (Capstone)
- **Description**: ML training data for permission assignments.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label) VALUES
  (1, 0.5, 1.8, 'positive'),
  (2, 1.2, 2.5, 'negative'),
  (3, 2.3, 3.1, 'positive'),
  (4, 0.8, 1.4, 'negative'),
  (5, 1.9, 2.9, 'positive'),
  (6, 0.3, 1.7, 'negative'),
  (7, 2.1, 3.4, 'positive'),
  (8, 1.0, 2.0, 'negative'),
  (9, 1.6, 2.6, 'positive'),
  (10, 0.7, 1.9, 'negative'),
  (11, 2.4, 3.2, 'positive'),
  (12, 0.9, 1.5, 'negative'),
  (13, 1.8, 2.8, 'positive'),
  (14, 0.4, 1.3, 'negative'),
  (15, 2.0, 3.0, 'positive'),
  (16, 0.8, 1.7, 'negative'),
  (17, 1.7, 2.7, 'positive'),
  (18, 0.6, 1.6, 'negative'),
  (19, 2.2, 3.3, 'positive'),
  (20, 0.5, 1.9, 'negative');
  ```
- **Notes**: Supports `GRANT SELECT`, `WITH GRANT OPTION` for analyst access.

### Dataset 2: predictions
- **Used In**: Project 1, Project 2, Project 5 (Capstone)
- **Description**: ML model predictions for permission management.
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
  (1, 101, 0.92, '2025-08-01'),
  (2, 101, 0.87, '2025-08-02'),
  (3, 102, 0.95, '2025-08-03'),
  (4, 102, 0.78, '2025-08-04'),
  (5, 103, 0.91, '2025-08-05'),
  (6, 103, 0.84, '2025-08-06'),
  (7, 104, 0.96, '2025-08-07'),
  (8, 104, 0.80, '2025-08-08'),
  (9, 105, 0.89, '2025-08-09'),
  (10, 105, 0.93, '2025-08-10'),
  (11, 106, 0.77, '2025-08-11'),
  (12, 106, 0.94, '2025-08-12'),
  (13, 107, 0.85, '2025-08-13'),
  (14, 107, 0.90, '2025-08-14'),
  (15, 108, 0.88, '2025-08-15'),
  (16, 108, 0.97, '2025-08-16'),
  (17, 109, 0.79, '2025-08-17'),
  (18, 109, 0.92, '2025-08-18'),
  (19, 110, 0.86, '2025-08-19'),
  (20, 110, 0.91, '2025-08-20');
  ```
- **Notes**: Supports `GRANT SELECT`, `DELETE` for model management.

### Dataset 3: model_logs
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Model logs for engineer permissions.
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
  (1, 101, 'Training started', '2025-08-01 10:00:00'),
  (2, 101, 'Training completed', '2025-08-01 12:00:00'),
  (3, 102, 'Validation error', '2025-08-02 09:30:00'),
  (4, 102, 'Model deployed', '2025-08-02 14:00:00'),
  (5, 103, 'Hyperparameter tuned', '2025-08-03 11:00:00'),
  (6, 103, 'Testing started', '2025-08-03 15:00:00'),
  (7, 104, 'Prediction generated', '2025-08-04 08:00:00'),
  (8, 104, 'Model updated', '2025-08-04 16:00:00'),
  (9, 105, 'Error logged', '2025-08-05 10:30:00'),
  (10, 105, 'Retraining initiated', '2025-08-05 13:00:00'),
  (11, 106, 'Training started', '2025-08-06 09:00:00'),
  (12, 106, 'Training completed', '2025-08-06 11:00:00'),
  (13, 107, 'Validation error', '2025-08-07 10:00:00'),
  (14, 107, 'Model deployed', '2025-08-07 14:30:00'),
  (15, 108, 'Hyperparameter tuned', '2025-08-08 12:00:00'),
  (16, 108, 'Testing started', '2025-08-08 15:00:00'),
  (17, 109, 'Prediction generated', '2025-08-09 09:00:00'),
  (18, 109, 'Model updated', '2025-08-09 17:00:00'),
  (19, 110, 'Error logged', '2025-08-10 11:00:00'),
  (20, 110, 'Retraining initiated', '2025-08-10 14:00:00');
  ```
- **Notes**: Supports `GRANT INSERT/UPDATE` for log management.

### Dataset 4: model_versions
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Model version data for developer permissions.
- **Schema**:
  ```sql
  CREATE TABLE model_versions (
      version_id INT PRIMARY KEY,
      model_id INT,
      version_number FLOAT,
      release_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO model_versions (version_id, model_id, version_number, release_date) VALUES
  (1, 101, 1.0, '2025-08-01'),
  (2, 101, 1.1, '2025-08-02'),
  (3, 102, 1.0, '2025-08-03'),
  (4, 102, 1.2, '2025-08-04'),
  (5, 103, 1.0, '2025-08-05'),
  (6, 103, 1.3, '2025-08-06'),
  (7, 104, 1.0, '2025-08-07'),
  (8, 104, 1.4, '2025-08-08'),
  (9, 105, 1.0, '2025-08-09'),
  (10, 105, 1.5, '2025-08-10'),
  (11, 106, 1.0, '2025-08-11'),
  (12, 106, 1.1, '2025-08-12'),
  (13, 107, 1.0, '2025-08-13'),
  (14, 107, 1.2, '2025-08-14'),
  (15, 108, 1.0, '2025-08-15'),
  (16, 108, 1.3, '2025-08-16'),
  (17, 109, 1.0, '2025-08-17'),
  (18, 109, 1.4, '2025-08-18'),
  (19, 110, 1.0, '2025-08-19'),
  (20, 110, 1.5, '2025-08-20');
  ```
- **Notes**: Supports `GRANT INSERT` for version updates.

### Dataset 5: sales_summary
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Sales summary for reporting permissions.
- **Schema**:
  ```sql
  CREATE TABLE sales_summary (
      region_id INT PRIMARY KEY,
      region VARCHAR(50),
      total_sales FLOAT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO sales_summary (region_id, region, total_sales) VALUES
  (1, 'North', 1500.0),
  (2, 'South', 2200.5),
  (3, 'East', 1800.0),
  (4, 'West', 1900.3),
  (5, 'North', 1700.0),
  (6, 'South', 2100.0),
  (7, 'East', 1600.5),
  (8, 'West', 2000.0),
  (9, 'North', 1400.7),
  (10, 'South', 2300.0),
  (11, 'East', 1500.0),
  (12, 'West', 1800.5),
  (13, 'North', 1600.0),
  (14, 'South', 1900.0),
  (15, 'East', 1700.3),
  (16, 'West', 2100.0),
  (17, 'North', 1300.0),
  (18, 'South', 2400.5),
  (19, 'East', 1400.0),
  (20, 'West', 2200.0);
  ```
- **Notes**: Supports `GRANT ALL PRIVILEGES` for reporting.

### Dataset 6: model_performance
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Model performance metrics for data scientists.
- **Schema**:
  ```sql
  CREATE TABLE model_performance (
      model_id INT PRIMARY KEY,
      avg_score FLOAT,
      prediction_count INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO model_performance (model_id, avg_score, prediction_count) VALUES
  (101, 0.89, 10),
  (102, 0.87, 12),
  (103, 0.91, 8),
  (104, 0.93, 15),
  (105, 0.88, 9),
  (106, 0.90, 11),
  (107, 0.86, 7),
  (108, 0.92, 13),
  (109, 0.85, 10),
  (110, 0.94, 14),
  (111, 0.87, 6),
  (112, 0.89, 12),
  (113, 0.91, 9),
  (114, 0.88, 11),
  (115, 0.90, 8),
  (116, 0.92, 10),
  (117, 0.86, 13),
  (118, 0.93, 7),
  (119, 0.89, 15),
  (120, 0.91, 9);
  ```
- **Notes**: Supports `GRANT ALL PRIVILEGES` for analysis.

### Dataset 7: customer_stats
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Customer statistics for BI analysts.
- **Schema**:
  ```sql
  CREATE TABLE customer_stats (
      customer_id INT PRIMARY KEY,
      order_count INT,
      total_spent FLOAT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO customer_stats (customer_id, order_count, total_spent) VALUES
  (301, 5, 450.0),
  (302, 3, 300.5),
  (303, 7, 600.0),
  (304, 2, 200.0),
  (305, 4, 350.3),
  (306, 6, 500.0),
  (307, 1, 100.0),
  (308, 8, 700.5),
  (309, 3, 250.0),
  (310, 5, 400.0),
  (311, 2, 150.0),
  (312, 4, 320.5),
  (313, 6, 550.0),
  (314, 3, 270.0),
  (315, 7, 650.3),
  (316, 1, 80.0),
  (317, 5, 420.0),
  (318, 4, 360.0),
  (319, 2, 180.0),
  (320, 6, 480.5);
  ```
- **Notes**: Supports `GRANT ALL PRIVILEGES` for reporting.

### Dataset 8: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for fraud detection permissions.
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
  (101, 301, 80.0, '2025-08-01'),
  (102, 302, 120.5, '2025-08-02'),
  (103, 303, 15.0, '2025-08-03'),
  (104, 304, 250.0, '2025-08-04'),
  (105, 305, 65.3, '2025-08-05'),
  (106, 306, 400.0, '2025-08-06'),
  (107, 307, 30.0, '2025-08-07'),
  (108, 308, 110.7, '2025-08-08'),
  (109, 309, 70.5, '2025-08-09'),
  (110, 310, 50.0, '2025-08-10'),
  (111, 311, 200.0, '2025-08-11'),
  (112, 312, 20.0, '2025-08-12'),
  (113, 313, 160.0, '2025-08-13'),
  (114, 314, 35.0, '2025-08-14'),
  (115, 315, 90.0, '2025-08-15'),
  (116, 316, 60.5, '2025-08-16'),
  (117, 317, 180.5, '2025-08-17'),
  (118, 318, 45.0, '2025-08-18'),
  (119, 319, 100.0, '2025-08-19'),
  (120, 320, 75.0, '2025-08-20');
  ```
- **Notes**: Supports `WITH GRANT OPTION` for delegated access.

### Dataset 9: fraud_flags
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Fraud flags for permission delegation.
- **Schema**:
  ```sql
  CREATE TABLE fraud_flags (
      flag_id INT PRIMARY KEY,
      order_id INT,
      flag_reason VARCHAR(100)
  );
  ```
- **Sample Data** (20 rows):
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
  (15, 115, 'Suspicious pattern'),
  (16, 116, 'Invalid address'),
  (17, 117, 'High amount'),
  (18, 118, 'Multiple orders'),
  (19, 119, 'Suspicious pattern'),
  (20, 120, 'Invalid address');
  ```
- **Notes**: Supports `GRANT INSERT/UPDATE`, `DELETE` for fraud management.

### Dataset 10: order_logs
- **Used In**: Project 5 (Capstone)
- **Description**: Order logs for fraud permissions.
- **Schema**:
  ```sql
  CREATE TABLE order_logs (
      log_id INT PRIMARY KEY,
      order_id INT,
      status VARCHAR(50),
      log_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO order_logs (log_id, order_id, status, log_date) VALUES
  (1, 101, 'PENDING', '2025-08-01'),
  (2, 102, 'APPROVED', '2025-08-02'),
  (3, 103, 'REJECTED', '2025-08-03'),
  (4, 104, 'PENDING', '2025-08-04'),
  (5, 105, 'APPROVED', '2025-08-05'),
  (6, 106, 'REJECTED', '2025-08-06'),
  (7, 107, 'PENDING', '2025-08-07'),
  (8, 108, 'APPROVED', '2025-08-08'),
  (9, 109, 'REJECTED', '2025-08-09'),
  (10, 110, 'PENDING', '2025-08-10'),
  (11, 111, 'APPROVED', '2025-08-11'),
  (12, 112, 'REJECTED', '2025-08-12'),
  (13, 113, 'PENDING', '2025-08-13'),
  (14, 114, 'APPROVED', '2025-08-14'),
  (15, 115, 'REJECTED', '2025-08-15'),
  (16, 116, 'PENDING', '2025-08-16'),
  (17, 117, 'APPROVED', '2025-08-17'),
  (18, 118, 'REJECTED', '2025-08-18'),
  (19, 119, 'PENDING', '2025-08-19'),
  (20, 120, 'APPROVED', '2025-08-20');
  ```
- **Notes**: Supports `GRANT SELECT/INSERT` for logging.

### Dataset 11: fraud_stats
- **Used In**: Project 5 (Capstone)
- **Description**: Fraud statistics for reporting permissions.
- **Schema**:
  ```sql
  CREATE TABLE fraud_stats (
      customer_id INT PRIMARY KEY,
      order_count INT,
      total_amount FLOAT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO fraud_stats (customer_id, order_count, total_amount) VALUES
  (301, 4, 320.0),
  (302, 3, 250.5),
  (303, 5, 400.0),
  (304, 2, 180.0),
  (305, 6, 450.3),
  (306, 1, 100.0),
  (307, 7, 600.0),
  (308, 3, 270.5),
  (309, 4, 350.0),
  (310, 2, 200.0),
  (311, 5, 420.0),
  (312, 3, 260.0),
  (313, 6, 500.0),
  (314, 1, 90.0),
  (315, 4, 380.3),
  (316, 2, 150.0),
  (317, 5, 430.0),
  (318, 3, 280.0),
  (319, 4, 360.0),
  (320, 2, 220.0);
  ```
- **Notes**: Supports `GRANT ALL PRIVILEGES` for fraud reporting.

### User and Role Setup
- **Users**: Create the following users for testing permissions:
  ```sql
  CREATE USER 'analyst1'@'localhost' IDENTIFIED BY 'password1';
  CREATE USER 'intern'@'localhost' IDENTIFIED BY 'password2';
  CREATE USER 'engineer1'@'localhost' IDENTIFIED BY 'password3';
  CREATE USER 'developer'@'localhost' IDENTIFIED BY 'password4';
  CREATE USER 'scientist1'@'localhost' IDENTIFIED BY 'password5';
  CREATE USER 'bi_analyst'@'localhost' IDENTIFIED BY 'password6';
  CREATE USER 'lead1'@'localhost' IDENTIFIED BY 'password7';
  CREATE USER 'manager'@'localhost' IDENTIFIED BY 'password8';
  CREATE USER 'fraud_analyst'@'localhost' IDENTIFIED BY 'password9';
  CREATE USER 'fraud_engineer'@'localhost' IDENTIFIED BY 'password10';
  CREATE USER 'team_lead'@'localhost' IDENTIFIED BY 'password11';
  CREATE USER 'admin'@'localhost' IDENTIFIED BY 'password12';
  ```
- **Roles**: Create the following roles for group permissions:
  ```sql
  CREATE ROLE data_team;
  CREATE ROLE ml_team;
  CREATE ROLE reporting_team;
  CREATE ROLE fraud_team;
  CREATE ROLE fraud_report_team;
  ```
- **Notes**: Ensure the database user running these commands has admin privileges to create users/roles and grant permissions.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Set Up Users/Roles**: Execute the user and role creation commands.
3. **Apply Permissions**: Use project tasks to grant permissions (e.g., `GRANT SELECT`).
4. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) with admin access to test permissions.
5. **Compatibility**:
   - MySQL: Roles supported in 8.0+; use `SET ROLE` to activate. Column-level grants supported.
   - PostgreSQL: Full support for roles and privileges; use `GRANT ... ON TABLE` syntax.
   - SQL Server: Use `DATABASE ROLE` for roles; column-level grants supported with `GRANT ... (column)`.
6. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master GRANT Permissions and shine in AI/ML interviews! Happy querying! ✨</p>
</div>