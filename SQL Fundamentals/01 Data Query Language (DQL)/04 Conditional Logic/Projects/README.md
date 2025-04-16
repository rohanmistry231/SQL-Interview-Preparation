# 📊 Projects - Mastering Conditional Logic

## 🌟 Overview

Welcome to the **Projects** section for **Conditional Logic**! 🚀 These five unique projects are your playground to master the four core concepts—`CASE Statement`, `COALESCE`, `NULLIF`, and `IF`. Dive into AI/ML-themed challenges like categorizing data or handling nulls, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL conditional logic practical and fun, helping you:
- **Apply Skills**: Use `CASE` and `COALESCE` for ML data preprocessing.
- **Ace Interviews**: Solve problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Transform data for model training, profiling, or analysis.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key conditional logic techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Data Categorization** | CASE Statement, IF | Categorize `training_data` rows based on features for ML model preparation. |
| **Null Handling** | COALESCE, NULLIF | Clean null values in a `users` table for consistent ML profiling. |
| **Feature Adjustment** | CASE Statement, COALESCE | Adjust `predictions` features using conditionals for model evaluation. |
| **User Profiling** | CASE Statement, IF | Profile users in a `customers` table with conditional logic for segmentation. |
| **Capstone: Preprocessing** | All Four | Preprocess `sales_data` for an ML model, combining all conditional techniques. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Data_Categorization/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `CASE Statement`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Data Categorization
- **Folder**: `Project1_Data_Categorization/`
- **Concepts**: `CASE Statement`, `IF`
- **Description**: Categorize rows in a `training_data` table based on feature values to prepare data for an ML model.
- **Tasks**:
  - Use `CASE` to categorize `feature1` into ‘Low’ (< 1), ‘Medium’ (1-2), or ‘High’ (> 2).
  - Create a column with `IF` to label rows as ‘Valid’ if `label` is not null, else ‘Invalid’.
  - Combine `CASE` to flag rows where `feature2` > 2 as ‘Outlier’, else ‘Normal’.
- **AI/ML Use Case**: Prepares categorized features for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT id, feature1,
         CASE
             WHEN feature1 < 1 THEN 'Low'
             WHEN feature1 BETWEEN 1 AND 2 THEN 'Medium'
             ELSE 'High'
         END AS feature1_category
  FROM training_data;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT id, label,
         IF(label IS NOT NULL, 'Valid', 'Invalid') AS validity
  FROM training_data;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT id, feature2,
         CASE
             WHEN feature2 > 2 THEN 'Outlier'
             ELSE 'Normal'
         END AS feature2_status
  FROM training_data;
  ```
  </details>

### Project 2: Null Handling
- **Folder**: `Project2_Null_Handling/`
- **Concepts**: `COALESCE`, `NULLIF`
- **Description**: Clean null values in a `users` table to ensure consistent data for ML user profiling.
- **Tasks**:
  - Use `COALESCE` to replace null `region` with ‘Unknown’.
  - Apply `NULLIF` to set `activity` to null if it equals 0.
  - Combine `COALESCE` and `NULLIF` to handle null `email` and empty `email` strings.
- **AI/ML Use Case**: Ensures clean user data for recommendation models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT user_id, COALESCE(region, 'Unknown') AS region
  FROM users;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT user_id, NULLIF(activity, 0) AS activity
  FROM users;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT user_id, COALESCE(NULLIF(email, ''), 'no_email') AS email
  FROM users;
  ```
  </details>

### Project 3: Feature Adjustment
- **Folder**: `Project3_Feature_Adjustment/`
- **Concepts**: `CASE Statement`, `COALESCE`
- **Description**: Adjust features in a `predictions` table using conditionals to standardize data for model evaluation.
- **Tasks**:
  - Use `CASE` to scale `score` to ‘High’ (> 0.9), ‘Medium’ (0.8-0.9), or ‘Low’ (< 0.8).
  - Apply `COALESCE` to replace null `score` with 0.
  - Combine `CASE` and `COALESCE` to categorize non-null `score` values.
- **AI/ML Use Case**: Standardizes model outputs for performance analysis.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT model_id, score,
         CASE
             WHEN score > 0.9 THEN 'High'
             WHEN score BETWEEN 0.8 AND 0.9 THEN 'Medium'
             ELSE 'Low'
         END AS score_category
  FROM predictions;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT model_id, COALESCE(score, 0) AS score
  FROM predictions;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT model_id, COALESCE(score, 0) AS score,
         CASE
             WHEN COALESCE(score, 0) > 0.9 THEN 'High'
             WHEN COALESCE(score, 0) BETWEEN 0.8 AND 0.9 THEN 'Medium'
             ELSE 'Low'
         END AS score_category
  FROM predictions;
  ```
  </details>

### Project 4: User Profiling
- **Folder**: `Project4_User_Profiling/`
- **Concepts**: `CASE Statement`, `IF`
- **Description**: Profile users in a `customers` table with conditional logic to segment them for an ML model.
- **Tasks**:
  - Use `CASE` to categorize `activity` into ‘Active’ (> 5), ‘Moderate’ (3-5), or ‘Inactive’ (< 3).
  - Apply `IF` to flag customers with `name` not null as ‘Known’, else ‘Unknown’.
  - Combine `CASE` to profile customers with high `activity` as ‘VIP’, else ‘Standard’.
- **AI/ML Use Case**: Segments customers for targeted ML predictions.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT customer_id, activity,
         CASE
             WHEN activity > 5 THEN 'Active'
             WHEN activity BETWEEN 3 AND 5 THEN 'Moderate'
             ELSE 'Inactive'
         END AS activity_level
  FROM customers;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT customer_id, name,
         IF(name IS NOT NULL, 'Known', 'Unknown') AS name_status
  FROM customers;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT customer_id, activity,
         CASE
             WHEN activity > 5 THEN 'VIP'
             ELSE 'Standard'
         END AS customer_type
  FROM customers;
  ```
  </details>

### Project 5: Capstone - Preprocessing
- **Folder**: `Project5_Capstone_Preprocessing/`
- **Concepts**: All Four (`CASE Statement`, `COALESCE`, `NULLIF`, `IF`)
- **Description**: Preprocess `sales_data` for an ML model, combining all conditional techniques to clean and categorize sales records.
- **Tasks**:
  - Use `CASE` to categorize `amount` into ‘Small’ (< 50), ‘Medium’ (50-200), or ‘Large’ (> 200).
  - Apply `COALESCE` to replace null `region` with ‘Unknown’.
  - Use `NULLIF` to set `amount` to null if it equals 0.
  - Apply `IF` to flag sales with non-null `customer_id` as ‘Valid’, else ‘Invalid’.
  - Combine all to categorize and clean `amount` and `region`.
- **AI/ML Use Case**: Prepares clean, categorized data for sales prediction models.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  SELECT sale_id, amount,
         CASE
             WHEN amount < 50 THEN 'Small'
             WHEN amount BETWEEN 50 AND 200 THEN 'Medium'
             ELSE 'Large'
         END AS amount_category
  FROM sales_data;
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  SELECT sale_id, COALESCE(region, 'Unknown') AS region
  FROM sales_data;
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  SELECT sale_id, NULLIF(amount, 0) AS amount
  FROM sales_data;
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  SELECT sale_id, customer_id,
         IF(customer_id IS NOT NULL, 'Valid', 'Invalid') AS validity
  FROM sales_data;
  ```
  </details>
  <details>
  <summary>Task 5 Solution</summary>
  ```sql
  SELECT sale_id, customer_id,
         COALESCE(NULLIF(amount, 0), 0) AS cleaned_amount,
         COALESCE(region, 'Unknown') AS cleaned_region,
         CASE
             WHEN COALESCE(NULLIF(amount, 0), 0) < 50 THEN 'Small'
             WHEN COALESCE(NULLIF(amount, 0), 0) BETWEEN 50 AND 200 THEN 'Medium'
             ELSE 'Large'
         END AS amount_category,
         IF(customer_id IS NOT NULL, 'Valid', 'Invalid') AS validity
  FROM sales_data;
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `CASE Statement`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix `COALESCE` and `CASE` for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for conditional logic? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all four conditional logic concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: training_data
- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML training data with features and labels for categorization.
- **Schema**:
  ```sql
  CREATE TABLE training_data (
      id INT PRIMARY KEY,
      feature1 FLOAT,
      feature2 FLOAT,
      label VARCHAR(50)
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO training_data (id, feature1, feature2, label) VALUES
  (1, 0.5, 1.8, 'positive'),
  (2, 1.2, 2.5, NULL),
  (3, 2.3, 3.1, 'negative'),
  (4, 0.8, 1.4, 'positive'),
  (5, 1.9, 2.9, 'negative'),
  (6, 0.3, 1.7, NULL),
  (7, 2.1, 3.4, 'positive'),
  (8, 1.0, 2.0, 'negative'),
  (9, 1.6, 2.6, 'positive'),
  (10, 0.7, 1.9, NULL),
  (11, 2.4, 3.2, 'negative'),
  (12, 0.9, 1.5, 'positive'),
  (13, 1.8, 2.8, 'negative'),
  (14, 0.4, 1.3, 'positive'),
  (15, 2.0, 3.0, NULL),
  (16, 1.1, 2.4, 'positive'),
  (17, 0.6, 1.6, 'negative'),
  (18, 2.2, 3.3, 'positive'),
  (19, 0.8, 1.8, NULL),
  (20, 1.7, 2.7, 'negative'),
  (21, 0.5, 1.9, 'positive'),
  (22, 2.5, 3.5, 'negative'),
  (23, 1.3, 2.2, 'positive'),
  (24, 0.9, 1.4, NULL),
  (25, 1.5, 2.5, 'positive');
  ```
- **Notes**: Supports `CASE` (feature categorization), `IF` (null checks).

### Dataset 2: users
- **Used In**: Project 2, Project 5 (Capstone)
- **Description**: User data for null handling and profiling.
- **Schema**:
  ```sql
  CREATE TABLE users (
      user_id INT PRIMARY KEY,
      email VARCHAR(100),
      region VARCHAR(50),
      activity INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO users (user_id, email, region, activity) VALUES
  (1, 'alice@gmail.com', NULL, 5),
  (2, '', 'South', 0),
  (3, 'carol@outlook.com', 'East', 3),
  (4, 'dave@gmail.com', 'West', 2),
  (5, NULL, 'North', 7),
  (6, 'frank@company.com', NULL, 4),
  (7, 'grace@gmail.com', 'East', 6),
  (8, '', 'West', 0),
  (9, 'ivy@yahoo.com', 'North', 5),
  (10, 'jack@gmail.com', 'South', 3),
  (11, NULL, 'East', 2),
  (12, 'liam@outlook.com', NULL, 4),
  (13, 'mia@gmail.com', 'North', 6),
  (14, 'noah@yahoo.com', 'South', 0),
  (15, 'olivia@company.com', 'West', 5),
  (16, '', NULL, 3),
  (17, 'quinn@outlook.com', 'North', 7),
  (18, 'rose@yahoo.com', 'South', 2),
  (19, NULL, 'East', 4),
  (20, 'tina@gmail.com', 'West', 6);
  ```
- **Notes**: Supports `COALESCE` (null `region`, `email`), `NULLIF` (zero `activity`).

### Dataset 3: predictions
- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: ML model predictions for feature adjustment.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      model_id INT PRIMARY KEY,
      score FLOAT,
      eval_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO predictions (model_id, score, eval_date) VALUES
  (1, 0.95, '2025-06-01'),
  (2, NULL, '2025-06-01'),
  (3, 0.88, '2025-06-02'),
  (4, 0.76, '2025-06-02'),
  (5, 0.91, '2025-06-03'),
  (6, 0.85, '2025-06-03'),
  (7, NULL, '2025-06-04'),
  (8, 0.80, '2025-06-04'),
  (9, 0.89, '2025-06-05'),
  (10, 0.93, '2025-06-05'),
  (11, 0.78, '2025-06-06'),
  (12, NULL, '2025-06-06'),
  (13, 0.84, '2025-06-07'),
  (14, 0.90, '2025-06-07'),
  (15, 0.87, '2025-06-08'),
  (16, 0.94, '2025-06-08'),
  (17, NULL, '2025-06-09'),
  (18, 0.79, '2025-06-09'),
  (19, 0.86, '2025-06-10'),
  (20, 0.91, '2025-06-10');
  ```
- **Notes**: Supports `CASE` (score categorization), `COALESCE` (null scores).

### Dataset 4: customers
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Customer data for profiling and segmentation.
- **Schema**:
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      name VARCHAR(100),
      activity INT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO customers (customer_id, name, activity) VALUES
  (101, 'Alice Smith', 6),
  (102, NULL, 2),
  (103, 'Carol White', 4),
  (104, 'Dave Brown', 1),
  (105, 'Emma Davis', 7),
  (106, 'Frank Wilson', 3),
  (107, NULL, 5),
  (108, 'Henry Clark', 0),
  (109, 'Ivy Taylor', 6),
  (110, 'Jack Moore', 2),
  (111, 'Kate Adams', 4),
  (112, NULL, 3),
  (113, 'Mia Lewis', 8),
  (114, 'Noah Walker', 1),
  (115, 'Olivia Young', 5),
  (116, 'Peter King', 2),
  (117, NULL, 6),
  (118, 'Rose Hall', 3),
  (119, 'Sam Green', 7),
  (120, 'Tina Baker', 4);
  ```
- **Notes**: Supports `CASE` (activity profiling), `IF` (null name checks).

### Dataset 5: sales_data
- **Used In**: Project 5 (Capstone)
- **Description**: Sales data for comprehensive preprocessing.
- **Schema**:
  ```sql
  CREATE TABLE sales_data (
      sale_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      sale_date DATE,
      region VARCHAR(50)
  );
  ```
- **Sample Data** (25 rows):
  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date, region) VALUES
  (1, 201, 15.5, '2025-07-01', NULL),
  (2, NULL, 250.0, '2025-07-02', 'West'),
  (3, 202, 0.0, '2025-07-03', 'East'),
  (4, 203, 100.0, '2025-07-04', NULL),
  (5, 204, 30.7, '2025-07-05', 'South'),
  (6, NULL, 12.0, '2025-07-06', 'West'),
  (7, 205, 400.5, '2025-07-07', NULL),
  (8, 206, 0.0, '2025-07-08', 'East'),
  (9, 207, 200.0, '2025-07-09', 'South'),
  (10, NULL, 50.0, '2025-07-10', 'West'),
  (11, 208, 75.3, '2025-07-11', NULL),
  (12, 209, 300.0, '2025-07-12', 'East'),
  (13, 210, 40.0, '2025-07-13', 'South'),
  (14, NULL, 120.7, '2025-07-14', 'West'),
  (15, 211, 60.0, '2025-07-15', NULL),
  (16, 212, 90.5, '2025-07-16', 'East'),
  (17, NULL, 0.0, '2025-07-17', 'South'),
  (18, 213, 20.0, '2025-07-18', 'West'),
  (19, 214, 80.0, '2025-07-19', NULL),
  (20, 215, 110.0, '2025-07-20', 'East'),
  (21, NULL, 65.0, '2025-07-21', 'South'),
  (22, 216, 175.0, '2025-07-22', 'West'),
  (23, 217, 35.0, '2025-07-23', NULL),
  (24, 218, 95.0, '2025-07-24', 'East'),
  (25, NULL, 150.0, '2025-07-25', 'South');
  ```
- **Notes**: Supports all concepts (`CASE`, `COALESCE`, `NULLIF`, `IF`) for cleaning and categorization.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` statements in your database.
2. **Load Data**: Copy-paste the `INSERT` statements or save as a `.sql` file and import.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to avoid production risks.
4. **Compatibility**:
   - MySQL: Add `AUTO_INCREMENT` to `PRIMARY KEY` if needed (e.g., `id INT PRIMARY KEY AUTO_INCREMENT`). Use `IF` via `CASE` if needed.
   - PostgreSQL: Use `SERIAL PRIMARY KEY` for IDs. `IF` not native; use `CASE`.
   - SQL Server: Use `IIF` for `IF`. Standard syntax for others.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

<div align="center">
  <p>Dive into these projects to master Conditional Logic and shine in AI/ML interviews! Happy querying! ✨</p>
</div>