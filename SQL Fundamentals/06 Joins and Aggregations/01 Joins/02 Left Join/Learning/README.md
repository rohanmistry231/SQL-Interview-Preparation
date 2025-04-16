# 🎉 Master LEFT JOIN - Keep All Your ML Base Data!

## 🌟 Welcome

The **LEFT JOIN** keeps all rows from the left table, matching right table rows where possible, ideal for including all ML predictions even without model details. It’s your tool for complete datasets. This guide will teach you `LEFT JOIN` with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Inclusion**: Learn how `LEFT JOIN` retains all left table rows.
2. **Study Syntax**: See how to join with `ON` and handle nulls.
3. **Run Examples**: Try the queries below in a database like MySQL.
4. **Test Results**: Check for unmatched rows with nulls.
5. **ML Spin**: Use `LEFT JOIN` to analyze incomplete ML data.

---

## 📜 Syntax

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```

- **Example 1: All Predictions**:
  ```sql
  SELECT p.prediction_id, p.score, m.model_name
  FROM predictions p
  LEFT JOIN models m
  ON p.model_id = m.model_id;
  ```
  *Includes all ML predictions, with nulls for missing models.*

- **Example 2: Metrics with Models**:
  ```sql
  SELECT mm.metric_id, mm.accuracy, m.model_name
  FROM model_metrics mm
  LEFT JOIN models m
  ON mm.model_id = m.model_id;
  ```
  *Keeps all ML metrics, even without model info.*

- **Example 3: Filter Unmatched**:
  ```sql
  SELECT p.prediction_id, p.score
  FROM predictions p
  LEFT JOIN models m
  ON p.model_id = m.model_id
  WHERE m.model_id IS NULL;
  ```
  *Finds ML predictions without linked models.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: `LEFT JOIN` ensures no ML predictions are lost, even if metadata is incomplete.
- **Try This**: Join `predictions` to `models` with `LEFT JOIN`, check for null `model_name`s.
- **Note**: Nulls appear for unmatched rows—use `IS NULL` to find gaps.

---

## 🚀 Next Steps

- **Level Up**: Try `Right Join` for opposite behavior or `Inner Join` for matches.
- **Portfolio Win**: Add a `LEFT JOIN` query to `irohanportfolio.netlify.app`, showing ML data inclusion.
- **Challenge**: Find unmatched ML predictions in a portfolio dataset.

Include like a pro, and let’s rock your SQL journey! 🌟