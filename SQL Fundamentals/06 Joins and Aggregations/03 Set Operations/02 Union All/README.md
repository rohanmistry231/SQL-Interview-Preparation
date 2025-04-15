# 🔄 Union All - Merging with Duplicates

## 🌟 Overview

The **UNION ALL** operator in SQL combines the results of two or more `SELECT` queries into a **single result set**, **keeping all rows**, including duplicates. It’s faster than `UNION` since it skips deduplication, ideal when duplicates are acceptable or expected.

In AI/ML, `UNION ALL` is used for **merging raw datasets** or combining model outputs without filtering duplicates, such as stacking prediction logs. For freshers, it’s a **common interview topic**, tested alongside `UNION` for performance and logic questions.

---

## 📜 Syntax

```sql
SELECT column(s) FROM table1
UNION ALL
SELECT column(s) FROM table2;
```

- **Basic Example**:
  ```sql
  SELECT user_id FROM training_data_2023
  UNION ALL
  SELECT user_id FROM training_data_2024;
  ```
- **With Multiple Columns**:
  ```sql
  SELECT model_id, score FROM predictions_v1
  UNION ALL
  SELECT model_id, score FROM predictions_v2;
  ```

---

## 💡 Use Cases in AI/ML

- **Log Aggregation**: Combine `logs` from multiple pipelines with duplicates.
- **Prediction Stacking**: Merge `predictions` from different runs for analysis.
- **Dataset Appending**: Unify `training_data` from sources with overlapping records.
- **Experiment Results**: Collect all `results` across `experiments` without deduplication.
- **Streaming Data**: Append real-time `events` to historical data.

---

## 🔑 Key Features

- **Keeps Duplicates**: Includes all rows, preserving multiplicity.
- **Column Matching**: Requires identical column counts and compatible types.
- **High Performance**: Faster than `UNION` due to no deduplication.
- **Vertical Stacking**: Concatenates query results directly.

---

## ✅ Best Practices

- **Verify Column Alignment**: Ensure matching columns across queries.
- **Filter Early**: Use `WHERE` to reduce rows before `UNION ALL`.
- **Use for Large Data**: Prefer `UNION ALL` over `UNION` for speed when duplicates are okay.
- **Test Output**: Check row counts to confirm expected duplicates.

---

## ⚠️ Common Pitfalls

- **Column Errors**: Mismatched columns cause query failures.
- **Unintended Duplicates**: Keeping duplicates may skew analysis if unexpected.
- **No Sorting**: Results are unordered without `ORDER BY`.
- **Overuse**: Using when deduplication is needed wastes resources.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL/PostgreSQL/SQL Server: Standard `UNION ALL` syntax.
  - Oracle: Consistent behavior; optimized for performance.
- **Performance**: Significantly faster than `UNION` for large datasets.
- **Sorting**: Apply `ORDER BY` after the final `UNION ALL`.