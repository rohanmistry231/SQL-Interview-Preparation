# 🏗️ Project 3: Model Schema Builder

## 🌟 Overview

Get ready for **Schema Optimizer**, where you’ll design and secure an ML database schema using *DDL*, *DCL*, and *Triggers*! This project builds a robust structure for model data, perfect for your *ML-Interview-Preparation-Hub* portfolio to show scalable design. 🚀

## 📊 Project Details

- **Scenario**: You’re a database architect for an ML platform. Your task is to create tables for models and predictions, secure access, and automate logging.
- **Goals**: Build tables, set permissions, add triggers, and document schema.
- **SQL Skills**: *DDL* (CREATE, ALTER), *DCL* (GRANT), *Triggers*.

## 📋 Tasks

1. Create `models` (`model_id INT, trained_date DATE`) and `predictions` tables.
2. Add constraints (e.g., primary keys, foreign keys).
3. Grant read-only access to analysts using *DCL*.
4. Create a trigger to log prediction inserts.
5. Create a log table for trigger data.
6. Test the schema with sample inserts.
7. Document for portfolio use.

## 💻 Sample Solution

```sql
-- Task 1 & 2: Create Tables with Constraints
CREATE TABLE models (
    model_id INT PRIMARY KEY,
    trained_date DATE NOT NULL
);
CREATE TABLE predictions (
    prediction_id INT PRIMARY KEY,
    model_id INT,
    score FLOAT,
    prediction_date DATE,
    model_name VARCHAR(50),
    FOREIGN KEY (model_id) REFERENCES models(model_id)
);

-- Task 3: Grant Permissions
CREATE ROLE analyst;
GRANT SELECT ON models, predictions TO analyst;

-- Task 4 & 5: Create Log Table and Trigger
CREATE TABLE prediction_log (
    log_id SERIAL PRIMARY KEY,
    prediction_id INT,
    insert_time TIMESTAMP
);
CREATE OR REPLACE FUNCTION log_prediction()
RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO prediction_log (prediction_id, insert_time)
    VALUES (NEW.prediction_id, CURRENT_TIMESTAMP);
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;
CREATE TRIGGER prediction_insert
AFTER INSERT ON predictions
FOR EACH ROW EXECUTE FUNCTION log_prediction();

-- Task 6: Test Schema
INSERT INTO models VALUES (101, '2025-04-01');
INSERT INTO predictions VALUES (1, 101, 0.85, '2025-04-15', 'BERT_v1');
SELECT * FROM prediction_log;

-- Task 7: Document (See Portfolio Tips)
```

**Explanation**:
- *DDL* defines tables with constraints.
- *DCL* secures access for analysts.
- *Triggers* automate logging of inserts.
- Tests verify schema integrity.

## 🎯 Expected Outcome

- A secure, functional ML schema.
- A log table tracking prediction inserts.
- A portfolio-ready schema design doc.

## 💼 Portfolio Tips

- Add schema SQL to `irohanportfolio.netlify.app`.
- Write a README explaining design and ML use (e.g., model tracking).
- Diagram the schema with tools like Lucidchart.
- Tag skills: *DDL*, *DCL*, *Triggers*.

## 🔥 Challenge

Add a *TCL* transaction to ensure atomic inserts across tables.

---