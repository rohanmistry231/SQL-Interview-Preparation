# 🛠️ Calling Procedures - Executing Stored Logic

## 🌟 Overview

**Calling Stored Procedures** involves invoking a stored procedure to **execute its predefined SQL logic**, optionally passing parameters or retrieving results. It’s the mechanism to leverage reusable code, improving efficiency and consistency.

In AI/ML, calling procedures is essential for **running automated tasks**, like scoring models or updating datasets in pipelines. For freshers, it’s a **common interview topic**, tested in questions about executing database logic and integrating SQL into workflows.

---

## 📜 Syntax

```sql
-- Generic SQL (varies by database)
CALL procedure_name(param1, param2);
-- or
EXEC procedure_name param1, param2;
```

- **Basic Example** (MySQL syntax):
  ```sql
  CALL CleanTrainingData();
  ```
- **With Parameters** (SQL Server syntax):
  ```sql
  DECLARE @Count INT;
  EXEC GetPredictionCount @ModelID = 101, @Count = @Count OUTPUT;
  SELECT @Count AS PredictionCount;
  ```

---

## 💡 Use Cases in AI/ML

- **Pipeline Execution**: Call `CleanTrainingData` to preprocess `training_data`.
- **Model Scoring**: Execute `ScoreTestData` with `model_id` to generate `predictions`.
- **Logging Metrics**: Run `LogModelResults` to insert into `logs`.
- **Batch Processing**: Call `UpdateFeatureTable` for ETL pipelines.
- **Experiment Automation**: Invoke `TrackExperiment` to record `results`.

---

## 🔑 Key Features

- **Simple Invocation**: Executes complex logic with a single command.
- **Parameter Support**: Passes inputs or retrieves outputs dynamically.
- **Reusable**: Runs the same procedure across contexts.
- **Error Reporting**: Returns execution status or errors.

---

## ✅ Best Practices

- **Match Parameters**: Provide correct number and types of parameters.
- **Handle Outputs**: Capture `OUT` parameters where needed.
- **Test Calls**: Verify procedure behavior in a sandbox first.
- **Log Errors**: Use try-catch (where supported) to manage failures.

---

## ⚠️ Common Pitfalls

- **Parameter Errors**: Incorrect or missing parameters cause failures.
- **Syntax Variance**: `CALL` vs. `EXEC` differs by database.
- **Permission Issues**: Lack of execute privileges blocks calls.
- **Uncaptured Outputs**: Ignoring `OUT` parameters loses results.

---

## 📝 Additional Notes

- **Database Variations**:
  - **MySQL**: Uses `CALL procedure_name(params)`.
  - **PostgreSQL**: Uses `CALL` for procedures; `SELECT` for functions.
  - **SQL Server**: Supports `EXEC` or `EXECUTE`; `OUTPUT` for results.
  - **Oracle**: Uses `EXEC` or PL/SQL blocks (e.g., `BEGIN procedure_name; END;`).
- **Performance**: Calling is fast due to precompilation.
- **Security**: Requires `EXECUTE` permission on the procedure.