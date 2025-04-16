# 🎯 Common Table Expressions Interview Questions

## 🌟 Overview

**Common Table Expressions (CTEs)** are a staple in SQL interviews, testing your ability to structure complex queries, especially for recursive or hierarchical ML data. In AI/ML, CTEs shine for feature engineering, graph analysis, or multi-step pipelines. These questions will prep you for FAANG-style challenges with ML flair—let’s dive in! 🚀

---

## 📚 Interview Questions

### Question 1: Filter High Scores with CTE
- **Difficulty**: Easy
- **Problem**: Using the `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE`), write a CTE to select predictions with `score > 0.9`.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  WITH high_scores AS (
      SELECT prediction_id, model_id, score
      FROM predictions
      WHERE score > 0.9
  )
  SELECT * FROM high_scores;
  ```
  **Explanation**: The CTE `high_scores` filters predictions, making the query modular. It’s equivalent to a subquery but clearer, a common interview expectation.
  </details>

### Question 2: Multi-Step Model Analysis
- **Difficulty**: Medium
- **Problem**: Given `predictions` and `models` (`model_id INT, model_name VARCHAR, created_date DATE`), use CTEs to compute average `score` per `model_id`, then select models with averages above 0.85.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  WITH scores AS (
      SELECT model_id, AVG(score) AS avg_score
      FROM predictions
      GROUP BY model_id
  ), top_models AS (
      SELECT m.model_id, m.model_name
      FROM models m
      JOIN scores s ON m.model_id = s.model_id
      WHERE s.avg_score > 0.85
  )
  SELECT * FROM top_models;
  ```
  **Explanation**: The first CTE computes averages, the second joins with `models` and filters. Chaining CTEs shows structured thinking, key for interviews.
  </details>

### Question 3: Recursive Feature Hierarchy
- **Difficulty**: Hard
- **Problem**: Given a `features` table with hierarchy (`feature_id INT, parent_id INT, name VARCHAR`), write a recursive CTE to list all features in a tree, starting from `parent_id IS NULL`.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  WITH RECURSIVE feature_tree AS (
      SELECT feature_id, parent_id, name, 1 AS level
      FROM features
      WHERE parent_id IS NULL
      UNION ALL
      SELECT f.feature_id, f.parent_id, f.name, ft.level + 1
      FROM features f
      INNER JOIN feature_tree ft ON f.parent_id = ft.feature_id
  )
  SELECT * FROM feature_tree ORDER BY level, feature_id;
  ```
  **Explanation**: The base case selects root features (`parent_id IS NULL`), and the recursive part joins children. The `level` tracks depth, useful for ML graph analysis.
  </details>

---

## 💡 Tips for Acing CTE Interviews

- **Break It Down**: Split complex queries into CTEs for clarity, a big win in interviews.
- **Master Recursion**: Practice recursive CTEs for hierarchical ML data—common in graph ML.
- **Optimize Joins**: Index tables in CTEs and verify with `EXPLAIN`.
- **Name Clearly**: Use descriptive CTE names (e.g., `top_models`) to show intent.

---

## 📝 Note

These questions are your spark! Customize them (e.g., add joins, tweak hierarchies) and add to your portfolio for recruiter wow-factor. Got a CTE brain-buster? Share it to elevate this repo! 🌟