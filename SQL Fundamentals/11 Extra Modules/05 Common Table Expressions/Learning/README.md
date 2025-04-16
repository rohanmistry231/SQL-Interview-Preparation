# 🎉 Master Common Table Expressions - Simplify Your ML Queries!

## 🌟 Welcome

**Common Table Expressions (CTEs)** create temporary result sets, making ML queries like recursive model hierarchies or clean aggregations easier. They’re your tool for readable SQL. This guide will show you CTEs with ML examples, boosting your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Concept**: Understand how CTEs act like named subqueries.
2. **Learn Syntax**: Study `WITH` clause and recursion.
3. **Run Examples**: Try the CTEs below in a database like PostgreSQL.
4. **Test Clarity**: Break down complex queries with CTEs.
5. **ML Angle**: Use CTEs for ML data preprocessing.

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

- **Example 1: High-Score CTE**:
  ```sql
  WITH HighScores AS (
      SELECT model_id, score
      FROM predictions
      WHERE score >= 0.9
  )
  SELECT model_id, AVG(score) AS avg_high_score
  FROM HighScores
  GROUP BY model_id;
  ```
  *Aggregates high ML prediction scores.*

- **Example 2: Metric Filter CTE**:
  ```sql
  WITH RecentMetrics AS (
      SELECT model_id, accuracy
      FROM model_metrics
      WHERE eval_date >= '2025-04-01'
  )
  SELECT model_id, MAX(accuracy) AS max_accuracy
  FROM RecentMetrics
  GROUP BY model_id;
  ```
  *Finds top ML model accuracies.*

- **Example 3: Recursive CTE (Model Hierarchy)**:
  ```sql
  WITH RECURSIVE ModelChain AS (
      SELECT model_id, model_name, 1 AS level
      FROM predictions
      WHERE model_name = 'BaseModel'
      UNION ALL
      SELECT p.model_id, p.model_name, mc.level + 1
      FROM predictions p
      JOIN ModelChain mc ON p.model_name = mc.model_name || '_v' || mc.level
  )
  SELECT model_id, model_name, level
  FROM ModelChain;
  ```
  *Traces ML model versions (hypothetical naming).*

---

## 💡 Practice Tips

- **Get Hands-On**: Use MySQL Workbench or [pgAdmin](https://www.pgadmin.org) for CTEs.
- **ML Use Case**: CTEs clean ML queries, like prepping data for training.
- **Try This**: Run the high-score CTE, verify with a subquery version.
- **Tip**: Use recursive CTEs sparingly—test base and recursive parts separately.

---

## 🚀 Next Steps

- **Go Deeper**: Explore `Window Functions` for analytics or `Dynamic Queries` for flexibility.
- **Portfolio Boost**: Add a CTE to `irohanportfolio.netlify.app`, explaining ML query clarity.
- **Challenge**: Use a CTE to preprocess ML data in a portfolio dataset.

Simplify like a boss, and let’s make your SQL skills soar! 🌟