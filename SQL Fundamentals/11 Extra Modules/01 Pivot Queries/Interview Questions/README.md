# 🎯 Pivot Queries Interview Questions

## 🌟 Overview

**Pivot Queries** are a go-to for reshaping data in SQL interviews, turning rows into columns for analytics. In AI/ML roles, expect questions on `PIVOT` or manual pivoting (e.g., `CASE` statements) to summarize model metrics or feature data. These questions test your ability to transform datasets for ML dashboards or comparisons, a must-have skill for data-driven roles. Let’s dive into ML-themed challenges to prep you for FAANG-style interviews! 🚀

---

## 📚 Interview Questions

### Question 1: Pivot Model Scores by Model
- **Difficulty**: Easy
- **Problem**: Given a `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE`), pivot the data to show average scores for `model_id` 101 and 102 as columns.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  SELECT *
  FROM predictions
  PIVOT (
      AVG(score)
      FOR model_id IN (101 AS model_101, 102 AS model_102)
  ) AS p;
  ```
  **Explanation**: The `PIVOT` aggregates `score` by `model_id`, creating columns `model_101` and `model_102` with average scores. For MySQL, use:
  ```sql
  SELECT prediction_date,
         AVG(CASE WHEN model_id = 101 THEN score END) AS model_101,
         AVG(CASE WHEN model_id = 102 THEN score END) AS model_102
  FROM predictions
  GROUP BY prediction_date;
  ```
  </details>

### Question 2: Dynamic Pivot for Model Scores
- **Difficulty**: Medium
- **Problem**: Pivot the `predictions` table to show average scores for all `model_id`s dynamically, without hardcoding values.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  DECLARE @columns NVARCHAR(MAX), @sql NVARCHAR(MAX);
  SELECT @columns = STRING_AGG(QUOTENAME(model_id) + ' AS model_' + CAST(model_id AS NVARCHAR(10)), ',')
  FROM (SELECT DISTINCT model_id FROM predictions) AS m;
  SET @sql = '
  SELECT *
  FROM predictions
  PIVOT (
      AVG(score)
      FOR model_id IN (' + @columns + ')
  ) AS p;';
  EXEC sp_executesql @sql;
  ```
  **Explanation**: This SQL Server query builds a dynamic `PIVOT` by generating column names from unique `model_id`s. For PostgreSQL/MySQL, dynamic pivoting requires scripting outside SQL.
  </details>

### Question 3: Pivot Features by Category
- **Difficulty**: Medium
- **Problem**: Given a `features` table (`feature_id INT, user_id INT, model_id INT, feature FLOAT, category VARCHAR`), pivot to show average `feature` values for categories ‘age’ and ‘income’ per `user_id`.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  SELECT user_id,
         AVG(CASE WHEN category = 'age' THEN feature END) AS age,
         AVG(CASE WHEN category = 'income' THEN feature END) AS income
  FROM features
  GROUP BY user_id;
  ```
  **Explanation**: Since MySQL lacks `PIVOT`, we use `CASE` to mimic it, averaging `feature` for each `category`. For SQL Server:
  ```sql
  SELECT *
  FROM features
  PIVOT (
      AVG(feature)
      FOR category IN (age, income)
  ) AS p;
  ```
  </details>

---

## 💡 Tips for Acing Pivot Query Interviews

- **Practice Manual Pivoting**: Master `CASE` and `GROUP BY` for MySQL or PostgreSQL, where `PIVOT` isn’t native.
- **Sketch the Output**: Visualize the pivoted table before coding to clarify columns and aggregates.
- **Test with EXPLAIN**: Check query performance, as pivots on large datasets can be slow without indexes.
- **Know Dynamic SQL**: Be ready for dynamic pivots, common in advanced ML pipeline questions.

---

## 📝 Note

These questions are designed to spark your curiosity! Tweak them (e.g., add more models, change aggregates) and add solutions to your portfolio to impress recruiters. Got a tricky pivot question? Share it to level up this repo! 🌟