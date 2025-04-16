# 📊 Projects - Mastering REVOKE Permissions

## 🌟 Overview

Welcome to the **Projects** section for **REVOKE Permissions**! 🚀 These five unique projects are your playground to master the four core concepts—`REVOKE SELECT`, `REVOKE INSERT/UPDATE/DELETE`, `REVOKE ALL PRIVILEGES`, and `REVOKE WITH GRANT OPTION`. Dive into AI/ML-themed challenges like tightening dataset security or restricting model pipeline access, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL REVOKE permissions practical and fun, helping you:
- **Apply Skills**: Secure ML datasets and pipelines by removing unnecessary access.
- **Ace Interviews**: Solve access control problems like those in real-world DB admin scenarios.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Restrict data access to protect model training, analysis, or deployment.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key REVOKE techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Dataset Security** | REVOKE SELECT | Remove read access to ML datasets for unauthorized users. |
| **Model Restrictions** | REVOKE INSERT/UPDATE/DELETE | Restrict data modification for model logs and predictions. |
| **Analyst Lockdown** | REVOKE ALL PRIVILEGES | Revoke full access to reporting tables for former analysts. |
| **Delegation Control** | REVOKE WITH GRANT OPTION | Remove delegation permissions for ML pipeline leads. |
| **Capstone: Revocations** | All Four | Redesign permissions for an ML fraud detection system by revoking access. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables, load data, and set up users/permissions.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Dataset_Security/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) with admin privileges to verify revoked permissions.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `REVOKE SELECT`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Dataset Security
- **Folder**: `Project1_Dataset_Security/`
- **Concepts**: `REVOKE SELECT`
- **Description**: Remove read access to ML datasets for unauthorized users to protect sensitive data.
- **Tasks**:
  - Revoke `SELECT` on `training_data` from user `intern`.
  - Revoke `SELECT` on `predictions` from role `data_team`.
  - Revoke `SELECT` on specific columns (`feature1`, `label`) of `training_data` from user `analyst1`.
- **AI/ML Use Case**: Ensures only authorized analysts query datasets.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  REVOKE SELECT ON training_data FROM intern;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  REVOKE SELECT ON predictions FROM data_team;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  REVOKE SELECT (feature1, label) ON training_data FROM analyst1;
  ```
  </details>

### Project 2: Model Restrictions
- **Folder**: `Project2_Model_Restrictions/`
- **Concepts**: `REVOKE INSERT/UPDATE/DELETE`
- **Description**: Restrict data modification for model logs and predictions to secure ML pipelines.
- **Tasks**:
  - Revoke `INSERT` and `UPDATE` on `model_logs` from user `engineer1`.
  - Revoke `DELETE` on `predictions` from role `ml_team`.
  - Revoke `INSERT` on `model_versions` from user `developer`.
- **AI/ML Use Case**: Prevents unauthorized changes to model outputs.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  REVOKE INSERT, UPDATE ON model_logs FROM engineer1;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  REVOKE DELETE ON predictions FROM ml_team;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  REVOKE INSERT ON model_versions FROM developer;
  ```
  </details>

### Project 3: Analyst Lockdown
- **Folder**: `Project3_Analyst_Lockdown/`
- **Concepts**: `REVOKE ALL PRIVILEGES`
- **Description**: Revoke full access to reporting tables for former analysts to maintain security.
- **Tasks**:
  - Revoke `ALL PRIVILEGES` on `sales_summary` from user `scientist1`.
  - Revoke `ALL PRIVILEGES` on `model_performance` from role `reporting_team`.
  - Revoke `ALL PRIVILEGES` on `customer_stats` from user `bi_analyst`.
- **AI/ML Use Case**: Secures reporting data after team changes.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  REVOKE ALL PRIVILEGES ON sales_summary FROM scientist1;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  REVOKE ALL PRIVILEGES ON model_performance FROM reporting_team;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  REVOKE ALL PRIVILEGES ON customer_stats FROM bi_analyst;
  ```
  </details>

### Project 4: Delegation Control
- **Folder**: `Project4_Delegation_Control/`
- **Concepts**: `REVOKE WITH GRANT OPTION`
- **Description**: Remove delegation permissions for ML pipeline leads to limit access spread.
- **Tasks**:
  - Revoke `SELECT` with `WITH GRANT OPTION` on `orders` from user `lead1`.
  - Revoke `INSERT`, `UPDATE` with `WITH GRANT OPTION` on `fraud_flags` from role `fraud_team`.
  - Revoke `ALL PRIVILEGES` with `WITH GRANT OPTION` on `training_data` from user `manager`.
- **AI/ML Use Case**: Prevents over-delegation in collaborative ML workflows.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  REVOKE GRANT OPTION FOR SELECT ON orders FROM lead1;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  REVOKE GRANT OPTION FOR INSERT, UPDATE ON fraud_flags FROM fraud_team;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  REVOKE GRANT OPTION FOR ALL PRIVILEGES ON training_data FROM manager;
  ```
  </details>

### Project 5: Capstone - Revocations
- **Folder**: `Project5_Capstone_Revocations/`
- **Concepts**: All Four (`REVOKE SELECT`, `REVOKE INSERT/UPDATE/DELETE`, `REVOKE ALL PRIVILEGES`, `REVOKE WITH GRANT OPTION`)
- **Description**: Redesign permissions for an ML fraud detection system by revoking unnecessary access.
- **Tasks**:
  - Revoke `SELECT` on `orders` from user `fraud_analyst`.
  - Revoke `INSERT`, `UPDATE` on `fraud_flags` from user `fraud_engineer`.
  - Revoke `ALL PRIVILEGES` on `fraud_stats` from role `fraud_report_team`.
  - Revoke `SELECT`, `INSERT` with `WITH GRANT OPTION` on `order_logs` from user `team_lead`.
  - Revoke `DELETE` on `fraud_flags` from user `admin`.
- **AI/ML Use Case**: Tightens security for a fraud detection pipeline.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  REVOKE SELECT ON orders FROM fraud_analyst;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  REVOKE INSERT, UPDATE ON fraud_flags FROM fraud_engineer;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  REVOKE ALL PRIVILEGES ON fraud_stats FROM fraud_report_team;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  REVOKE GRANT OPTION FOR SELECT, INSERT ON order_logs FROM team_lead;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  REVOKE DELETE ON fraud_flags FROM admin;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `REVOKE SELECT`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries with admin privileges in a local database to verify revoked permissions.
- **Combine Skills**: Mix `REVOKE ALL PRIVILEGES` and `WITH GRANT OPTION` for realistic scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore role-based access control (RBAC) in DB admin guides or interview questions.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for REVOKE permissions? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables, data, and users in your database (MySQL, PostgreSQL, or similar). Each project applies `REVOKE` permissions to these tables, testing all four concepts. Below are schemas, sample data, and user/role setups—copy-paste to create tables or save as a `.sql` file. Assume permissions from `01 GRANT` projects are initially applied for revocation.

### Dataset 1: training_data
- **Used In**: Project 1, Project 4, Project 5 (Capstone)
- **Description**: ML training data for permission revocation.
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
- **Notes**: Supports `REVOKE SELECT`, `WITH GRANT OPTION` for analyst restrictions.

### Dataset 2: predictions
- **Used In**: Project 1, Project 2, Project 5 (Capstone)
- **Description**: ML model predictions for permission revocation.
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
- **Notes**: Supports `REVOKE SELECT`, `DELETE` for model restrictions.

### Dataset 3: model_logs
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Model logs for engineer restrictions.
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
  (4, 102, 'Model deployed', '2025-08-16 14:00:00'),
  (5, 103, 'Hyperparameter tuned', '2025-08-17 11:00:00'),
  (6, 103, 'Testing started', '2025-08-17 15:00:00'),
  (7, 104, 'Prediction generated', '2025-08-18 08:00:00'),
  (8, 104, 'Model updated', '2025-08-18 16:00:00'),
  (9, 105, 'Error logged', '2025-08-19 10:30:00'),
  (10, 105, 'Retraining initiated', '2025-08-19 13:00:00'),
  (11, 106, 'Training started', '2025-08-20 09:00:00'),
  (12, 106, 'Training completed', '2025-08-20 11:00:00'),
  (13, 107, 'Validation error', '2025-08-21 10:00:00'),
  (14, 107, 'Model deployed', '2025-08-21 14:30:00'),
  (15, 108, 'Hyperparameter tuned', '2025-08-22 12:00:00'),
  (16, 108, 'Testing started', '2025-08-22 15:00:00'),
  (17, 109, 'Prediction generated', '2025-08-23 09:00:00'),
  (18, 109, 'Model updated', '2025-08-23 17:00:00'),
  (19, 110, 'Error logged', '2025-08-24 11:00:00'),
  (20, 110, 'Retraining initiated', '2025-08-24 14:00:00');
  ```
- **Notes**: Supports `REVOKE INSERT/UPDATE` for log restrictions.

### Dataset 4: model_versions
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: Model version data for developer restrictions.
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
  (1, 101, 1.0, '2025-08-15'),
  (2, 101, 1.1, '2025-08-16'),
  (3, 102, 1.0, '2025-08-17'),
  (4, 102, 1.2, '2025-08-18'),
  (5, 103, 1.0, '2025-08-19'),
  (6, 103, 1.3, '2025-08-20'),
  (7, 104, 1.0, '2025-08-21'),
  (8, 104, 1.4, '2025-08-22'),
  (9, 105, 1.0, '2025-08-23'),
  (10, 105, 1.5, '2025-08-24'),
  (11, 106, 1.0, '2025-08-25'),
  (12, 106, 1.1, '2025-08-26'),
  (13, 107, 1.0, '2025-08-27'),
  (14, 107, 1.2, '2025-08-28'),
  (15, 108, 1.0, '2025-08-29'),
  (16, 108, 1.3, '2025-08-30'),
  (17, 109, 1.0, '2025-08-31'),
  (18, 109, 1.4, '2025-09-01'),
  (19, 110, 1.0, '2025-09-02'),
  (20, 110, 1.5, '2025-09-03');
  ```
- **Notes**: Supports `REVOKE INSERT` for version restrictions.

### Dataset 5: sales_summary
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Sales summary for reporting restrictions.
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
  (1, 'North', 1600.0),
  (2, 'South', 2300.5),
  (3, 'East', 1900.0),
  (4, 'West', 2000.3),
  (5, 'North', 1800.0),
  (6, 'South', 2200.0),
  (7, 'East', 1700.5),
  (8, 'West', 2100.0),
  (9, 'North', 1500.7),
  (10, 'South', 2400.0),
  (11, 'East', 1600.0),
  (12, 'West', 1900.5),
  (13, 'North', 1700.0),
  (14, 'South', 2000.0),
  (15, 'East', 1800.3),
  (16, 'West', 2200.0),
  (17, 'North', 1400.0),
  (18, 'South', 2500.5),
  (19, 'East', 1500.0),
  (20, 'West', 2300.0);
  ```
- **Notes**: Supports `REVOKE ALL PRIVILEGES` for reporting.

### Dataset 6: model_performance
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Model performance metrics for analyst restrictions.
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
  (101, 0.90, 12),
  (102, 0.88, 10),
  (103, 0.92, 9),
  (104, 0.94, 14),
  (105, 0.89, 11),
  (106, 0.91, 8),
  (107, 0.87, 13),
  (108, 0.93, 7),
  (109, 0.86, 15),
  (110, 0.95, 10),
  (111, 0.88, 9),
  (112, 0.90, 11),
  (113, 0.92, 8),
  (114, 0.89, 12),
  (115, 0.91, 7),
  (116, 0.93, 10),
  (117, 0.87, 14),
  (118, 0.94, 6),
  (119, 0.90, 13),
  (120, 0.92, 9);
  ```
- **Notes**: Supports `REVOKE ALL PRIVILEGES` for analysis.

### Dataset 7: customer_stats
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Customer statistics for BI restrictions.
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
  (301, 6, 500.0),
  (302, 4, 350.5),
  (303, 8, 650.0),
  (304, 3, 250.0),
  (305, 5, 400.3),
  (306, 7, 550.0),
  (307, 2, 150.0),
  (308, 9, 750.5),
  (309, 4, 300.0),
  (310, 6, 450.0),
  (311, 3, 200.0),
  (312, 5, 370.5),
  (313, 7, 600.0),
  (314, 4, 320.0),
  (315, 8, 700.3),
  (316, 2, 100.0),
  (317, 6, 470.0),
  (318, 5, 390.0),
  (319, 3, 230.0),
  (320, 7, 530.5);
  ```
- **Notes**: Supports `REVOKE ALL PRIVILEGES` for reporting.

### Dataset 8: orders
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Orders for fraud detection restrictions.
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
  (102, 302, 130.5, '2025-08-16'),
  (103, 303, 20.0, '2025-08-17'),
  (104, 304, 260.0, '2025-08-18'),
  (105, 305, 70.3, '2025-08-19'),
  (106, 306, 410.0, '2025-08-20'),
  (107, 307, 35.0, '2025-08-21'),
  (108, 308, 120.7, '2025-08-22'),
  (109, 309, 80.5, '2025-08-23'),
  (110, 310, 60.0, '2025-08-24'),
  (111, 311, 210.0, '2025-08-25'),
  (112, 312, 25.0, '2025-08-26'),
  (113, 313, 170.0, '2025-08-27'),
  (114, 314, 40.0, '2025-08-28'),
  (115, 315, 100.0, '2025-08-29'),
  (116, 316, 65.5, '2025-08-30'),
  (117, 317, 190.5, '2025-08-31'),
  (118, 318, 50.0, '2025-09-01'),
  (119, 319, 110.0, '2025-09-02'),
  (120, 320, 85.0, '2025-09-03');
  ```
- **Notes**: Supports `REVOKE WITH GRANT OPTION` for delegated restrictions.

### Dataset 9: fraud_flags
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Fraud flags for permission restrictions.
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
- **Notes**: Supports `REVOKE INSERT/UPDATE`, `DELETE` for fraud restrictions.

### Dataset 10: order_logs
- **Used In**: Project 5 (Capstone)
- **Description**: Order logs for fraud restrictions.
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
  (1, 101, 'PENDING', '2025-08-15'),
  (2, 102, 'APPROVED', '2025-08-16'),
  (3, 103, 'REJECTED', '2025-08-17'),
  (4, 104, 'PENDING', '2025-08-18'),
  (5, 105, 'APPROVED', '2025-08-19'),
  (6, 106, 'REJECTED', '2025-08-20'),
  (7, 107, 'PENDING', '2025-08-21'),
  (8, 108, 'APPROVED', '2025-08-22'),
  (9, 109, 'REJECTED', '2025-08-23'),
  (10, 110, 'PENDING', '2025-08-24'),
  (11, 111, 'APPROVED', '2025-08-25'),
  (12, 112, 'REJECTED', '2025-08-26'),
  (13, 113, 'PENDING', '2025-08-27'),
  (14, 114, 'APPROVED', '2025-08-28'),
  (15, 115, 'REJECTED', '2025-08-29'),
  (16, 116, 'PENDING', '2025-08-30'),
  (17, 117, 'APPROVED', '2025-08-31'),
  (18, 118, 'REJECTED', '2025-09-01'),
  (19, 119, 'PENDING', '2025-09-02'),
  (20, 120, 'APPROVED', '2025-09-03');
  ```
- **Notes**: Supports `REVOKE SELECT/INSERT` for logging.

### Dataset 11: fraud_stats
- **Used In**: Project 5 (Capstone)
- **Description**: Fraud statistics for reporting restrictions.
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
  (301, 5, 350.0),
  (302, 3, 280.5),
  (303, 6, 450.0),
  (304, 2, 200.0),
  (305, 4, 320.3),
  (306, 1, 120.0),
  (307, 7, 550.0),
  (308, 3, 260.5),
  (309, 5, 380.0),
  (310, 2, 180.0),
  (311, 4, 400.0),
  (312, 3, 270.0),
  (313, 6, 520.0),
  (314, 1, 100.0),
  (315, 5, 420.3),
  (316, 2, 150.0),
  (317, 4, 390.0),
  (318, 3, 290.0),
  (319, 5, 370.0),
  (320, 2, 230.0);
  ```
- **Notes**: Supports `REVOKE ALL PRIVILEGES` for fraud reporting.

### User and Role Setup
- **Users**: Ensure the following users exist (from `01 GRANT` or create anew):
  ```sql
  CREATE USER IF NOT EXISTS 'analyst1'@'localhost' IDENTIFIED BY 'password1';
  CREATE USER IF NOT EXISTS 'intern'@'localhost' IDENTIFIED BY 'password2';
  CREATE USER IF NOT EXISTS 'engineer1'@'localhost' IDENTIFIED BY 'password3';
  CREATE USER IF NOT EXISTS 'developer'@'localhost' IDENTIFIED BY 'password4';
  CREATE USER IF NOT EXISTS 'scientist1'@'localhost' IDENTIFIED BY 'password5';
  CREATE USER IF NOT EXISTS 'bi_analyst'@'localhost' IDENTIFIED BY 'password6';
  CREATE USER IF NOT EXISTS 'lead1'@'localhost' IDENTIFIED BY 'password7';
  CREATE USER IF NOT EXISTS 'manager'@'localhost' IDENTIFIED BY 'password8';
  CREATE USER IF NOT EXISTS 'fraud_analyst'@'localhost' IDENTIFIED BY 'password9';
  CREATE USER IF NOT EXISTS 'fraud_engineer'@'localhost' IDENTIFIED BY 'password10';
  CREATE USER IF NOT EXISTS 'team_lead'@'localhost' IDENTIFIED BY 'password11';
  CREATE USER IF NOT EXISTS 'admin'@'localhost' IDENTIFIED BY 'password12';
  ```
- **Roles**: Ensure the following roles exist:
  ```sql
  CREATE ROLE IF NOT EXISTS data_team;
  CREATE ROLE IF NOT EXISTS ml_team;
  CREATE ROLE IF NOT EXISTS reporting_team;
  CREATE ROLE IF NOT EXISTS fraud_team;
  CREATE ROLE IF NOT EXISTS fraud_report_team;
  ```
- **Initial Permissions**: Assume permissions from `01 GRANT` projects are applied (e.g., `GRANT SELECT ON training_data TO intern`), so revocations can be tested. If starting fresh, grant permissions before revoking:
  ```sql
  GRANT SELECT ON training_data TO intern;
  GRANT SELECT ON predictions TO data_team;
  GRANT SELECT (feature1, label) ON training_data TO analyst1;
  GRANT INSERT, UPDATE ON model_logs TO engineer1;
  GRANT DELETE ON predictions TO ml_team;
  GRANT INSERT ON model_versions TO developer;
  GRANT ALL PRIVILEGES ON sales_summary TO scientist1;
  GRANT ALL PRIVILEGES ON model_performance TO reporting_team;
  GRANT ALL PRIVILEGES ON customer_stats TO bi_analyst;
  GRANT SELECT ON orders TO lead1 WITH GRANT OPTION;
  GRANT INSERT, UPDATE ON fraud_flags TO fraud_team WITH GRANT OPTION;
  GRANT ALL PRIVILEGES ON training_data TO manager WITH GRANT OPTION;
  GRANT SELECT ON orders TO fraud_analyst;
  GRANT INSERT, UPDATE ON fraud_flags TO fraud_engineer;
  GRANT ALL PRIVILEGES ON fraud_stats TO fraud_report_team;
  GRANT SELECT, INSERT ON order_logs TO team_lead WITH GRANT OPTION;
  GRANT DELETE ON fraud_flags TO admin;
  ```
- **Notes**: Requires admin privileges to manage users/roles and revoke permissions.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Set Up Users/Roles**: Execute the user and role creation commands.
3. **Apply Initial Permissions**: Run the `GRANT` statements above to set up permissions for revocation.
4. **Revoke Permissions**: Use project tasks to revoke permissions (e.g., `REVOKE SELECT`).
5. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) with admin access to test revocations.
6. **Compatibility**:
   - MySQL: Roles supported in 8.0+; use `SET ROLE` to test. Column-level revokes supported. `WITH GRANT OPTION` revocation uses `REVOKE GRANT OPTION FOR`.
   - PostgreSQL: Full support for roles and privileges; use `REVOKE ... FROM` syntax. `WITH GRANT OPTION` is `WITH ADMIN OPTION`.
   - SQL Server: Use `DATABASE ROLE` for roles; column-level revokes supported. Use `REVOKE GRANT OPTION FOR` for delegation.
7. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master REVOKE Permissions and shine in AI/ML interviews! Happy querying! ✨</p>
</div>