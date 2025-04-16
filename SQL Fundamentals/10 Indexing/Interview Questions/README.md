# 🎯 Interview Questions - Indexing to Crush SQL Interviews

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master Indexing and land that AI/ML role! 🚀</p>

---

## 🌟 Overview

Welcome to the **Interview Questions** arena for **Indexing**! 💻 This README is your secret weapon, packed with tricky, real-world questions covering **four core concepts**: `Creating Indexes`, `B-Tree Indexes`, `Hash Indexes`, and `Specialty Indexes`. Crafted to mirror coding tests and technical rounds at top companies, each section below dives into one concept with 1-2 challenging, ML-themed questions. With schemas, sample data, and solutions (hidden in `<details>` tags), you’ll sharpen your optimization skills, boost your confidence, and make your portfolio shine for recruiters. Let’s index those queries and ace those interviews!

---

## 🎯 Why These Questions?

These questions are designed to:
- **Mimic Real Interviews**: Tackle problems inspired by FAANG, startups, and ML-focused SQL challenges.
- **Master Indexing**: Perfect your ability to speed up queries and optimize databases.
- **Power AI/ML Workflows**: Accelerate feature retrieval, spatial ML, and NLP tasks.
- **Shine Under Pressure**: Practice explaining index choices for whiteboard rounds.
- **Boost Portfolio**: Showcase your solutions on GitHub to impress recruiters.

---

## 🚀 How to Use This README

1. **Set Up**: Check **Schema & Database Details** below to create tables, load data, and test queries.
2. **Dive In**:
   - Pick a concept section (e.g., `Creating Indexes`).
   - Read the question and try writing the index in a sandbox (MySQL, PostgreSQL, SQL Server, etc.).
3. **Test Your Index**: Run queries with and without the index, using `EXPLAIN` to compare performance.
4. **Need a Hint?**: Peek at the **Solution (Answer)** in `<details>` tags.
5. **Practice Explaining**: Verbalize your index logic to nail interview communication.
6. **Show Off**: Save solutions to your GitHub for portfolio cred!

> **Pro Tip**: Start with `Creating Indexes` to grasp basics, then tackle `B-Tree` and `Specialty Indexes` for ML scenarios. Use solutions sparingly to build real skills!

---

## 📚 Interview Questions by Concept

Below, each concept has 1-2 tricky questions with ML-relevant scenarios, schemas, and solutions. Get ready to optimize like a pro!

### 1. Creating Indexes
- **Description**: `CREATE INDEX` builds structures to speed up data retrieval.
- **Interview Focus**: Tests syntax and index selection.

#### Question 1.1: Index for Prediction Filtering
- **Problem**: Your ML pipeline runs slow on filtering predictions. Write a query to create an index on `predictions` to optimize `SELECT * FROM predictions WHERE model_id = 101 AND score > 0.9`.
- **Trick**: Tests if you choose a multi-column index and order columns correctly.
- **AI/ML Use Case**: Speeds up model-specific prediction queries.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE INDEX idx_model_score ON predictions (model_id, score);
  ```
  </details>

#### Question 1.2: Unique Index for Features
- **Problem**: Your feature table has duplicate `user_id` entries, breaking ML preprocessing. Write a query to create a unique index on `features.user_id` to prevent duplicates.
- **Trick**: Tests if you use `CREATE UNIQUE INDEX` for data integrity.
- **AI/ML Use Case**: Ensures clean feature data for training.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE UNIQUE INDEX idx_unique_user ON features (user_id);
  ```
  </details>

---

### 2. B-Tree Indexes
- **Description**: B-Tree indexes handle equality, range, and sorting queries efficiently.
- **Interview Focus**: Tests B-Tree application and query optimization.

#### Question 2.1: Optimize Range Query
- **Problem**: A query `SELECT * FROM predictions WHERE prediction_date BETWEEN '2025-08-01' AND '2025-08-31' ORDER BY score DESC` is slow. Write a B-Tree index to speed it up.
- **Trick**: Tests if you index for range and sorting clauses.
- **AI/ML Use Case**: Accelerates time-based prediction analysis.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE INDEX idx_pred_date_score ON predictions USING btree (prediction_date, score);
  ```
  </details>

#### Question 2.2: Speed Up Join
- **Problem**: The query `SELECT f.feature FROM features f JOIN models m ON f.model_id = m.model_id WHERE m.created_date > '2025-08-01'` is sluggish. Write a B-Tree index on `models` to optimize it.
- **Trick**: Tests if you index the JOIN and filter columns.
- **AI/ML Use Case**: Boosts feature-model joins for ML pipelines.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE INDEX idx_model_date ON models USING btree (created_date, model_id);
  ```
  </details>

---

### 3. Hash Indexes
- **Description**: Hash indexes excel for exact-match queries.
- **Interview Focus**: Tests Hash index use and limitations.

#### Question 3.1: Fast Model Lookup
- **Problem**: The query `SELECT * FROM predictions WHERE model_id = 102` runs frequently but slowly in PostgreSQL. Write a Hash index to optimize it.
- **Trick**: Tests if you choose Hash for equality and verify DB support.
- **AI/ML Use Case**: Speeds up model-specific prediction retrieval.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE INDEX idx_model_id_hash ON predictions USING hash (model_id);
  ```
  </details>

#### Question 3.2: User Feature Access
- **Problem**: In PostgreSQL, `SELECT feature FROM features WHERE user_id = 12345` is slow on a large table. Write a Hash index to improve performance.
- **Trick**: Tests if you apply Hash for high-selectivity keys.
- **AI/ML Use Case**: Optimizes user-specific feature lookups for inference.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE INDEX idx_user_id_hash ON features USING hash (user_id);
  ```
  </details>

---

### 4. Specialty Indexes
- **Description**: Specialty indexes (R-Tree, Full-Text, etc.) handle spatial, text, or custom queries.
- **Interview Focus**: Tests advanced index application for ML scenarios.

#### Question 4.1: Spatial ML Query
- **Problem**: Your geospatial ML model uses `SELECT * FROM locations WHERE ST_Within(geog, ST_MakeEnvelope(-74, 40, -73, 41))` in PostgreSQL with PostGIS, but it’s slow. Write an R-Tree index to optimize it.
- **Trick**: Tests if you use `gist` for spatial queries.
- **AI/ML Use Case**: Accelerates location-based model inference.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE INDEX idx_location ON locations USING gist (geog);
  ```
  </details>

#### Question 4.2: NLP Text Search
- **Problem**: The query `SELECT * FROM documents WHERE MATCH(content) AGAINST('machine learning')` in MySQL is slow for NLP data. Write a Full-Text index to speed it up.
- **Trick**: Tests if you apply `FULLTEXT` for text search.
- **AI/ML Use Case**: Optimizes text queries for NLP datasets.
- **Solution (Answer)**:
  <details>
  <summary>Solution</summary>
  ```sql
  CREATE FULLTEXT INDEX idx_content ON documents (content);
  ```
  </details>

---

## 💡 Tips for Success

- **Start Basic**: Begin with `Creating Indexes` to nail syntax.
- **Watch for Traps**: Interviewers test over-indexing, wrong index types (e.g., Hash for ranges), and missing `EXPLAIN` analysis.
- **Explain Clearly**: Practice justifying index choices (e.g., B-Tree vs. Hash) for whiteboard rounds.
- **Test Thoroughly**: Run queries in MySQL, PostgreSQL, or SQL Server with the schemas below.
- **Optimize Indexes**: Avoid redundant indexes; use `DROP INDEX` for unused ones.
- **Portfolio Power**: Save solutions to your GitHub to show recruiters your SQL skills.

---

## 📂 Schema & Database Details

To tackle these questions, set up the following tables in your database (MySQL, PostgreSQL, or SQL Server). Each question uses these tables to test index performance. Below are schemas and sample data—copy-paste to create tables or save as `.sql` files.

### Schema 1: predictions
- **Used In**: Creating Indexes, B-Tree Indexes, Hash Indexes
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
- **Sample Data** (6 rows):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date) VALUES
  (1, 101, 0.92, '2025-08-15'),
  (2, 101, 0.87, '2025-08-16'),
  (3, 102, 0.95, '2025-08-17'),
  (4, 102, 0.78, '2025-08-18'),
  (5, 103, 0.91, '2025-08-19'),
  (6, 103, 0.85, '2025-08-20');
  ```

### Schema 2: features
- **Used In**: Creating Indexes, Hash Indexes
- **Description**: Stores ML feature data.
- **Schema**:
  ```sql
  CREATE TABLE features (
      feature_id INT PRIMARY KEY,
      user_id INT,
      model_id INT,
      feature FLOAT
  );
  ```
- **Sample Data** (5 rows):
  ```sql
  INSERT INTO features (feature_id, user_id, model_id, feature) VALUES
  (1, 12345, 101, 0.65),
  (2, 12346, 101, 0.72),
  (3, 12347, 102, 0.88),
  (4, 12348, 102, 0.91),
  (5, 12349, 103, 0.79);
  ```

### Schema 3: models
- **Used In**: B-Tree Indexes
- **Description**: Stores ML model metadata.
- **Schema**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(100),
      created_date DATE
  );
  ```
- **Sample Data** (4 rows):
  ```sql
  INSERT INTO models (model_id, model_name, created_date) VALUES
  (101, 'Model A', '2025-08-01'),
  (102, 'Model B', '2025-08-02'),
  (103, 'Model C', '2025-08-03'),
  (104, 'Model D', '2025-08-04');
  ```

### Schema 4: locations
- **Used In**: Specialty Indexes
- **Description**: Stores geospatial data for ML.
- **Schema** (PostgreSQL with PostGIS):
  ```sql
  CREATE TABLE locations (
      location_id INT PRIMARY KEY,
      name VARCHAR(100),
      geog GEOGRAPHY(POINT)
  );
  ```
- **Sample Data** (4 rows):
  ```sql
  INSERT INTO locations (location_id, name, geog) VALUES
  (1, 'Store A', ST_GeogFromText('POINT(-73.95 40.75)')),
  (2, 'Store B', ST_GeogFromText('POINT(-73.90 40.80)')),
  (3, 'Store C', ST_GeogFromText('POINT(-74.00 40.70)')),
  (4, 'Store D', ST_GeogFromText('POINT(-73.85 40.85)'));
  ```

### Schema 5: documents
- **Used In**: Specialty Indexes
- **Description**: Stores text data for NLP.
- **Schema**:
  ```sql
  CREATE TABLE documents (
      doc_id INT PRIMARY KEY,
      content TEXT
  );
  ```
- **Sample Data** (4 rows):
  ```sql
  INSERT INTO documents (doc_id, content) VALUES
  (1, 'Machine learning is transforming industries'),
  (2, 'Deep learning models for image recognition'),
  (3, 'Natural language processing with transformers'),
  (4, 'AI advancements in 2025');
  ```

### Setup Instructions
1. **Create Tables and Data**: Run the `CREATE TABLE` and `INSERT` statements above.
2. **Test Indexes**: Use a sandbox (MySQL Workbench, pgAdmin, SQL Server Management Studio) to create indexes and run queries.
3. **Compatibility**:
   - MySQL: Supports B-Tree, Full-Text; no native Hash (use InnoDB key lookups).
   - PostgreSQL: Supports B-Tree, Hash, GiST (R-Tree via PostGIS), Bitmap; requires `CREATE EXTENSION postgis` for `locations`.
   - SQL Server: Supports B-Tree, Spatial; Hash for memory-optimized tables.
4. **Verify Performance**: Run queries with `EXPLAIN` (MySQL/PostgreSQL) or `SHOW PLAN` (SQL Server) to confirm index usage.
5. **Data Scale**: Sample data is small (~23 rows total) for testing; scale to 1,000 rows by repeating patterns for real-world simulation.

---

<div align="center">
  <p>Smash these Indexing questions to rule SQL interviews and supercharge your AI/ML journey! Happy optimizing! ✨</p>
</div>