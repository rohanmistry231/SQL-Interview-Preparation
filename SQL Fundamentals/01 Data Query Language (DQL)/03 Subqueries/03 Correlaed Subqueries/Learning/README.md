# 🎉 Master Correlated Subqueries - Row-by-Row ML Magic!

## 🌟 Welcome

**Correlated Subqueries** run for each row of the outer query, perfect for row-specific ML comparisons like matching predictions to model metadata. They’re like a loop in SQL, checking conditions per row. This guide will teach you correlated subqueries with ML examples, boosting your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand the Loop**: Learn how correlated subqueries reference outer query rows.
2. **Study Syntax**: See how subqueries tie to outer tables.
3. **Run Examples**: Try the queries below in a database like PostgreSQL.
4. **Tweak Conditions**: Adjust subquery logic to explore results.
5. **ML Angle**: Use correlated subqueries for per-row ML data checks.

---

## 📜 Syntax

```sql
SELECT column1, column2, ...
FROM table_name t1
WHERE condition (SELECT column FROM table_name t2 WHERE t2.column = t1.column);
```

- **Example 1: Match Model Date**:
  ```sql
  SELECT prediction_id, model_id, score
  FROM predictions p
  WHERE EXISTS (
      SELECT 1 FROM models m WHERE m.model_id = p.model_id AND m.created_date > '2025-01-01'
  );
  ```
  *Finds predictions for models created after Jan 2025, like filtering recent ML data.*

- **Example 2: Above Model Average**:
  ```sql
  SELECT prediction_id, score
  FROM predictions p
  WHERE score > (
      SELECT AVG(score) FROM predictions p2 WHERE p2.model_id = p.model_id
  );
  ```
  *Grabs `score`s above their model’s average, great for ML outlier detection.*

- **Example 3: Model Name Check**:
  ```sql
  SELECT model_id, model_name
  FROM predictions p
  WHERE model_name = (
      SELECT model_name FROM models m WHERE m.model_id = p.model_id
  );
  ```
  *Verifies `model_name` matches `models` table, useful for ML data validation.*

---

## 💡 Practice Tips

- **Get Hands-On**: Use [SQLFiddle](http://sqlfiddle.com) or MySQL.
- **ML Use Case**: Correlated subqueries shine in row-level ML tasks (e.g., validating predictions, comparing metrics).
- **Try This**: Create `predictions` and `models`, then find predictions with above-average `score`s per `model_id`. Verify counts.
- **Tip**: Correlated subqueries can be slow—test with `EXPLAIN` to optimize.

---

## 🚀 Next Steps

- **Go Deeper**: Explore `Nested Subqueries` for layered logic or `Single-Row Subqueries` for simpler scalars.
- **Portfolio Boost**: Add a correlated subquery to `irohanportfolio.netlify.app`, explaining ML row-level analysis.
- **Challenge**: Find predictions from recently created models for a portfolio ML report.

Loop like a pro, and let’s make your SQL skills soar! 🌟