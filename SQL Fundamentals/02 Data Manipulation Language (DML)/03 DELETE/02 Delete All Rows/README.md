# 🗑️ Delete All Rows - Clear Your Table Completely

## 🌟 Overview

The **Delete All Rows** is a `DELETE` statement that removes **every row** from a table without conditions, effectively emptying it while preserving the table structure. It’s a powerful tool for resetting datasets or clearing test data. In AI/ML, deleting all rows is used to refresh staging tables, reset test environments, or prepare for new data loads.

---

## 📜 Syntax

```sql
DELETE FROM table_name;
```

- **Basic Example**:
  ```sql
  DELETE FROM predictions;
  ```
- **With Transaction**:
  ```sql
  BEGIN;
  DELETE FROM predictions;
  COMMIT;
  ```
- **Alternative (Some DBs)**:
  ```sql
  TRUNCATE TABLE predictions;
  ```

---

## 💡 Use Cases in AI/ML

- **Test Reset**: Clear test predictions (e.g., `DELETE FROM test_predictions`).
- **Staging Cleanup**: Empty staging tables (e.g., `DELETE FROM staging_data`).
- **Data Refresh**: Remove all records before reloading (e.g., `DELETE FROM model_outputs`).
- **Environment Prep**: Reset tables for new experiments (e.g., `DELETE FROM experiment_logs`).

---

## 🔑 Key Features

- **Complete Removal**: Deletes all rows in one statement.
- **Structure Preserved**: Keeps table schema, indexes, and constraints intact.
- **Fast Execution**: Typically faster than conditional deletes for full clears.
- **Constraint Awareness**: May be restricted by foreign keys.

---

## ✅ Best Practices

- **Confirm Intent**: Double-check you want all rows gone—there’s no undo without backups.
- **Use Transactions**: Enclose in `BEGIN`/`COMMIT` or `ROLLBACK` for safety.
- **Consider TRUNCATE**: Use `TRUNCATE` for faster clears if constraints allow.
- **Backup Data**: Save critical data before deleting everything.

---

## ⚠️ Common Pitfalls

- **Accidental Deletion**: Running without a `WHERE` clause clears everything unintentionally.
- **Foreign Key Issues**: Deletes may fail if rows are referenced elsewhere.
- **No Rollback**: Without transactions, deleted data is gone permanently.
- **Confusion with DROP**: `DELETE` keeps the table; `DROP` removes it entirely.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL/PostgreSQL/SQL Server: `DELETE FROM table_name` works universally.
  - PostgreSQL: `TRUNCATE` is faster but skips triggers; `DELETE` supports `RETURNING`.
- **Performance**: `TRUNCATE` resets auto-increment counters; `DELETE` doesn’t.
- **Restrictions**: Foreign keys may block deletion unless cascaded or disabled.