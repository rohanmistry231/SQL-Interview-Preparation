
# 🧹 Truncate Table - Clearing All Data

## 🌟 Overview

The **TRUNCATE TABLE** statement in SQL is a DDL command used to **delete all rows** from a table while preserving its structure, including columns, constraints, and indexes. Unlike `DROP TABLE`, it keeps the table intact for reuse. In AI/ML, `TRUNCATE TABLE` is useful for resetting datasets, clearing temporary results, or preparing tables for new data during experiments.

---

## 📜 Syntax

```sql
TRUNCATE TABLE table_name [CASCADE | RESTRICT];
```

- **Basic Example**:
  ```sql
  TRUNCATE TABLE temp_predictions;
  ```
- **With Cascade**:
  ```sql
  TRUNCATE TABLE orders CASCADE;
  ```

---

## 💡 Use Cases in AI/ML

- **Dataset Reset**: Clear training data for new runs (e.g., `TRUNCATE TABLE training_data`).
- **Experiment Cleanup**: Remove temporary results (e.g., `TRUNCATE TABLE test_metrics`).
- **Data Refresh**: Prepare tables for fresh data (e.g., `TRUNCATE TABLE staging_table`).
- **Performance Testing**: Reset tables for benchmarking (e.g., `TRUNCATE TABLE performance_logs`).

---

## 🔑 Key Features

- **Data Removal**: Deletes all rows, leaving the table structure intact.
- **Speed**: Faster than `DELETE` as it doesn’t scan rows or log individual deletions.
- **CASCADE Option**: Handles dependent foreign keys in some databases.
- **Auto-Commit**: Changes are permanent, like other DDL commands.

---

## ✅ Best Practices

- **Verify Need**: Ensure data is no longer required before truncating.
- **Use CASCADE Carefully**: Only use when dependent tables should also be cleared.
- **Backup Data**: Save critical data before truncation, as recovery is difficult.
- **Combine with Transactions**: Some databases allow `TRUNCATE` in transactions for safety.

---

## ⚠️ Common Pitfalls

- **Irreversible Action**: Truncation cannot be undone without backups.
- **Foreign Key Issues**: Truncating tables with dependencies fails without `CASCADE`.
- **Trigger Impact**: Unlike `DELETE`, `TRUNCATE` may not fire row-level triggers.
- **Misuse vs. DELETE**: Using `TRUNCATE` when selective deletion is needed removes too much data.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL: Supports `CASCADE` for foreign keys.
  - PostgreSQL: Allows `CASCADE` and `RESTART IDENTITY` for sequences.
  - SQL Server: Doesn’t support `CASCADE`; drop constraints first.
- **Performance**: Ideal for large tables due to minimal logging compared to `DELETE`.
- **Restrictions**: Cannot truncate tables referenced by active views or cursors in some systems.