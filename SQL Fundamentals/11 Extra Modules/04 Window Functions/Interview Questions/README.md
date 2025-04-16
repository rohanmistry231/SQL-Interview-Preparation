# 🎯 Window Functions Interview Questions

## 🌟 Overview

**Window Functions** are a favorite in SQL interviews, testing your ability to analyze data without grouping, like ranking models or tracking trends. In AI/ML, they’re crucial for ranking predictions, time-series analysis, or feature engineering. These questions, covering `RANK`, `LAG`, and more, will prep you for FAANG-style ML challenges—let’s crush it! 🚀

---

## 📚 Interview Questions

### Question 1: Rank Predictions by Score
- **Difficulty**: Easy
- **Problem**: Given a `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE`), rank predictions within each `model_id` by `score` (highest first).
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  SELECT prediction_id, model_id, score,
         RANK() OVER (PARTITION BY model_id ORDER BY score DESC) AS score_rank
  FROM predictions;
  ```
  **Explanation**: `RANK()` assigns ranks within each `model_id`, with ties getting the same rank and gaps (e.g., 1,1,3). For dense ranking:
  ```sql
  SELECT ..., DENSE_RANK() OVER (...) AS dense_rank
  ```
  Use `DENSE_RANK()` for no gaps (e.g., 1,1,2).
  </details>

### Question 2: Calculate Score Delta
- **Difficulty**: Medium
- **Problem**: For the `predictions` table, compute the difference between each `score` and the previous `score` for the same `model_id`, ordered by `prediction_date`.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  SELECT prediction_id, model_id, score,
         score - LAG(score) OVER (PARTITION BY model_id ORDER BY prediction_date) AS score_delta
  FROM predictions;
  ```
  **Explanation**: `LAG(score)` fetches the previous `score` within the `model_id`, ordered by `prediction_date`. Subtracting gives the delta. Handle `NULL` with:
  ```sql
  COALESCE(score - LAG(score) OVER (...), 0) AS score_delta
  ```
  </details>

### Question 3: Running Average Score
- **Difficulty**: Medium
- **Problem**: Compute the running average `score` for each `model_id` in the `predictions` table, ordered by `prediction_date`.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  SELECT prediction_id, model_id, score,
         AVG(score) OVER (
             PARTITION BY model_id
             ORDER BY prediction_date
             ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
         ) AS running_avg
  FROM predictions;
  ```
  **Explanation**: `AVG(score)` over a window from the start to the current row calculates the running average per `model_id`. The `ROWS` clause ensures a cumulative window.
  </details>

### Question 4: Top N Predictions
- **Difficulty**: Hard
- **Problem**: Select the top 2 predictions per `model_id` by `score` from the `predictions` table.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  WITH RankedPredictions AS (
      SELECT prediction_id, model_id, score,
             ROW_NUMBER() OVER (PARTITION BY model_id ORDER BY score DESC) AS rn
      FROM predictions
  )
  SELECT prediction_id, model_id, score
  FROM RankedPredictions
  WHERE rn <= 2;
  ```
  **Explanation**: `ROW_NUMBER()` assigns unique numbers per `model_id`, ordered by `score`. Filtering `rn <= 2` keeps the top 2. Use a CTE for clarity, common in interviews.
  </details>

---

## 💡 Tips for Acing Window Function Interviews

- **Know the Functions**: Memorize `RANK`, `DENSE_RANK`, `ROW_NUMBER`, `LAG`, `LEAD`, and aggregates.
- **Sketch Partitions**: Map out `PARTITION BY` and `ORDER BY` before coding.
- **Optimize Windows**: Index `PARTITION BY` columns and test with `EXPLAIN`.
- **Practice Frames**: Experiment with `ROWS` vs. `RANGE` for cumulative vs. grouped calculations.

---

## 📝 Note

These questions are your runway to success! Tweak them (e.g., add partitions, change metrics) and showcase solutions in your portfolio. Got a window function puzzle? Share it to make this repo shine! 🌟