# 🌳 Common Table Expressions - Structured Queries for ML

## 🌟 Overview

**Common Table Expressions (CTEs)** define temporary result sets within a query, like named subqueries, simplifying complex logic. Using `WITH`, they support recursive and non-recursive queries, ideal for hierarchical ML data. In AI/ML, CTEs streamline feature engineering, recursive model evaluations, or graph-based analyses.

---

## 📜 Syntax

```sql
WITH cte_name AS (
    SELECT column1, column2
    FROM table_name
    WHERE condition
)
SELECT * FROM cte_name;
```

- **Basic CTE**:
  ```sql
  WITH high_scores AS (
      SELECT model_id, score
      FROM predictions
      WHERE score > 0.9
  )
  SELECT * FROM high_scores;
  ```
- **Recursive CTE**:
  ```sql
  WITH RECURSIVE feature_tree AS (
      SELECT feature_id, parent_id, name
      FROM features
      WHERE parent_id IS NULL
      UNION ALL
      SELECT f.feature_id, f.parent_id, f.name
      FROM features f
      INNER JOIN feature_tree ft ON f.parent_id = ft.feature_id
  )
  SELECT * FROM feature_tree;
  ```
- **Multiple CTEs**:
  ```sql
  WITH scores AS (
      SELECT model_id, AVG(score) AS avg_score
      FROM predictions
      GROUP BY model_id
  ), top_models AS (
      SELECT model_id
      FROM scores
      WHERE avg_score > 0.85
  )
  SELECT * FROM top_models;
  ```

---

## 💡 Use Cases in AI/ML

- **Feature Hierarchies**: Traverse feature graphs with recursive CTEs (e.g., `WITH RECURSIVE feature_tree`).
- **Pipeline Staging**: Break complex ML queries into steps (e.g., filter, aggregate, join).
- **Model Analysis**: Chain CTEs for multi-step evaluation (e.g., compute metrics, then rank).
- **Graph ML**: Process node-edge relationships for recommendation systems.

---

## 🔑 Key Features

- **Modularity**: Break queries into readable, reusable blocks.
- **Recursion**: Handle hierarchical or iterative ML data (e.g., trees, graphs).
- **Chaining**: Combine multiple CTEs for staged processing.
- **Temporary Scope**: CTEs exist only for the query, reducing clutter.

---

## ✅ Best Practices

- **Name Intuitively**: Use descriptive CTE names (e.g., `high_scores` vs. `cte1`).
- **Limit Recursion**: Cap recursive depth to avoid infinite loops (e.g., `MAXRECURSION` in SQL Server).
- **Optimize Subqueries**: Index tables used in CTEs for performance.
- **Keep It Clear**: Avoid nesting too many CTEs—flatten where possible.

---

## ⚠️ Common Pitfalls

- **Recursion Errors**: Missing base cases cause infinite loops—always define a termination condition.
- **Performance Drag**: Unoptimized CTEs (e.g., no indexes) slow large datasets.
- **Overuse**: Using CTEs for simple queries adds unnecessary complexity—use subqueries instead.
- **DB Limitations**: MySQL < 8.0 doesn’t support CTEs—use temporary tables as a workaround.

---

## 📝 Additional Notes

- **Database Variations**: PostgreSQL, SQL Server, MySQL 8.0+ support CTEs; MySQL 5.x requires subqueries.
- **Recursion Limits**: SQL Server defaults to 100 recursions—adjust with `OPTION (MAXRECURSION n)`.
- **Performance**: CTEs materialize in some DBs (e.g., SQL Server)—check with `EXPLAIN`.
- **Debugging**: Break CTEs into separate queries to isolate errors.