# ⚙️ Project 5: Dynamic Model Evaluator

## 🌟 Overview

Step into **Dynamic Model Evaluator**, where you’ll craft flexible ML evaluation queries using *Dynamic Queries*, *Stored Procedures*, and *User-Defined Functions*! This project builds a reusable evaluator for model metrics, a star for your *ML-Interview-Preparation-Hub* portfolio to show automation skills. 🚀

## 📊 Project Details

- **Scenario**: You’re an ML developer automating model evaluation. Your task is to create dynamic SQL to compute metrics based on user inputs and store reusable logic.
- **Goals**: Build dynamic queries, create procedures, and export results.
- **SQL Skills**: *Dynamic Queries* (EXECUTE), *Stored Procedures*, *User-Defined Functions*.

## 📋 Tasks

1. Use `predictions` and `model_configs` (`model_id INT, config JSON`).
2. Insert sample data with JSON configs.
3. Write a UDF to extract JSON metrics.
4. Create a stored procedure for dynamic metric queries.
5. Build a dynamic query to filter by date or model.
6. Export results to a CSV.
7. Document for portfolio use.

## 💻 Sample Solution

```sql
-- Task 1: Tables exist (predictions), create model_configs
CREATE TABLE model_configs (
    model_id INT PRIMARY KEY,
    config JSON
);

-- Task 2: Insert Sample Data
INSERT INTO model_configs VALUES
(101, '{"metric": "accuracy", "value": 0.85}'),
(102, '{"metric": "f1_score", "value": 0.90}');
INSERT INTO predictions VALUES
(1, 101, 0.85, '2025-04-15', 'BERT_v1'),
(2, 102, 0.90, '2025-04-20', 'XGBoost_v2');

-- Task 3: Create UDF
CREATE OR REPLACE FUNCTION get_json_metric(config JSON, metric_key VARCHAR)
RETURNS FLOAT AS $$
BEGIN
    RETURN config->>metric_key::FLOAT;
END;
$$ LANGUAGE plpgsql;

-- Task 4: Stored Procedure
CREATE OR REPLACE PROCEDURE evaluate_models(metric_type VARCHAR)
LANGUAGE plpgsql AS $$
BEGIN
    EXECUTE format('
        SELECT p.model_id, AVG(p.score) AS avg_score, get_json_metric(c.config, %L) AS config_metric
        FROM predictions p
        JOIN model_configs c ON p.model_id = c.model_id
        GROUP BY p.model_id, c.config
    ', metric_type);
END;
$$;

-- Task 5: Dynamic Query
DO $$
BEGIN
    EXECUTE 'SELECT model_id, AVG(score) AS avg_score
             FROM predictions
             WHERE prediction_date >= ''2025-04-01''
             GROUP BY model_id';
END $$;

-- Task 6: Export (Pseudo-code)
-- COPY (SELECT ...) TO 'model_metrics.csv' WITH CSV HEADER;

-- Task 7: Document (See Portfolio Tips)
```

**Explanation**:
- *DDL* adds config table.
- *UDF* extracts JSON metrics.
- *Stored Procedures* and *Dynamic Queries* enable flexible evaluation.
- *DML* tests functionality.

## 🎯 Expected Outcome

- A dynamic evaluation query system.
- A CSV file (`model_metrics.csv`) with model metrics.
- A portfolio-ready automation showcase.

## 💼 Portfolio Tips

- Add `model_metrics.csv` to `irohanportfolio.netlify.app`.
- Write a README explaining automation and ML use (e.g., model evaluation).
- Demo with Python’s `sqlalchemy` calling the procedure.
- Tag skills: *Dynamic Queries*, *Stored Procedures*, *UDFs*.

## 🔥 Challenge

Add a *Cursor* to iterate over models for batch evaluation.

---