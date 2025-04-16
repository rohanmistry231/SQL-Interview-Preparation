# 📊 Projects - Mastering SELECT Operations

## 🌟 Overview

Welcome to the **Projects** section for **SELECT Operations**! 🚀 These five unique projects are your playground to master the nine core concepts—`Select Statement`, `Distinct`, `Where Clause`, `Like Operator`, `Wildcard Operator`, `In Operator`, `Between Operator`, `Is Null`, and `And, Or, Not`. Dive into AI/ML-themed challenges like cleaning datasets or segmenting users, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions to guide you if you’re stuck, making this perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects bring SQL to life, helping you:

- **Apply Skills**: Combine `Where Clause` and `Distinct` for real-world queries.
- **Crush Interviews**: Tackle problems like those on LeetCode or HackerRank.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Query data for model training, analysis, or preprocessing.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key SELECT operations, with a capstone combining all nine concepts. Each project has a dataset, tasks, and solutions (hidden in collapsible sections) to keep you learning and unstuck.

| Project | Concepts Covered | Description |
| --- | --- | --- |
| **Training Data Filtering** | Select Statement, Where Clause, Is Null, And, Or, Not | Filter a `training_data` table to prep clean ML data, handling nulls and logical conditions. |
| **User Segmentation** | Distinct, In Operator, And, Or, Not | Segment unique users from a `users` table for a recommendation system using filters. |
| **Order Analysis** | Select Statement, Where Clause, Between Operator, Is Null | Analyze a `customer_orders` table to identify valid orders for fraud detection. |
| **Email Pattern Matching** | Like Operator, Wildcard Operator, Distinct | Match email patterns in a `users` table to clean data for ML profiling. |
| **Capstone: Data Cleaning** | All Nine | Clean a `sales_data` table for an ML model, combining all operations for a robust dataset. |

---

## 🚀 How to Use These Projects

1. **Set Up**: See **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:    
   - Navigate to a project folder (e.g., `Project1_Training_Data_Filtering/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) to verify results.
4. **Need Help?**: Check the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Hit the capstone to flex all nine concepts together.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Where Clause`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL mastery!

---

## 📚 Project Details

### Project 1: Training Data Filtering

- **Folder**: `Project1_Training_Data_Filtering/`
- **Concepts**: `Select Statement`, `Where Clause`, `Is Null`, `And, Or, Not`
- **Description**: You’re preprocessing a `training_data` table for an ML model. Select valid rows, removing nulls and filtering with logical operators.
- **Tasks**:
  - Select all columns where `label IS NOT NULL`.
  - Filter rows with `feature1 > 0 AND label = 'positive'`.
  - Include rows with `label = 'negative' OR label = 'positive'`.
  - Exclude rows with `NOT label = 'unknown'`.
- **AI/ML Use Case**: Prepares clean data for model training.
- **Solution (Answer)**:Task 1 Solution\`\`\`sql SELECT \* FROM training_data WHERE label IS NOT NULL; \`\`\` Task 2 Solution\`\`\`sql SELECT \* FROM training_data WHERE feature1 &gt; 0 AND label = 'positive'; \`\`\` Task 3 Solution\`\`\`sql SELECT \* FROM training_data WHERE label = 'negative' OR label = 'positive'; \`\`\` Task 4 Solution\`\`\`sql SELECT \* FROM training_data WHERE NOT label = 'unknown'; \`\`\`

### Project 2: User Segmentation

- **Folder**: `Project2_User_Segmentation/`
- **Concepts**: `Distinct`, `In Operator`, `And, Or, Not`
- **Description**: Segment unique users from a `users` table for a recommendation system, filtering by regions and activity.
- **Tasks**:
  - Select unique `user_id` with `DISTINCT`.
  - Filter users with `region IN ('North', 'South')`.
  - Select active users with `activity > 3 AND region = 'North'`.
  - Exclude inactive users with `NOT activity <= 2`.
- **AI/ML Use Case**: Prepares user segments for personalized predictions.
- **Solution (Answer)**:Task 1 Solution\`\`\`sql SELECT DISTINCT user_id FROM users; \`\`\` Task 2 Solution\`\`\`sql SELECT \* FROM users WHERE region IN ('North', 'South'); \`\`\` Task 3 Solution\`\`\`sql SELECT \* FROM users WHERE activity &gt; 3 AND region = 'North'; \`\`\` Task 4 Solution\`\`\`sql SELECT \* FROM users WHERE NOT activity &lt;= 2; \`\`\`

### Project 3: Order Analysis

- **Folder**: `Project3_Order_Analysis/`
- **Concepts**: `Select Statement`, `Where Clause`, `Between Operator`, `Is Null`
- **Description**: Analyze a `customer_orders` table to identify valid orders for fraud detection, focusing on amount ranges and valid customers.
- **Tasks**:
  - Select all orders where `customer_id IS NOT NULL`.
  - Filter orders with `amount BETWEEN 10 AND 1000`.
  - Select orders with `status = 'pending' AND amount > 50`.
  - Select all columns for valid orders.
- **AI/ML Use Case**: Filters orders for fraud model training.
- **Solution (Answer)**:Task 1 Solution\`\`\`sql SELECT \* FROM customer_orders WHERE customer_id IS NOT NULL; \`\`\` Task 2 Solution\`\`\`sql SELECT \* FROM customer_orders WHERE amount BETWEEN 10 AND 1000; \`\`\` Task 3 Solution\`\`\`sql SELECT \* FROM customer_orders WHERE status = 'pending' AND amount &gt; 50; \`\`\` Task 4 Solution\`\`\`sql SELECT \* FROM customer_orders; \`\`\`

### Project 4: Email Pattern Matching

- **Folder**: `Project4_Email_Pattern_Matching/`
- **Concepts**: `Like Operator`, `Wildcard Operator`, `Distinct`
- **Description**: Match email patterns in a `users` table to clean data for ML user profiling, ensuring unique records.
- **Tasks**:
  - Select unique `email` with `DISTINCT`.
  - Find emails with `LIKE 'test%'`.
  - Match emails ending with `'%@gmail.com'`.
  - Combine patterns with `LIKE '%user%'`.
- **AI/ML Use Case**: Cleans user data for profiling models.
- **Solution (Answer)**:Task 1 Solution\`\`\`sql SELECT DISTINCT email FROM users; \`\`\` Task 2 Solution\`\`\`sql SELECT \* FROM users WHERE email LIKE 'test%'; \`\`\` Task 3 Solution\`\`\`sql SELECT \* FROM users WHERE email LIKE '%@gmail.com'; \`\`\` Task 4 Solution\`\`\`sql SELECT \* FROM users WHERE email LIKE '%user%'; \`\`\`

### Project 5: Capstone - Data Cleaning

- **Folder**: `Project5_Capstone_Data_Cleaning/`
- **Concepts**: All Nine (`Select Statement`, `Distinct`, `Where Clause`, `Like Operator`, `Wildcard Operator`, `In Operator`, `Between Operator`, `Is Null`, `And, Or, Not`)
- **Description**: Clean a `sales_data` table for an ML model, combining all operations to filter valid sales, remove duplicates, and handle edge cases.
- **Tasks**:
  - Select distinct `sale_id` with `DISTINCT`.
  - Filter `amount BETWEEN 5 AND 5000`.
  - Find `status LIKE 'complete%'` and `customer_id IS NOT NULL`.
  - Use `region IN ('East', 'West')`.
  - Combine conditions with `AND`, `OR`, `NOT` (e.g., `NOT status = 'cancelled'`).
- **AI/ML Use Case**: Produces a clean dataset for sales prediction models.
- **Solution (Answer)**:Task 1 Solution\`\`\`sql SELECT DISTINCT sale_id FROM sales_data; \`\`\` Task 2 Solution\`\`\`sql SELECT \* FROM sales_data WHERE amount BETWEEN 5 AND 5000; \`\`\` Task 3 Solution\`\`\`sql SELECT \* FROM sales_data WHERE status LIKE 'complete%' AND customer_id IS NOT NULL; \`\`\` Task 4 Solution\`\`\`sql SELECT \* FROM sales_data WHERE region IN ('East', 'West'); \`\`\` Task 5 Solution\`\`\`sql SELECT \* FROM sales_data WHERE NOT status = 'cancelled' AND (region = 'East' OR amount &gt; 100); \`\`\`

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Where Clause`.
- **Use Solutions Wisely**: Peek at answers only if stuck to keep learning fun.
- **Test in Sandbox**: Run queries in a local database to catch errors.
- **Combine Skills**: Mix `Like` and `In Operator` for realistic practice.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Explore LeetCode or HackerRank for more challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for SELECT operations? Make this section epic! 🌟

1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or similar). Each project uses one or more datasets, crafted to test all nine SELECT operations. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: training_data

- **Used In**: Project 1, Project 5 (Capstone)
- **Description**: ML training data with features and labels, including nulls and varied values for filtering.
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
  (1, 1.5, 2.3, 'positive'),
  (2, NULL, 1.8, 'negative'),
  (3, 0.7, 3.1, 'positive'),
  (4, 2.0, NULL, 'unknown'),
  (5, -1.2, 0.9, 'negative'),
  (6, 1.8, 2.7, NULL),
  (7, 0.5, 1.4, 'positive'),
  (8, NULL, 2.0, 'unknown'),
  (9, 3.0, 0.8, 'negative'),
  (10, 1.1, 1.9, 'positive'),
  (11, 0.0, 2.5, 'negative'),
  (12, 2.2, NULL, 'positive'),
  (13, -0.5, 1.6, 'unknown'),
  (14, 1.7, 2.1, 'negative'),
  (15, NULL, 0.7, 'positive'),
  (16, 0.9, 3.0, NULL),
  (17, 2.5, 1.2, 'positive'),
  (18, 1.3, 2.4, 'negative'),
  (19, 0.6, NULL, 'unknown'),
  (20, 1.9, 1.5, 'positive');
  ```
- **Notes**: Supports `Is Null` (null `feature1`), `Where Clause`/`And, Or, Not` (`label` filters), `Select Statement` (all columns).

### Dataset 2: users

- **Used In**: Project 2, Project 4, Project 5 (Capstone)
- **Description**: User data for a recommendation system, with emails and regions for pattern matching and segmentation.
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
  (1, 'test.user@gmail.com', 'North', 5),
  (2, 'john.doe@yahoo.com', 'South', 3),
  (3, 'test123@outlook.com', 'North', 7),
  (4, 'jane.smith@gmail.com', NULL, 2),
  (5, 'test.user2@gmail.com', 'South', 4),
  (6, 'alice@company.com', 'East', 6),
  (7, 'bob.test@outlook.com', 'North', 3),
  (8, 'test456@gmail.com', 'South', 5),
  (9, 'carol@company.com', NULL, 1),
  (10, 'dave.test@gmail.com', 'North', 4),
  (11, 'test789@yahoo.com', 'South', 2),
  (12, 'emma@outlook.com', 'East', 6),
  (13, 'test.user3@gmail.com', 'North', 5),
  (14, 'frank@company.com', 'South', 3),
  (15, 'test000@gmail.com', NULL, 4),
  (16, 'grace.test@outlook.com', 'West', 7),
  (17, 'test111@yahoo.com', 'North', 2),
  (18, 'henry@company.com', 'South', 5),
  (19, 'test222@gmail.com', 'East', 3),
  (20, 'ivy.test@gmail.com', 'West', 4);
  ```
- **Notes**: Enables `Distinct` (`user_id`, `email`), `In Operator` (`region`), `Like`/`Wildcard` (`email` patterns), `And, Or, Not` (`activity` filters).

### Dataset 3: customer_orders

- **Used In**: Project 3, Project 5 (Capstone)
- **Description**: Customer orders for fraud detection, with amounts and statuses for range and null checks.
- **Schema**:

  ```sql
  CREATE TABLE customer_orders (
      order_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      order_date DATE,
      status VARCHAR(50)
  );
  ```
- **Sample Data** (20 rows):

  ```sql
  INSERT INTO customer_orders (order_id, customer_id, amount, order_date, status) VALUES
  (1, 101, 50.0, '2025-01-01', 'pending'),
  (2, NULL, 150.5, '2025-01-02', 'completed'),
  (3, 102, 25.0, '2025-01-03', 'pending'),
  (4, 101, 50.0, '2025-01-04', 'cancelled'),
  (5, 103, 2000.0, '2025-01-05', 'pending'),
  (6, 104, 75.3, '2025-01-06', NULL),
  (7, NULL, 100.0, '2025-01-07', 'pending'),
  (8, 105, 30.0, '2025-01-08', 'completed'),
  (9, 101, 50.0, '2025-01-09', 'pending'),
  (10, 106, 500.5, '2025-01-10', 'pending'),
  (11, 107, 15.0, '2025-01-11', 'cancelled'),
  (12, 108, 250.0, '2025-01-12', 'pending'),
  (13, NULL, 80.0, '2025-01-13', 'completed'),
  (14, 109, 120.7, '2025-01-14', 'pending'),
  (15, 110, 45.0, '2025-01-15', NULL),
  (16, 111, 300.0, '2025-01-16', 'pending'),
  (17, NULL, 60.0, '2025-01-17', 'completed'),
  (18, 112, 90.5, '2025-01-18', 'pending'),
  (19, 113, 20.0, '2025-01-19', 'cancelled'),
  (20, 114, 150.0, '2025-01-20', 'pending');
  ```
- **Notes**: Supports `Between` (`amount`), `Is Null` (`customer_id`), `Where Clause` (`status`), `Select Statement` (all columns).

### Dataset 4: sales_data

- **Used In**: Project 5 (Capstone)
- **Description**: Sales data for an ML prediction model, with diverse fields to test all nine operations.
- **Schema**:

  ```sql
  CREATE TABLE sales_data (
      sale_id INT PRIMARY KEY,
      customer_id INT,
      amount FLOAT,
      sale_date DATE,
      status VARCHAR(50),
      region VARCHAR(50)
  );
  ```
- **Sample Data** (20 rows):

  ```sql
  INSERT INTO sales_data (sale_id, customer_id, amount, sale_date, status, region) VALUES
  (1, 201, 15.5, '2025-02-01', 'completed', 'East'),
  (2, NULL, 250.0, '2025-02-02', 'pending', 'West'),
  (3, 202, 8.0, '2025-02-03', 'completed', 'East'),
  (4, 201, 15.5, '2025-02-04', 'cancelled', NULL),
  (5, 203, 6000.0, '2025-02-05', 'pending', 'West'),
  (6, 204, 30.7, '2025-02-06', NULL, 'East'),
  (7, NULL, 100.0, '2025-02-07', 'completed', 'South'),
  (8, 205, 12.0, '2025-02-08', 'completed', 'West'),
  (9, 201, 15.5, '2025-02-09', 'pending', 'East'),
  (10, 206, 400.5, '2025-02-10', 'pending', NULL),
  (11, 207, 5.0, '2025-02-11', 'cancelled', 'West'),
  (12, 208, 200.0, '2025-02-12', 'completed', 'East'),
  (13, NULL, 50.0, '2025-02-13', 'pending', 'South'),
  (14, 209, 75.3, '2025-02-14', 'completed', 'West'),
  (15, 210, 25.0, '2025-02-15', NULL, 'East'),
  (16, 211, 300.0, '2025-02-16', 'pending', 'South'),
  (17, NULL, 40.0, '2025-02-17', 'completed', 'West'),
  (18, 212, 60.5, '2025-02-18', 'pending', 'East'),
  (19, 213, 10.0, '2025-02-19', 'cancelled', NULL),
  (20, 214, 120.0, '2025-02-20', 'completed', 'South');
  ```
- **Notes**: Enables `Distinct` (`sale_id`), `Between` (`amount`), `Like` (`status`), `In Operator` (`region`), `Is Null` (`customer_id`), `And, Or, Not` (combined filters).

### Setup Instructions

1. **Create Tables**: Run the `CREATE TABLE` statements in your database.
2. **Load Data**: Copy-paste the `INSERT` statements or save as a `.sql` file and import.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin) to avoid production risks.
4. **Compatibility**:
   - MySQL: Add `AUTO_INCREMENT` to `PRIMARY KEY` if needed (e.g., `id INT PRIMARY KEY AUTO_INCREMENT`).
   - PostgreSQL: Use `SERIAL PRIMARY KEY` for auto-incrementing IDs if preferred.
   - SQL Server: Standard syntax works; ensure date format is `YYYY-MM-DD`.
5. **Expand Data**: For more rows (up to 100), repeat similar patterns or check `Datasets/full_data.sql` (coming soon).

---

Dive into these projects to master SELECT operations and shine in AI/ML interviews! Happy querying! ✨