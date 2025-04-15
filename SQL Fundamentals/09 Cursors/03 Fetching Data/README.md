# 🔄 Fetching Data - Retrieving Rows from Cursors

## 🌟 Overview

**Fetching Data** from a cursor retrieves the **next row** (or a set of rows) from the cursor’s result set, allowing row-by-row processing in stored procedures or scripts. It moves the cursor’s pointer forward, assigning row values to variables for manipulation.

In AI/ML, fetching data is vital for **processing datasets iteratively**, like validating `predictions` or transforming `training_data` rows. For freshers, it’s a **key interview topic**, often tested in questions about cursor-based logic and advanced SQL workflows.

---

## 📜 Syntax

```sql
-- Generic SQL (varies by database)
FETCH cursor_name INTO variable1, variable2, ...;
```

- **Basic Example** (SQL Server syntax):
  ```sql
  DECLARE prediction_cursor CURSOR FOR
      SELECT model_id, score FROM predictions;
  DECLARE @ModelID INT, @Score FLOAT;
  OPEN prediction_cursor;
  FETCH NEXT FROM prediction_cursor INTO @ModelID, @Score;
  ```
- **With Loop** (PostgreSQL-style):
  ```sql
  DO $$
  DECLARE
      training_cursor CURSOR FOR SELECT feature1 FROM training_data;
      v_feature FLOAT;
  BEGIN
      OPEN training_cursor;
      LOOP
          FETCH training_cursor INTO v_feature;
          EXIT WHEN NOT FOUND;
          -- Process v_feature
      END LOOP;
  END $$;
  ```

---

## 💡 Use Cases in AI/ML

- **Prediction Validation**: Fetch `predictions` rows to check score ranges.
- **Feature Engineering**: Retrieve `training_data` rows for per-row calculations.
- **Error Logging**: Process `logs` rows to flag anomalies.
- **Experiment Analysis**: Fetch `results` rows for custom aggregations.
- **Data Reformatting**: Retrieve `legacy_data` rows for ML-ready transformations.

---

## 🔑 Key Features

- **Row Retrieval**: Moves cursor to the next row and assigns values.
- **Variable Binding**: Maps columns to variables for processing.
- **Loop Support**: Enables iteration with `FETCH` in loops.
- **End Detection**: Signals when no more rows remain.

---

## ✅ Best Practices

- **Match Variables**: Ensure variable types match column types.
- **Use Loops**: Combine `FETCH` with loops for full iteration.
- **Check End**: Detect end-of-data (e.g., `NOT FOUND` in PostgreSQL).
- **Optimize Fetching**: Fetch only needed columns to reduce overhead.

---

## ⚠️ Common Pitfalls

- **Type Mismatches**: Wrong variable types cause runtime errors.
- **Unopened Cursor**: Fetching before `OPEN` fails.
- **Infinite Loops**: Missing end checks risks endless iteration.
- **Performance Cost**: Fetching large datasets row-by-row is slow.

---

## 📝 Additional Notes

- **Database Variations**:
  - **MySQL**: Uses `FETCH cursor_name INTO var1, ...` in procedures.
  - **PostgreSQL**: Supports `FETCH` with `NOT FOUND` for loop exits.
  - **SQL Server**: Uses `FETCH NEXT FROM ... INTO`; supports `@@FETCH_STATUS`.
  - **Oracle**: Uses `FETCH cursor_name INTO var1, ...` with `%NOTFOUND`.
- **Performance**: Cursors are slower than set-based queries; use judiciously.
- **Bulk Fetch**: Some databases (e.g., Oracle) allow fetching multiple rows.