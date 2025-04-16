# 📊 Projects - Mastering SQL Indexing

## 🌟 Overview

Welcome to the **Projects** section for **SQL Indexing**! 🚀 These five unique projects are your sandbox to master four core concepts—`Creating Indexes`, `B-Tree Indexes`, `Hash Indexes`, and `Specialty Indexes`. Dive into AI/ML-themed challenges like optimizing feature lookups, speeding up spatial ML queries, or powering NLP searches, designed to get your hands dirty and prep you for interviews. Each project includes tasks, datasets, and solutions (hidden in collapsible sections) to keep you learning and unstuck, perfect for your Machine Learning journey and portfolio.

---

## 🎯 Why Projects?

Projects make SQL indexing practical and fun, helping you:
- **Apply Skills**: Optimize ML dataset queries for lightning-fast performance.
- **Ace Interviews**: Solve real-world optimization problems like those in FAANG tests.
- **Build Portfolio**: Showcase SQL in your *ML-Interview-Preparation-Hub* for recruiters.
- **Power AI/ML**: Speed up feature retrieval, spatial analysis, and text search for insights.

---

## 🗺️ Projects Roadmap

Here are five projects, each targeting key indexing techniques, with a capstone combining all four concepts. Each project has a dataset, tasks, and solutions to guide you.

| Project | Concepts Covered | Description |
|---------|------------------|-------------|
| **Feature Indexer** | Creating Indexes | Optimize feature table queries with indexes. |
| **Prediction Ranger** | B-Tree Indexes | Speed up range and join queries for predictions. |
| **Model Lookup** | Hash Indexes | Accelerate exact-match model queries. |
| **Spatial Text Searcher** | Specialty Indexes | Boost spatial and text searches for ML. |
| **Capstone: Indexing** | All Four | Build a full ML pipeline with optimized indexes. |

---

## 🚀 How to Use These Projects

1. **Set Up**: Check **Dataset & Database Details** below to create tables and load data.
2. **Get Started**:
   - Navigate to a project folder (e.g., `Project1_Feature_Indexer/`).
   - Read its `README.md` for the problem and tasks.
   - Write SQL index queries to solve each task.
3. **Test Queries**: Run in a sandbox (MySQL, PostgreSQL, etc.) with `EXPLAIN` to verify performance gains.
4. **Need Help?**: Peek at the **Solution (Answer)** in each project’s description (hidden in `<details>` tags).
5. **Go Big**: Tackle the capstone to flex all four concepts.
6. **Show Off**: Push solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Project1` to nail `Creating Indexes`, use solutions sparingly, and conquer the capstone to impress interviewers with your SQL optimization mastery!

---

## 📚 Project Details

### Project 1: Feature Indexer
- **Folder**: `Project1_Feature_Indexer/`
- **Concepts**: `Creating Indexes`
- **Description**: Optimize queries on a feature table for ML preprocessing by creating indexes.
- **Tasks**:
  - Create a multi-column index on `features` to speed up `SELECT * FROM features WHERE user_id = 12345 AND model_id = 101`.
  - Verify the index improves performance using `EXPLAIN`.
- **AI/ML Use Case**: Accelerates feature retrieval for model training.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE INDEX idx_user_model ON features (user_id, model_id);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  EXPLAIN SELECT * FROM features WHERE user_id = 12345 AND model_id = 101;
  ```
  </details>

### Project 2: Prediction Ranger
- **Folder**: `Project2_Prediction_Ranger/`
- **Concepts**: `B-Tree Indexes`
- **Description**: Speed up range and join queries on predictions for ML analysis using B-Tree indexes.
- **Tasks**:
  - Create a B-Tree index on `predictions` to optimize `SELECT * FROM predictions WHERE prediction_date BETWEEN '2025-08-01' AND '2025-08-31' ORDER BY score DESC`.
  - Create a B-Tree index on `models` for `SELECT p.* FROM predictions p JOIN models m ON p.model_id = m.model_id WHERE m.created_date > '2025-08-01'`.
- **AI/ML Use Case**: Boosts time-based prediction queries and model joins.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE INDEX idx_pred_date_score ON predictions USING btree (prediction_date, score);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE INDEX idx_model_date ON models USING btree (created_date, model_id);
  ```
  </details>

### Project 3: Model Lookup
- **Folder**: `Project3_Model_Lookup/`
- **Concepts**: `Hash Indexes`
- **Description**: Accelerate exact-match queries for model-specific predictions using Hash indexes in PostgreSQL.
- **Tasks**:
  - Create a Hash index on `predictions` to optimize `SELECT * FROM predictions WHERE model_id = 102`.
  - Verify the index with `EXPLAIN`.
- **AI/ML Use Case**: Speeds up model-specific inference queries.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE INDEX idx_model_id_hash ON predictions USING hash (model_id);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  EXPLAIN SELECT * FROM predictions WHERE model_id = 102;
  ```
  </details>

### Project 4: Spatial Text Searcher
- **Folder**: `Project4_Spatial_Text_Searcher/`
- **Concepts**: `Specialty Indexes`
- **Description**: Boost spatial and text searches for ML datasets using R-Tree and Full-Text indexes.
- **Tasks**:
  - Create an R-Tree index on `locations` in PostgreSQL (with PostGIS) to optimize `SELECT * FROM locations WHERE ST_Within(geog, ST_MakeEnvelope(-74, 40, -73, 41))`.
  - Create a Full-Text index on `documents` in MySQL to speed up `SELECT * FROM documents WHERE MATCH(content) AGAINST('machine learning')`.
- **AI/ML Use Case**: Enhances geospatial ML and NLP data queries.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE INDEX idx_location ON locations USING gist (geog);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE FULLTEXT INDEX idx_content ON documents (content);
  ```
  </details>

### Project 5: Capstone - Indexing
- **Folder**: `Project5_Capstone_Indexing/`
- **Concepts**: All Four (`Creating Indexes`, `B-Tree Indexes`, `Hash Indexes`, `Specialty Indexes`)
- **Description**: Build a full ML pipeline with optimized indexes for predictions, features, and spatial data.
- **Tasks**:
  - Create a unique index on `features.user_id` to ensure data integrity.
  - Create a B-Tree index on `predictions` for `SELECT * FROM predictions WHERE score > 0.9 ORDER BY prediction_date`.
  - Create a Hash index on `features` for `SELECT * FROM features WHERE model_id = 101` in PostgreSQL.
  - Create an R-Tree index on `locations` for `SELECT * FROM locations WHERE ST_DWithin(geog, ST_GeogFromText('POINT(-73.95 40.75)'), 1000)`.
- **AI/ML Use Case**: Optimizes a real-time ML pipeline for feature retrieval, prediction analysis, and geospatial queries.
- **Solution (Answer)**:
  <details>
  <summary>Task 1 Solution</summary>
  ```sql
  CREATE UNIQUE INDEX idx_unique_user ON features (user_id);
  ```
  </details>
  <details>
  <summary>Task 2 Solution</summary>
  ```sql
  CREATE INDEX idx_score_date ON predictions USING btree (score, prediction_date);
  ```
  </details>
  <details>
  <summary>Task 3 Solution</summary>
  ```sql
  CREATE INDEX idx_model_id_hash ON features USING hash (model_id);
  ```
  </details>
  <details>
  <summary>Task 4 Solution</summary>
  ```sql
  CREATE INDEX idx_location_dist ON locations USING gist (geog);
  ```
  </details>

---

## 💡 Tips for Success

- **Start Easy**: Try `Project1` to get comfy with `Creating Indexes`.
- **Use Solutions Sparingly**: Peek only if stuck to keep learning fun.
- **Test in Sandbox**: Run indexes in a local database (MySQL, PostgreSQL) and use `EXPLAIN` to verify speedup.
- **Combine Skills**: Mix indexing with joins, procedures, or triggers (from `06 Joins and Aggregations`, `07 Stored Procedures`, `08 Triggers`) for realistic ML scenarios.
- **Save Work**: Store scripts in your portfolio for recruiters.
- **Level Up**: Experiment with partial indexes or index maintenance (e.g., `REINDEX`) for advanced challenges.

---

## 🤝 Contribute to the Projects

Got a fresh SQL project idea for indexing? Make this section epic! 🌟
1. Fork the repo.
2. Add a new project folder with a `README.md` and dataset.
3. Submit a Pull Request with a clear description.

---

## 📂 Dataset & Database Details

To run these projects, set up the following tables and data in your database (MySQL, PostgreSQL, or SQL Server). Each project uses indexes on these tables, testing all four concepts. Below are schemas and sample data—copy-paste to create tables or save as a `.sql` file.

### Dataset 1: predictions
- **Used In**: Project 2, Project 3, Project 5 (Capstone)
- **Description**: ML predictions for index-based optimization.
- **Schema**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 102, 0.95, '2025-08-17'),
  (4, 102, 0.78, '2025-08-18'),
  (5, 103, 0.91, '2025-08-19'),
  (6, 103, 0.85, '2025-08-20'),
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
- **Notes**: Supports B-Tree and Hash indexes for range and equality queries.

### Dataset 2: features
- **Used In**: Project 1, Project 3, Project 5 (Capstone)
- **Description**: ML feature data for indexing.
- **Schema**:
  ```sql
  CREATE TABLE features (
      feature_id INT PRIMARY KEY,
      user_id INT,
      model_id INT,
      feature FLOAT
  );
  ```
- **Sample Data** (20 rows):
  ```sql
  INSERT INTO features (feature_id, user_id, model_id, feature) VALUES
  (1, 12345, 101, 0.65),
  (2, 12346, 101, 0.72),
  (3, 12347, 102, 0.88),
  (4, 12348, 102, 0.91),
  (5, 12349, 103, 0.79),
  (6, 12350, 103, 0.67),
  (7, 12351, 104, 0.85),
  (8, 12352, 104, 0.76),
  (9, 12353, 105, 0.93),
  (10, 12354, 105, 0.82),
  (11, 12355, 106, 0.70),
  (12, 12356, 106, 0.89),
  (13, 12357, 107, 0.77),
  (14, 12358, 107, 0.94),
  (15, 12359, 108, 0.81),
  (16, 12360, 108, 0.90),
  (17, 12361, 109, 0.78),
  (18, 12362, 109, 0.87),
  (19, 12363, 110, 0.95),
  (20, 12364, 110, 0.73);
  ```
- **Notes**: Supports unique and Hash indexes for lookups.

### Dataset 3: models
- **Used In**: Project 2
- **Description**: ML model metadata for joins.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE
  );
  ```
- **Sample Data** (10 rows):
  ```sql
  INSERT INTO models (model_id, model_name, created_date) VALUES
  (101, 'Model A', '2025-08-01'),
  (102, 'Model B', '2025-08-02'),
  (103, 'Model C', '2025-08-03'),
  (104, 'Model D', '2025-08-04'),
  (105, 'Model E', '2025-08-05'),
  (106, 'Model F', '2025-08-06'),
  (107, 'Model G', '2025-08-07'),
  (108, 'Model H', '2025-08-08'),
  (109, 'Model I', '2025-08-09'),
  (110, 'Model J', '2025-08-10');
  ```
- **Notes**: Supports B-Tree indexes for joins and filters.

### Dataset 4: locations
- **Used In**: Project 4, Project 5 (Capstone)
- **Description**: Geospatial data for R-Tree indexing.
- **Schema** (PostgreSQL with PostGIS):
  ```sql
  CREATE TABLE locations (
      location_id INT PRIMARY KEY,
      name VARCHAR(100),
      geog GEOGRAPHY(POINT)
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO locations (location_id, name, geog) VALUES
  (1, 'Store A', ST_GeogFromText('POINT(-73.95 40.75)')),
  (2, 'Store B', ST_GeogFromText('POINT(-73.90 40.80)')),
  (3, 'Store C', ST_GeogFromText('POINT(-74.00 40.70)')),
  (4, 'Store D', ST_GeogFromText('POINT(-73.85 40.85)')),
  (5, 'Store E', ST_GeogFromText('POINT(-73.92 40.77)')),
  (6, 'Store F', ST_GeogFromText('POINT(-73.87 40.82)')),
  (7, 'Store G', ST_GeogFromText('POINT(-74.02 40.72)')),
  (8, 'Store H', ST_GeogFromText('POINT(-73.88 40.79)')),
  (9, 'Store I', ST_GeogFromText('POINT(-73.93 40.76)')),
  (10, 'Store J', ST_GeogFromText('POINT(-73.91 40.81)')),
  (11, 'Store K', ST_GeogFromText('POINT(-74.01 40.71)')),
  (12, 'Store L', ST_GeogFromText('POINT(-73.86 40.84)')),
  (13, 'Store M', ST_GeogFromText('POINT(-73.94 40.74)')),
  (14, 'Store N', ST_GeogFromText('POINT(-73.89 40.83)')),
  (15, 'Store O', ST_GeogFromText('POINT(-74.03 40.69)'));
  ```
- **Notes**: Requires PostGIS for R-Tree (GiST) indexes.

### Dataset 5: documents
- **Used In**: Project 4
- **Description**: Text data for Full-Text indexing.
- **Schema**:
  ```sql
  CREATE TABLE documents (
      doc_id INT PRIMARY KEY,
      content TEXT
  );
  ```
- **Sample Data** (15 rows):
  ```sql
  INSERT INTO documents (doc_id, content) VALUES
  (1, 'Machine learning is transforming industries'),
  (2, 'Deep learning models for image recognition'),
  (3, 'Natural language processing with transformers'),
  (4, 'AI advancements in 2025'),
  (5, 'Neural networks for predictive analytics'),
  (6, 'Machine learning for healthcare solutions'),
  (7, 'Reinforcement learning in robotics'),
  (8, 'Text analysis with NLP techniques'),
  (9, 'AI-driven insights for business'),
  (10, 'Deep learning for autonomous vehicles'),
  (11, 'Machine learning in finance'),
  (12, 'Transformers for language models'),
  (13, 'AI for personalized recommendations'),
  (14, 'Natural language processing trends'),
  (15, 'Machine learning for fraud detection');
  ```
- **Notes**: Supports Full-Text indexes for NLP queries.

### Setup Instructions
1. **Create Tables**: Run the `CREATE TABLE` and `INSERT` statements for all datasets.
2. **Execute Index Queries**: Use project tasks to create and test indexes.
3. **Test Environment**: Use a sandbox (e.g., MySQL Workbench, pgAdmin, SQL Server Management Studio) to verify performance.
4. **Compatibility**:
   - MySQL: Supports B-Tree, Full-Text. No native Hash (use InnoDB key lookups).
   - PostgreSQL: Supports B-Tree, Hash, GiST (R-Tree via PostGIS). Install `CREATE EXTENSION postgis` for `locations`.
   - SQL Server: Supports B-Tree, Spatial. Hash for memory-optimized tables.
5. **Expand Data**: For up to 100 rows, repeat similar patterns or generate programmatically.

---

<div align="center">
  <p>Dive into these projects to master SQL Indexing and shine in AI/ML interviews! Happy optimizing! ✨</p>
</div>