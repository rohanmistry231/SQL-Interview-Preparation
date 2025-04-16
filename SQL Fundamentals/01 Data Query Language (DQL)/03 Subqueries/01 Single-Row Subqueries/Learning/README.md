# 🎉 Master Single-Row Subqueries - Fetch ML Scalars with Precision!

## 🌟 Welcome

**Single-Row Subqueries** return one row and one column, perfect for grabbing a single ML metric like the highest score or a model’s creation date. They’re your secret weapon for embedding scalar values in queries. This guide will walk you through learning single-row subqueries with ML-themed examples, making your *ML-Interview-Preparation-Hub* shine! 🚀

---

## 🛤️ Learning Path

1. **Grasp the Concept**: Understand that single-row subqueries return one value for comparisons.
2. **Study the Syntax**: Learn where subqueries fit in `SELECT` or `WHERE`.
3. **Run Examples**: Try the queries below in a database like PostgreSQL or MySQL.
4. **Tweak Queries**: Modify subqueries to test different scalars.
5. **Apply to ML**: Use single-row subqueries to fetch metrics for ML model analysis.

---

## 📜 Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column = (SELECT column FROM table_name WHERE condition);
-- OR
SELECT column1, (SELECT column FROM table_name WHERE condition) AS subquery_result
FROM table_name;
```

- **Example 1: Compare to Max Score**:
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE score = (SELECT MAX(score) FROM predictions);
  ```
  *Finds predictions with the highest `score`, like identifying top ML performers.*

- **Example 2: Fetch Model Date**:
  ```sql
  SELECT model_id, model_name,
         (SELECT created_date FROM models WHERE models.model_id = predictions.model_id) AS created_date
  FROM predictions;
  ```
  *Adds each model’s `created_date`, great for ML metadata analysis.*

- **Example 3: Filter by Average**:
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE score > (SELECT AVG(score) FROM predictions);
  ```
  *Grabs above-average `score`s, useful for ML model evaluation.*

---

## 💡 Practice Tips

- **Tool Up**: Use [SQLFiddle](http://sqlfiddle.com) or a local DB to test queries.
- **ML Use Case**: Single-row subqueries help fetch benchmarks (e.g., max score, average metric) for ML comparisons.
- **Try This**: Create `predictions` with 10 rows, then find rows matching the lowest `score`. Verify with `SELECT MIN(score)`.
- **Debug**: Ensure subqueries return exactly one value—multiple rows cause errors!

---

## 🚀 Next Steps

- **Deepen Skills**: Explore `Multi-Row Subqueries` for lists or `Correlated Subqueries` for row-by-row logic.
- **Portfolio Boost**: Add a single-row subquery to `irohanportfolio.netlify.app`, explaining its ML metric role.
- **Challenge**: Find predictions matching the earliest `prediction_date` for a portfolio ML report.

Query like a pro, and let’s make your SQL skills sparkle! 🌟