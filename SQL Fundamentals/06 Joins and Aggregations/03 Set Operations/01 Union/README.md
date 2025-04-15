# 🔄 Union - Merging with Deduplication

## 🌟 Overview

The **UNION** operator in SQL combines the results of two or more `SELECT` queries into a **single result set**, **removing duplicate rows**. It’s ideal for merging distinct data from multiple sources while ensuring uniqueness.

In AI/ML, `UNION` is crucial for **deduplicating datasets**, such as combining unique records from different data sources for training. For freshers, it’s a **core interview topic**, frequently tested in questions about data consolidation and query merging.

---

## 📜 Syntax

```sql
SELECT column(s) FROM table1
UNION
SELECT column(s) FROM table2;
```

- **Basic Example**:
  ```sql
  SELECT user_id FROM training_data_2023
  UNION
  SELECT user_id FROM training_data_2024;
  ```
- **With Multiple Columns**:
  ```sql
  SELECT model_id, name FROM models_v1
  UNION
  SELECT model_id, name FROM models_v2;
  ```

---

## 💡 Use Cases in AI/ML

- **Dataset Merging**: Combine `training_data` from multiple years without duplicates.
- **Feature Deduplication**: Merge `features` from different sources for unique attributes.
- **Experiment Consolidation**: Unify `results` from various `experiments` for analysis.
- **User Analysis**: Collect unique `user_id` from `orders` and `reviews`.
- **Data Cleaning**: Merge `logs` from pipelines to remove redundant entries.

---

## 🔑 Key Features

- **Deduplication**: Automatically removes duplicate rows based on all columns.
- **Column Matching**: Queries must have the same number and compatible types of columns.
- **Set-Based**: Treats results as sets, ignoring order unless sorted.
- **Stacking Results**: Vertically combines rows from each query.

---

## ✅ Best Practices

- **Match Columns**: Ensure identical column counts and types across queries.
- **Limit Scope**: Use `WHERE` to reduce rows before `UNION` for efficiency.
- **Test Small**: Verify deduplication with small datasets first.
- **Consider UNION ALL**: Use `UNION ALL` if duplicates are acceptable for speed.

---

## ⚠️ Common Pitfalls

- **Column Mismatch**: Differing column counts or types cause errors.
- **Performance Cost**: Deduplication is slower than `UNION ALL` on large datasets.
- **Unexpected Duplicates**: Misaligned columns prevent proper deduplication.
- **Sorting Oversight**: Results are unordered unless `ORDER BY` is used.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL/PostgreSQL/SQL Server: Standard `UNION` syntax.
  - Oracle: Consistent behavior; supports `UNION` with subqueries.
- **Performance**: Deduplication requires sorting, impacting large datasets.
- **Sorting**: Add `ORDER BY` after the final `UNION` for sorted output.