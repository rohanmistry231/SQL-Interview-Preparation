# 🛠️ Parameters - Adding Flexibility to Procedures

## 🌟 Overview

**Parameters** in stored procedures allow **dynamic input and output**, making procedures versatile by accepting values at runtime or returning results. Parameters can be input (IN), output (OUT), or both (INOUT), enabling customized logic without hardcoding.

In AI/ML, parameters are vital for **dynamic data tasks**, like filtering datasets by date or returning model metrics. For freshers, it’s a **frequent interview topic**, tested in questions about reusable logic and parameterization in production systems.

---

## 📜 Syntax

```sql
-- Generic SQL (varies by database)
CREATE PROCEDURE procedure_name (IN param1 datatype, OUT param2 datatype)
AS
BEGIN
    -- Use parameters in logic
END;
```

- **Basic Example** (SQL Server syntax):
  ```sql
  CREATE PROCEDURE GetPredictionCount
      @ModelID INT,
      @Count OUT INT
  AS
  BEGIN
      SELECT @Count = COUNT(*)
      FROM predictions
      WHERE model_id = @ModelID;
  END;
  ```
- **With Input Parameter** (MySQL-style):
  ```sql
  DELIMITER //
  CREATE PROCEDURE FilterTrainingData (IN min_feature FLOAT)
  BEGIN
      DELETE FROM training_data WHERE feature1 < min_feature;
  END //
  DELIMITER ;
  ```

---

## 💡 Use Cases in AI/ML

- **Dynamic Filtering**: Pass `min_accuracy` to select `models` above a threshold.
- **Model Evaluation**: Use `model_id` to compute `predictions` stats, returning counts.
- **ETL Customization**: Input `batch_date` to process `staging_table` for pipelines.
- **Feature Scaling**: Pass `scale_factor` to normalize `training_data`.
- **Experiment Analysis**: Return `avg_score` for a given `experiment_id`.

---

## 🔑 Key Features

- **Input Parameters**: Pass values to customize logic (e.g., `IN model_id INT`).
- **Output Parameters**: Retrieve results (e.g., `OUT count INT`).
- **INOUT Support**: Combine input and output (limited support in some databases).
- **Type Safety**: Parameters require specific data types for reliability.

---

## ✅ Best Practices

- **Define Types Clearly**: Match parameter types to column types (e.g., `INT` for `model_id`).
- **Use Descriptive Names**: Name parameters like `min_accuracy` for clarity.
- **Limit Parameters**: Avoid excessive parameters to keep procedures manageable.
- **Validate Inputs**: Check parameter values to prevent errors.

---

## ⚠️ Common Pitfalls

- **Type Mismatches**: Wrong data types cause runtime errors.
- **Missing Parameters**: Omitting required inputs breaks execution.
- **Overuse of OUT**: Too many output parameters complicates logic.
- **Database Quirks**: Syntax varies (e.g., MySQL’s `IN`, SQL Server’s `@param`).

---

## 📝 Additional Notes

- **Database Variations**:
  - **MySQL**: Uses `IN`, `OUT`, `INOUT` with `DELIMITER`.
  - **PostgreSQL**: Prefers functions for `OUT` parameters; procedures less common.
  - **SQL Server**: Uses `@param` notation; supports `OUTPUT`.
  - **Oracle**: PL/SQL uses `IN`, `OUT`, `IN OUT` with flexible syntax.
- **Default Values**: Supported in some databases (e.g., MySQL) for `IN` parameters.
- **Performance**: Parameters don’t impact precompilation benefits.