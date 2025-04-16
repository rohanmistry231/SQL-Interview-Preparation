# 📊 Projects - Mastering Constraints

## 🌟 Overview

Welcome to the **Projects** section for **Constraints**! 🚀 These five unique projects are your playground to master the four core concepts—`PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, and `CHECK`. Dive into AI/ML-themed challenges like enforcing dataset relationships or validating model data, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL constraints practical and fun, helping you:
- **Apply Skills**: Ensure data integrity for ML datasets with constraints.
- **Ace Interviews**: Solve schema design problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Enforce rules for model training, logging, or analysis.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key constraint techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Model Integrity** | PRIMARY KEY, FOREIGN KEY | Design tables with primary and foreign keys for ML model tracking. |
| **Dataset Relations** | FOREIGN KEY, CHECK | Create related tables with constraints for ML dataset integrity. |
| **User Uniqueness** | UNIQUE | Enforce unique constraints on user data for a recommendation system. |
| **Sales Validation** | CHECK | Apply check constraints to validate sales data for predictions. |
| **Capstone: Constraints** | All Four | Build a constrained schema for an ML fraud detection pipeline. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Model_Integrity/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `PRIMARY KEY`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Model Integrity
- **Folder**: `Project1_Model_Integrity/`
- **Concepts**: `PRIMARY KEY`, `FOREIGN KEY`
- **Description**: Design tables with primary and foreign keys to track ML models and their predictions.
- **Tasks**:
  - Create a `models` table with a `PRIMARY KEY` on `model_id`.
  - Create a `predictions` table with a `FOREIGN KEY` referencing `models`.
  - Create a `model_versions` table with a `FOREIGN KEY` to `models` and a `PRIMARY KEY` on `version_id`.
- **AI/ML Use Case**: Ensures relational integrity for model tracking.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      name VARCHAR(100),
      created_date DATE
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      eval_date DATE,
      FOREIGN KEY (model_id) REFERENCES models(model_id)
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE model_versions (
      version_id INT PRIMARY KEY,
      model_id INT,
      version_number FLOAT,
      FOREIGN KEY (model_id) REFERENCES models(model_id)
  );
  ```
  </details>

### Project 2: Dataset Relations
- **Folder**: `Project2_Dataset_Relations/`
- **Concepts**: `FOREIGN KEY`, `CHECK`
- **Description**: Create related tables with constraints to ensure ML dataset integrity.
- **Tasks**:
  - Create a `datasets` table with a `PRIMARY KEY` and a `CHECK` on `size_mb`.
  - Create a `training_data` table with a `FOREIGN KEY` to `datasets`.
  - Create a `test_data` table with a `CHECK` on `confidence` and a `FOREIGN KEY` to `datasets`.
- **AI/ML Use Case**: Maintains valid relationships for training datasets.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE datasets (
      dataset_id INT PRIMARY KEY,
      name VARCHAR(100),
      size_mb INT,
      CHECK (size_mb > 0)
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE training_data (
      record_id INT PRIMARY KEY,
      dataset_id INT,
      feature1 FLOAT,
      label VARCHAR(50),
      FOREIGN KEY (dataset_id) REFERENCES datasets(dataset_id)
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE test_data (
      record_id INT PRIMARY KEY,
      dataset_id INT,
      feature1 FLOAT,
      confidence FLOAT,
      FOREIGN KEY (dataset_id) REFERENCES datasets(dataset_id),
      CHECK (confidence BETWEEN 0 AND 1)
  );
  ```
  </details>

### Project 3: User Uniqueness
- **Folder**: `Project3_User_Uniqueness/`
- **Concepts**: `UNIQUE`
- **Description**: Enforce unique constraints on user data for a recommendation system.
- **Tasks**:
  - Create a `users` table with a `UNIQUE` constraint on `email`.
  - Create a `user_profiles` table with a `UNIQUE` pair of `user_id` and `profile_tag`.
  - Create a `user_logins` table with a `UNIQUE` constraint on `login_token`.
- **AI/ML Use Case**: Ensures distinct user data for personalization models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE users (
      user_id INT PRIMARY KEY,
      email VARCHAR(100) UNIQUE,
      region VARCHAR(50)
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE user_profiles (
      profile_id INT PRIMARY KEY,
      user_id INT,
      profile_tag VARCHAR(50),
      UNIQUE (user_id, profile_tag)
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE user_logins (
      login_id INT PRIMARY KEY,
      user_id INT,
      login_token VARCHAR(100) UNIQUE,
      login_date DATE
  );
  ```
  </details>

### Project 4: Sales Validation
- **Folder**: `Project4_Sales_Validation/`
- **Concepts**: `CHECK`
- **Description**: Apply check constraints to validate sales data for ML prediction models.
- **Tasks**:
  - Create a `sales_data` table with a `CHECK` on `amount` to ensure positive values.
  - Create a `sales_regions` table with a `CHECK` on `region` for valid values.
  - Create a `sales_logs` table with a `CHECK` on `log_level` (e.g., 'INFO', 'ERROR').
- **AI/ML Use Case**: Validates sales data for forecasting accuracy.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE sales_data (
      sale_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      sale_date DATE,
      CHECK (amount > 0)
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE sales_regions (
      region_id INT PRIMARY KEY,
      region VARCHAR(50),
      CHECK (region IN ('North', 'South', 'East', 'West'))
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE sales_logs (
      log_id INT PRIMARY KEY,
      sale_id INT,
      log_level VARCHAR(50),
      log_message VARCHAR(255),
      CHECK (log_level IN ('INFO', 'ERROR', 'WARNING'))
  );
  ```
  </details>

### Project 5: Capstone - Constraints
- **Folder**: `Project5_Capstone_Constraints/`
- **Concepts**: All Four (`PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `CHECK`)
- **Description**: Build a constrained schema for an ML fraud detection pipeline.
- **Tasks**:
  - Create a `orders` table with a `PRIMARY KEY` and a `CHECK` on `amount`.
  - Create a `fraud_flags` table with a `FOREIGN KEY` to `orders` and a `UNIQUE` constraint on `flag_id`.
  - Create a `customers` table with a `UNIQUE` constraint on `email`.
  - Create a `order_logs` table with a `FOREIGN KEY` to `orders` and a `CHECK` on `status`.
  - Create a `fraud_summary` table with a `PRIMARY KEY` and a `UNIQUE` pair of `customer_id` and `analysis_date`.
- **AI/ML Use Case**: Ensures robust data integrity for fraud analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      order_date DATE,
      CHECK (amount >= 0)
  );
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE TABLE fraud_flags (
      flag_id INT PRIMARY KEY UNIQUE,
      order_id INT,
      flag_reason VARCHAR(100),
      FOREIGN KEY (order_id) REFERENCES orders(order_id)
  );
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      email VARCHAR(100) UNIQUE,
      name VARCHAR(100)
  );
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  CREATE TABLE order_logs (
      log_id INT PRIMARY KEY,
      order_id INT,
      status VARCHAR(50),
      log_date DATE,
      FOREIGN KEY (order_id) REFERENCES orders(order_id),
      CHECK (status IN ('PENDING', 'APPROVED', 'REJECTED'))
  );
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  CREATE TABLE fraud_summary (
      summary_id INT PRIMARY KEY,
      customer_id INT,
      analysis_date DATE,
      risk_score FLOAT,
      UNIQUE (customer_id, analysis_date)
  );
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `PRIMARY KEY`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch constraint violations.
- **Combine Skills**: Mix `FOREIGN KEY` and `CHECK` for realistic schemas.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more schema challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for constraints? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project creates new tables with constraints, but some rely on existing tables for context or relationships. Below are schemas and sample data for input tables—copy-paste to create tables or save as a `.sql` file. Output tables are created via project tasks.

### Dataset 1: models
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML model metadata for constraint application.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      name VARCHAR(100),
      created_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO models (model_id, name, created_date) VALUES
  (101, 'Classifier_A', '2025-06-01'),
  (102, 'Regressor_B', '2025-06-02'),
  (103, 'Cluster_C', '2025-06-03'),
  (104, 'NN_D', '2025-06-04'),
  (105, 'Tree_E', '2025-06-05'),
  (106, 'SVM_F', '2025-06-06'),
  (107, 'Boost_G', '2025-06-07'),
  (108, 'RF_H', '2025-06-08'),
  (109, 'KNN_I', '2025-06-09'),
  (110, 'LR_J', '2025-06-10'),
  (111, 'Classifier_K', '2025-06-11'),
  (112, 'Regressor_L', '2025-06-12'),
  (113, 'Cluster_M', '2025-06-13'),
  (114, 'NN_N', '2025-06-14'),
  (115, 'Tree_O', '2025-06-15'),
  (116, 'SVM_P', '2025-06-16'),
  (117, 'Boost_Q', '2025-06-17'),
  (118, 'RF_R', '2025-06-18'),
  (119, 'KNN_S', '2025-06-19'),
  (120, 'LR_T', '2025-06-20');
  ```
- **Notes**: Provides `PRIMARY KEY` for `FOREIGN KEY` references in `predictions`, `model_versions`.

### Dataset 2: datasets
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: ML dataset metadata for relational constraints.
- **Schema**:
  ```sql
  CREATE TABLE datasets (
      dataset_id INT PRIMARY KEY,
      name VARCHAR(100),
      size_mb INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO datasets (dataset_id, name, size_mb) VALUES
  (1, 'Fraud_Dataset', 150),
  (2, 'Sales_Dataset', 200),
  (3, 'User_Dataset', 100),
  (4, 'Image_Dataset', 500),
  (5, 'Text_Dataset', 80),
  (6, 'Click_Dataset', 120),
  (7, 'Sensor_Dataset', 300),
  (8, 'Log_Dataset', 90),
  (9, 'Review_Dataset', 110),
  (10, 'Traffic_Dataset', 250),
  (11, 'Health_Dataset', 140),
  (12, 'Retail_Dataset', 180),
  (13, 'Weather_Dataset', 70),
  (14, 'Finance_Dataset', 220),
  (15, 'Social_Dataset', 130),
  (16, 'Game_Dataset', 160),
  (17, 'Ad_Dataset', 95),
  (18, 'Video_Dataset', 400),
  (19, 'Audio_Dataset', 85),
  (20, 'Event_Dataset', 175);
  ```
- **Notes**: Supports `FOREIGN KEY` in `training_data`, `test_data`.

### Dataset 3: users
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: User data for unique constraints.
- **Schema**:
  ```sql
  CREATE TABLE users (
      user_id INT PRIMARY KEY,
      email VARCHAR(100),
      region VARCHAR(50)
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO users (user_id, email, region) VALUES
  (101, 'john@gmail.com', 'North'),
  (102, 'jane@yahoo.com', 'South'),
  (103, 'mike@outlook.com', 'East'),
  (104, 'sara@gmail.com', 'West'),
  (105, 'tom@company.com', 'North'),
  (106, 'lisa@yahoo.com', 'South'),
  (107, 'mark@outlook.com', 'East'),
  (108, 'anna@gmail.com', 'West'),
  (109, 'paul@company.com', 'North'),
  (110, 'emma@yahoo.com', 'South'),
  (111, 'david@outlook.com', 'East'),
  (112, 'clara@gmail.com', 'West'),
  (113, 'steve@company.com', 'North'),
  (114, 'lucy@yahoo.com', 'South'),
  (115, 'peter@outlook.com', 'East'),
  (116, 'mary@gmail.com', 'West'),
  (117, 'nick@company.com', 'North'),
  (118, 'zoe@yahoo.com', 'South'),
  (119, 'ben@outlook.com', 'East'),
  (120, 'kate@gmail.com', 'West'),
  (121, 'lily@company.com', 'North'),
  (122, 'jack@yahoo.com', 'South'),
  (123, 'rose@outlook.com', 'East'),
  (124, 'sam@gmail.com', 'West'),
  (125, 'tina@company.com', 'North');
  ```
- **Notes**: Provides base data for `UNIQUE` constraints on `email`, `profile_tag`.

### Dataset 4: orders
- **Used In**: Project 5 (Capstone)
- **Description**: Order data for fraud detection constraints.
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
  (101, 301, 80.0, '2025-07-01'),
  (102, 302, 120.5, '2025-07-02'),
  (103, 303, 15.0, '2025-07-03'),
  (104, 304, 250.0, '2025-07-04'),
  (105, 305, 65.3, '2025-07-05'),
  (106, 306, 400.0, '2025-07-06'),
  (107, 307, 30.0, '2025-07-07'),
  (108, 308, 110.7, '2025-07-08'),
  (109, 309, 70.5, '2025-07-09'),
  (110, 310, 50.0, '2025-07-10'),
  (111, 311, 200.0, '2025-07-11'),
  (112, 312, 20.0, '2025-07-12'),
  (113, 313, 160.0, '2025-07-13'),
  (114, 314, 35.0, '2025-07-14'),
  (115, 315, 90.0, '2025-07-15'),
  (116, 316, 60.5, '2025-07-16'),
  (117, 317, 180.5, '2025-07-17'),
  (118, 318, 45.0, '2025-07-18'),
  (119, 319, 100.0, '2025-07-19'),
  (120, 320, 75.0, '2025-07-20');
  ```
- **Notes**: Supports `FOREIGN KEY`, `CHECK` in fraud-related tables.

### Setup Instructions
1. **Create Input Tables**: Run the `CREATE TABLE` and `INSERT` statements for `models`, `datasets`, `users`, and `orders`.
2. **Generate Output Tables**: Use project tasks to create constrained tables (e.g., `predictions`, `sales_data`).
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to test constraint enforcement.
4. **Compatibility**:
   - MySQL: `CHECK` constraints supported in 8.0+; use `INT` for `BOOLEAN` (0/1).
   - PostgreSQL: Full support for all constraints; `BOOLEAN` is native.
   - SQL Server: `CHECK` syntax standard; use `BIT` for `BOOLEAN`.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master Constraints and shine in AI/ML interviews! Happy querying! ✨</p>
</div>