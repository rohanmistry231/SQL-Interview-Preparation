# 🎯 Specialized Queries Interview Questions

## 🌟 Overview

**Specialized Queries** cover advanced SQL like JSON parsing, `MERGE`, partitioning, and hints, testing your ability to handle complex ML data. In AI/ML, they’re key for parsing configs, syncing datasets, or optimizing big queries. These questions, spanning JSON, `MERGE`, and more, will gear you up for FAANG-style ML interviews—let’s dive in! 🚀

---

## 📚 Interview Questions

### Question 1: Parse JSON Config
- **Difficulty**: Easy
- **Problem**: Given a `model_configs` table (`model_id INT, config JSON`), extract the learning rate (`lr`) from the `config` JSON for each `model_id`.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- PostgreSQL
  SELECT model_id, config->'hyperparams'->>'lr' AS learning_rate
  FROM model_configs;
  ```
  **Explanation**: The `->` and `->>` operators extract the `lr` field from nested JSON. For MySQL:
  ```sql
  SELECT model_id, JSON_EXTRACT(config, '$.hyperparams.lr') AS learning_rate
  FROM model_configs;
  ```
  Handles JSON paths clearly, common in ML config queries.
  </details>

### Question 2: Merge Predictions
- **Difficulty**: Medium
- **Problem**: Using the `predictions` table (`prediction_id INT, model_id INT, score FLOAT`), write a `MERGE` to update scores from a `new_predictions` table (`prediction_id INT, score FLOAT`) or insert new ones.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- SQL Server
  MERGE INTO predictions AS target
  USING new_predictions AS source
  ON target.prediction_id = source.prediction_id
  WHEN MATCHED THEN
      UPDATE SET score = source.score
  WHEN NOT MATCHED THEN
      INSERT (prediction_id, model_id, score)
      VALUES (source.prediction_id, 101, source.score);
  ```
  **Explanation**: `MERGE` updates matching `prediction_id`s and inserts new ones, assuming a default `model_id`. For PostgreSQL (no `MERGE`):
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score)
  SELECT prediction_id, 101, score
  FROM new_predictions
  ON CONFLICT (prediction_id)
  DO UPDATE SET score = EXCLUDED.score;
  ```
  </details>

### Question 3: Partitioned Query Optimization
- **Difficulty**: Medium
- **Problem**: Given a partitioned `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE`), write a query to select scores for 2025, using a hint to force an index.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- SQL Server
  SELECT * FROM predictions WITH (INDEX(idx_score))
  WHERE prediction_date BETWEEN '2025-01-01' AND '2025-12-31';
  ```
  **Explanation**: The hint forces `idx_score` for optimization. For PostgreSQL:
  ```sql
  SELECT * FROM predictions
  WHERE prediction_date >= '2025-01-01' AND prediction_date <= '2025-12-31';
  ```
  Assumes partitioning by `prediction_date`, so the planner targets 2025 partitions.
  </details>

### Question 4: JSON Aggregation
- **Difficulty**: Hard
- **Problem**: Aggregate `model_configs` to count models by `model_type` stored in `config` JSON, filtering for `accuracy > 0.9`.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- PostgreSQL
  SELECT config->>'model_type' AS model_type, COUNT(*) AS model_count
  FROM model_configs
  WHERE CAST(config->>'accuracy' AS FLOAT) > 0.9
  GROUP BY config->>'model_type';
  ```
  **Explanation**: Extracts `model_type` and `accuracy` from JSON, filters, and aggregates. For MySQL:
  ```sql
  SELECT JSON_EXTRACT(config, '$.model_type') AS model_type, COUNT(*) AS model_count
  FROM model_configs
  WHERE JSON_EXTRACT(config, '$.accuracy') > 0.9
  GROUP BY JSON_EXTRACT(config, '$.model_type');
  ```
  Casting ensures numeric comparison.
  </details>

---

## 💡 Tips for Acing Specialized Query Interviews

- **Master JSON Paths**: Practice `->>` (PostgreSQL) or `JSON_EXTRACT` (MySQL) for ML config queries.
- **Understand MERGE**: Map out `WHEN MATCHED` vs. `NOT MATCHED` logic before coding.
- **Test Partitioning**: Use `EXPLAIN` to verify partition pruning in big ML datasets.
- **Use Hints Judiciously**: Know when to force indexes vs. trust the optimizer.

---

## 📝 Note

These questions are your edge! Adapt them (e.g., new JSON fields, partition keys) and add to your portfolio to impress recruiters. Got a specialized query gem? Share it to make this repo epic! 🌟