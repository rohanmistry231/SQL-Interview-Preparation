# 🔄 Declaring Cursors - Setting Up Data Iteration

## 🌟 Overview

**Declaring Cursors** involves defining a cursor in SQL to prepare for **row-by-row processing** of a query’s result set. A cursor acts like a pointer to the result rows, enabling sequential access within stored procedures or scripts for complex logic.

In AI/ML, declaring cursors is key for **iterating through datasets**, such as processing `training_data` for per-row feature engineering. For freshers, it’s a **core interview topic**, often tested in questions about advanced SQL logic, stored procedures, and data pipeline customization.

---

## 📜 Syntax

```sql
-- Generic SQL (varies by database)
DECLARE cursor_name CURSOR FOR
    SELECT column(s) FROM table_name [WHERE condition];
```

- **Basic Example** (SQL Server syntax):
  ```sql
  DECLARE prediction_cursor CURSOR FOR
      SELECT model_id, score FROM predictions WHERE score > 0.5;
  ```
- **With Conditions** (PostgreSQL-style):
  ```sql
  DECLARE training_cursor CURSOR FOR
      SELECT feature1, label FROM training_data WHERE dataset_id = 101;
  ```

---

## 💡 Use Cases in AI/ML

- **Feature Engineering**: Declare a cursor to process `training_data` rows for custom metrics.
- **Model Validation**: Iterate `predictions` to check per-row accuracy thresholds.
- **Data Cleaning**: Define a cursor for `staging_table` to validate rows.
- **Experiment Analysis**: Process `results` rows for per-experiment summaries.
- **Pipeline Debugging**: Step through `logs` to identify row-level issues.

---

## 🔑 Key Features

- **Query Binding**: Ties a cursor to a specific `SELECT` query.
- **Row Access**: Prepares rows for sequential fetching.
- **Scope-Limited**: Exists within a procedure or session.
- **Flexible**: Supports any valid `SELECT` with filters or joins.

---

## ✅ Best Practices

- **Optimize Queries**: Keep the cursor’s `SELECT` simple to reduce overhead.
- **Name Clearly**: Use names like `prediction_cursor` to indicate purpose.
- **Limit Rows**: Use `WHERE` to minimize the result set for efficiency.
- **Test in Sandbox**: Declare cursors in a test environment first.

---

## ⚠️ Common Pitfalls

- **Heavy Queries**: Complex `SELECT` statements slow cursor performance.
- **Scope Errors**: Using cursors outside their defined session fails.
- **Syntax Variance**: Declaration syntax differs (e.g., SQL Server vs. Oracle).
- **Resource Locks**: Large result sets may lock tables unnecessarily.

---

## 📝 Additional Notes

- **Database Variations**:
  - **MySQL**: Limited cursor support; only in stored procedures.
  - **PostgreSQL**: Uses `DECLARE ... CURSOR` with flexible options.
  - **SQL Server**: Supports `DECLARE CURSOR` with `LOCAL`/`GLOBAL` scopes.
  - **Oracle**: Uses `CURSOR cursor_name IS SELECT ...` in PL/SQL.
- **Performance**: Avoid cursors for large datasets; prefer set-based SQL.
- **Scope**: Cursors are typically procedure-bound; global cursors are rare.