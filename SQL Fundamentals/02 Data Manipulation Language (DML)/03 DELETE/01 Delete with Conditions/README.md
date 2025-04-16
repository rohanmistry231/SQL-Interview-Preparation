# 🗑️ Delete with Conditions - Remove Data Selectively

## 🌟 Overview

The **Delete with Conditions** is a `DELETE` statement that removes **specific rows** from a table based on conditions defined in a `WHERE` clause. It’s the go-to method for targeted data cleanup, ideal for purging invalid ML predictions or outdated records. In AI/ML, conditional deletes are essential for maintaining dataset quality, ensuring only relevant data fuels your models.

---

## 📜 Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

- **Basic Example**:
  ```sql
  DELETE FROM predictions
  WHERE score < 0.5;
  ```
- **Multi-Condition**:
  ```sql
  DELETE FROM predictions
  WHERE model_id = 101 AND prediction_date < '2025-04-01';
  ```
- **Pattern-Based**:
  ```sql
  DELETE FROM predictions
  WHERE model_name LIKE 'Old_Model%';
  ```

---

## 💡 Use Cases in AI/ML

- **Data Cleaning**: Remove low-confidence predictions (e.g., `DELETE FROM predictions WHERE score < 0.3`).
- **Obsolete Data**: Purge old records (e.g., `DELETE FROM predictions WHERE prediction_date < '2025-01-01'`).
- **Error Removal**: Delete invalid entries (e.g., `DELETE FROM predictions WHERE score IS NULL`).
- **Selective Pruning**: Clear specific model data (e.g., `DELETE FROM predictions WHERE model_id = 102`).

---

## 🔑 Key Features

- **Precision Removal**: `WHERE` clause targets only matching rows.
- **Flexible Conditions**: Supports comparisons, logical operators, and patterns (e.g., `LIKE`).
- **Atomic Operation**: Deletes all matching rows or none (with transactions).
- **Constraint Awareness**: Respects foreign keys and other table rules.

---

## ✅ Best Practices

- **Test Conditions**: Run `SELECT COUNT(*) WHERE ...` to preview rows to delete.
- **Use Indexes**: Ensure `WHERE` columns are indexed for faster execution.
- **Use Transactions**: Wrap deletes in `BEGIN`/`COMMIT` or `ROLLBACK` for safety.
- **Be Specific**: Craft precise conditions to avoid removing unintended rows.

---

## ⚠️ Common Pitfalls

- **Missing WHERE**: Forgetting `WHERE` deletes all rows (use *Delete All Rows* for that).
- **Vague Conditions**: Overly broad `WHERE` clauses remove too much data.
- **Constraint Violations**: Deletes blocked by foreign keys cause errors.
- **Logic Errors**: Incorrect `AND`/`OR` usage deletes wrong rows.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL/PostgreSQL/SQL Server: Syntax is identical for conditional deletes.
  - PostgreSQL: Supports `RETURNING` to view deleted rows (e.g., `DELETE ... RETURNING prediction_id`).
- **Performance**: Conditional deletes on indexed columns are faster; avoid table scans.
- **Safety**: Use `LIMIT` (MySQL) or test in a sandbox to cap deletions.