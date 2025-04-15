# ↩️ ROLLBACK - Undoing Your Changes

## 🌟 Overview

The **ROLLBACK** command in SQL is a TCL statement used to **undo all changes** made during the current transaction, restoring the database to its state before the transaction began. It’s a safety net for handling errors, ensuring data integrity by canceling failed or incorrect operations. ROLLBACK supports the ACID model, particularly Atomicity and Consistency.

In AI/ML, `ROLLBACK` is crucial for recovering from failed ETL jobs, correcting model updates, or discarding faulty data imports. For freshers, `ROLLBACK` is a **key interview topic**, often tested in scenarios involving error recovery and transaction failure.

---

## 📜 Syntax

```sql
ROLLBACK [WORK];
```

- **Basic Example**:
  ```sql
  BEGIN;
  INSERT INTO training_data (sample_id, feature1, label) VALUES (1, -999, 'invalid');
  ROLLBACK;
  ```
- **With Error Handling**:
  ```sql
  BEGIN;
  UPDATE models SET accuracy = NULL WHERE model_id = 101;
  -- Error detected (NULL invalid)
  ROLLBACK;
  ```

---

## 💡 Use Cases in AI/ML

- **ETL Recovery**: Undo failed data loads (e.g., `ROLLBACK` if `staging_table` import fails).
- **Model Safety**: Revert erroneous updates (e.g., `ROLLBACK` after invalid `models` update).
- **Data Validation**: Cancel invalid inserts (e.g., `ROLLBACK` if `training_data` has bad values).
- **Experiment Cleanup**: Discard test changes (e.g., `ROLLBACK` after trial `predictions` insert).
- **Pipeline Protection**: Revert feature updates (e.g., `ROLLBACK` if `feature_table` transformation fails).

---

## 🔑 Key Features

- **Full Reversal**: Undoes all transaction changes since the last `BEGIN`.
- **Error Recovery**: Restores database consistency after failures.
- **ACID Compliance**: Ensures Atomicity by treating transactions as all-or-nothing.
- **No Partial Undo**: Affects the entire transaction unless using savepoints.

---

## ✅ Best Practices

- **Use Explicitly**: Start transactions with `BEGIN` to control rollback scope.
- **Rollback Early**: Issue `ROLLBACK` immediately after detecting errors to free resources.
- **Validate Data**: Check inputs before operations to minimize rollbacks.
- **Monitor Transactions**: Keep transactions small to reduce rollback overhead.

---

## ⚠️ Common Pitfalls

- **No Rollback Without BEGIN**: Auto-commit modes prevent rollback in some databases.
- **Large Rollbacks**: Undoing big transactions can be slow and lock resources.
- **Unintended Scope**: Rolling back forgets all changes, not just errors, without savepoints.
- **Connection Issues**: Open transactions without `ROLLBACK` can hang connections.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL: Requires `START TRANSACTION` for rollback; auto-commit disables it.
  - PostgreSQL: Supports `ROLLBACK TO SAVEPOINT` for partial undo.
  - SQL Server: Uses `ROLLBACK TRANSACTION` for named transactions.
- **Performance**: Rollback is faster than commit but may still impact large datasets.
- **Pairing**: Combine with `COMMIT` and error checks for robust workflows.