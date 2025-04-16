# 🎉 Master UNION ALL - Stack Your ML Data Fast!

## 🌟 Welcome

The **UNION ALL** operator combines rows from multiple queries, keeping all rows including duplicates, ideal for quick ML dataset merges like prediction logs. It’s your tool for speed and volume. This guide will teach you `UNION ALL` with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Speed**: Learn how `UNION ALL` includes all rows without deduplication.
2. **Study Syntax**: See how it mirrors `UNION` but runs faster.
3. **Run Examples**: Try the queries below in a database like MySQL.
4. **Test Volume**: Check for duplicate rows in results.
5. **ML Spin**: Use `UNION ALL` to bulk-combine ML data.

---

## 📜 Syntax

```sql
SELECT column1, column2, ...
FROM table1
[WHERE condition]
UNION ALL
SELECT column1, column2, ...
FROM table2
[WHERE condition];
```

- **Example 1: Stack Predictions**:
  ```sql
  SELECT prediction_id, score, model_name
  FROM predictions
  UNION ALL
  SELECT prediction_id, score, model_name
  FROM archive_predictions;
  ```
  *Merges all ML predictions, keeping duplicates.*

- **Example 2: Recent Data Merge**:
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE prediction_date >= '2025-04-01'
  UNION ALL
  SELECT prediction_id, score
  FROM archive_predictions
  WHERE prediction_date >= '2025-04-01';
  ```
  *Combines recent ML predictions from both tables.*

- **Example 3: Mixed Metrics**:
  ```sql
  SELECT model_id, accuracy AS metric
  FROM model_metrics
  UNION ALL
  SELECT model_id, score AS metric
  FROM predictions;
  ```
  *Stacks ML metrics and scores for raw analysis.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: `UNION ALL` speeds up ML data pipelines, like combining logs for training.
- **Try This**: Add duplicate rows to `predictions` and `archive_predictions`, run `UNION ALL`, and count rows with `SELECT COUNT(*)`.
- **Note**: `UNION ALL` is faster than `UNION`—use it when duplicates are okay or expected.

---

## 🚀 Next Steps

- **Level Up**: Compare with `Union` or try `Except` for differences.
- **Portfolio Win**: Add a `UNION ALL` query to `irohanportfolio.netlify.app`, showing ML data stacking.
- **Challenge**: Stack ML logs from multiple tables in a portfolio dataset.

Stack like a boss, and let’s rock your SQL journey! 🌟