# 🎉 Master Nested Subqueries - Layer Your ML Queries Like a Boss!

## 🌟 Welcome

**Nested Subqueries** are subqueries inside subqueries, letting you build complex ML data pipelines like finding top-scoring predictions from select models. They’re your tool for multi-step logic in one query. This guide will show you how to learn nested subqueries with ML examples, powering your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Layers**: Understand how subqueries nest for step-by-step logic.
2. **Learn Syntax**: Study nested subqueries in `WHERE` or `SELECT`.
3. **Run Examples**: Try the queries below in a database like MySQL.
4. **Build Complexity**: Add layers to subqueries to test deeper logic.
5. **ML Spin**: Use nested subqueries for multi-level ML data filtering.

---

## 📜 Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column IN (
    SELECT column FROM table_name WHERE condition IN (
        SELECT column FROM table_name WHERE condition
    )
);
```

- **Example 1: Top Models’ Scores**:
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE model_id IN (
      SELECT model_id FROM models WHERE model_id IN (
          SELECT model_id FROM predictions WHERE score > 0.9
      )
  );
  ```
  *Finds predictions from models with high scores, like selecting elite ML performers.*

- **Example 2: Recent High Scores**:
  ```sql
  SELECT model_id, model_name
  FROM predictions
  WHERE score > (
      SELECT AVG(score) FROM predictions WHERE model_id IN (
          SELECT model_id FROM models WHERE created_date > '2025-01-01'
      )
  );
  ```
  *Grabs high `score`s from recent models, great for ML trend analysis.*

- **Example 3: Nested Validation**:
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE model_name IN (
      SELECT model_name FROM models WHERE model_id IN (
          SELECT model_id FROM predictions WHERE prediction_date = '2025-01-01'
      )
  );
  ```
  *Filters predictions by model names from specific dates, useful for ML data audits.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: Nested subqueries help build complex ML filters (e.g., models by performance and date).
- **Try This**: Create `predictions` and `models`, then nest a subquery to find `score`s from top models. Verify with `SELECT COUNT(*)`.
- **Note**: Keep nesting clear—too many layers can slow queries. Test with `EXPLAIN`.

---

## 🚀 Next Steps

- **Level Up**: Combine nested subqueries with `Correlated Subqueries` or `Multi-Row Subqueries` for advanced logic.
- **Portfolio Win**: Add a nested subquery to `irohanportfolio.netlify.app`, showing ML data layering.
- **Challenge**: Find high `score`s from 2025 models for a portfolio ML report.

Layer like a boss, and let’s rock your SQL game! 🌟