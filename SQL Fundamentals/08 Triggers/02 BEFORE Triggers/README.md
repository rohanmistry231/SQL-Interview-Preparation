# ⚡ BEFORE Triggers - Pre-Event Automation

## 🌟 Overview

**BEFORE Triggers** execute **before** a database event (`INSERT`, `UPDATE`, or `DELETE`) modifies a table, allowing validation or modification of data prior to the operation. They’re ideal for enforcing rules or transforming incoming data.

In AI/ML, `BEFORE` triggers are essential for **validating dataset quality**, like rejecting invalid `training_data` rows, or normalizing features before storage. For freshers, it’s a **common interview topic**, tested in questions about data integrity and preprocessing logic.

---

## 📜 Syntax

```sql
-- Generic SQL (varies by database)
CREATE TRIGGER trigger_name
BEFORE {INSERT | UPDATE | DELETE}
ON table_name
FOR EACH ROW
BEGIN
    -- Validation or modification logic
END;
```

- **Basic Example** (MySQL syntax):
  ```sql
  DELIMITER //
  CREATE TRIGGER NormalizeFeature
  BEFORE INSERT ON training_data
  FOR EACH ROW
  BEGIN
      SET NEW.feature1 = NEW.feature1 / 100;
  END //
  DELIMITER ;
  ```
- **Validation Example** (PostgreSQL-style):
  ```sql
  CREATE TRIGGER CheckModelAccuracy
  BEFORE UPDATE ON models
  FOR EACH ROW
  WHEN (NEW.accuracy < 0 OR NEW.accuracy > 1)
  BEGIN
      RAISE EXCEPTION 'Accuracy must be between 0 and 1';
  END;
  ```

---

## 💡 Use Cases in AI/ML

- **Feature Validation**: Reject `training_data` with null or out-of-range `feature1`.
- **Normalization**: Scale `features` before inserting into `test_data`.
- **Metadata Update**: Set `last_modified` before `experiments` updates.
- **Data Cleaning**: Transform `staging_table` rows before pipeline processing.
- **Model Constraints**: Enforce valid `accuracy` in `models` updates.

---

## 🔑 Key Features

- **Pre-Event Execution**: Runs before the database applies changes.
- **Data Modification**: Can alter `NEW` values for `INSERT`/`UPDATE`.
- **Validation Power**: Can abort operations with errors (database-dependent).
- **Row-Level**: Affects each row individually.

---

## ✅ Best Practices

- **Validate Early**: Use `BEFORE` for checks to avoid invalid data.
- **Keep Simple**: Minimize logic to maintain performance.
- **Use NEW Wisely**: Modify `NEW` fields carefully to avoid errors.
- **Test Extensively**: Simulate events in a sandbox to confirm behavior.

---

## ⚠️ Common Pitfalls

- **Overwriting Data**: Incorrect `NEW` assignments corrupt rows.
- **Performance Issues**: Complex logic slows bulk operations.
- **Error Handling**: Not all databases support aborting (e.g., MySQL limits).
- **Syntax Differences**: `NEW` access varies (e.g., SQL Server uses `inserted`).

---

## 📝 Additional Notes

- **Database Variations**:
  - **MySQL**: Limited to `NEW` modifications; no direct error raising.
  - **PostgreSQL**: Supports `RAISE EXCEPTION` for validation.
  - **SQL Server**: Uses `inserted` table; `RAISERROR` for aborts.
  - **Oracle**: Uses `:NEW` for modifications; supports exceptions.
- **Limitations**: MySQL doesn’t allow triggers to stop events directly.
- **Use Case**: Best for validation or transformation, not logging.