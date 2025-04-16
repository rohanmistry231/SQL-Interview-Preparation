# 🔍 Specialized Queries - Advanced Tools for ML Data

## 🌟 Overview

**Specialized Queries** cover advanced SQL techniques like JSON/XML parsing, `MERGE`/`UPSERT`, table partitioning, and query hints, unlocking flexibility for complex ML tasks. These tools handle semi-structured data, efficient updates, or performance tuning. In AI/ML, specialized queries are crucial for parsing model configs, merging datasets, or optimizing large-scale queries.

---

## 📜 Syntax

```sql
-- JSON Query (PostgreSQL)
SELECT JSON_EXTRACT_PATH_TEXT(config, 'hyperparams', 'lr') AS learning_rate
FROM model_configs;
```

- **JSON Query** (PostgreSQL):
  ```sql
  SELECT model_id, config->>'accuracy' AS accuracy
  FROM model_configs
  WHERE config->>'model_type' = 'neural_net';
  ```
- **MERGE** (SQL Server):
  ```sql
  MERGE INTO predictions AS target
  USING new_predictions AS source
  ON target.prediction_id = source.prediction_id
  WHEN MATCHED THEN
      UPDATE SET score = source.score
  WHEN NOT MATCHED THEN
      INSERT (prediction_id, score)
      VALUES (source.prediction_id, source.score);
  ```
- **Table Partitioning** (PostgreSQL):
  ```sql
  CREATE TABLE predictions (
      prediction_id INT,
      score FLOAT,
      prediction_date DATE
  ) PARTITION BY RANGE (prediction_date);
  CREATE TABLE predictions_2025 PARTITION OF predictions
      FOR VALUES FROM ('2025-01-01') TO ('2026-01-01');
  ```
- **Query Hint** (SQL Server):
  ```sql
  SELECT * FROM predictions WITH (INDEX(idx_score))
  WHERE score > 0.9;
  ```

---

## 💡 Use Cases in AI/ML

- **Model Configs**: Parse JSON for hyperparameters (e.g., `JSON_EXTRACT(config, '$.lr')`).
- **Data Sync**: Use `MERGE` to update ML predictions with new data (e.g., sync inference results).
- **Scalability**: Partition large feature tables by date for faster queries (e.g., `PARTITION BY RANGE(date)`).
- **Query Tuning**: Apply hints to force index usage in ML pipelines (e.g., `FORCE INDEX`).

---

## 🔑 Key Features

- **JSON/XML Parsing**: Query semi-structured data for ML configs or embeddings.
- **MERGE/UPSERT**: Combines inserts and updates for efficient pipelines.
- **Partitioning**: Splits tables for performance on big ML datasets.
- **Query Hints**: Guides optimizer for tailored query plans.

---

## ✅ Best Practices

- **Validate JSON**: Ensure JSON data is well-formed before querying (e.g., `IS_JSON` in MySQL).
- **Index Partitions**: Create indexes on partitioned tables for speed (e.g., `CREATE INDEX ON predictions_2025(score)`).
- **Test MERGE Logic**: Verify `WHEN MATCHED`/`NOT MATCHED` conditions to avoid data errors.
- **Use Hints Sparingly**: Apply query hints only when optimizer fails—test with `EXPLAIN`.

---

## ⚠️ Common Pitfalls

- **JSON Overhead**: Parsing large JSON fields slows queries—extract to columns if frequent.
- **MERGE Conflicts**: Ambiguous `ON` clauses cause duplicate updates—ensure unique keys.
- **Partition Misuse**: Over-partitioning small tables wastes resources—partition only large datasets.
- **Hint Overreach**: Forcing bad plans (e.g., wrong index) degrades performance—validate with metrics.

---

## 📝 Additional Notes

- **Database Variations**: PostgreSQL excels at JSON (`->>`), SQL Server supports `MERGE`, MySQL 8.0+ has JSON but no native `MERGE`.
- **Partition Limits**: PostgreSQL supports range/list partitioning; MySQL supports only basic partitioning.
- **Security**: Restrict JSON query access to prevent exposure of sensitive configs.
- **Tools**: Use `pg_partman` (PostgreSQL) for partition management or SQL Server DMVs for hint analysis.