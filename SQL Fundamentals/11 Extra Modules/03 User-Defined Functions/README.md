# 🧩 User-Defined Functions - Custom Logic for ML Data

## 🌟 Overview

**User-Defined Functions (UDFs)** let you create custom SQL logic to process data, like reusable formulas or table generators. From scalar functions (e.g., compute metrics) to table-valued functions (e.g., return datasets), UDFs streamline complex ML tasks. In AI/ML, UDFs are vital for preprocessing features, calculating model metrics, or encapsulating business logic.

---

## 📜 Syntax

```sql
-- Scalar Function
CREATE FUNCTION function_name(param1 type) RETURNS type AS $$
BEGIN
    RETURN expression;
END;
$$ LANGUAGE plpgsql;
```

- **Scalar Function** (PostgreSQL):
  ```sql
  CREATE FUNCTION compute_rmse(actual FLOAT, predicted FLOAT) RETURNS FLOAT AS $$
  BEGIN
      RETURN SQRT(ABS(actual - predicted));
  END;
  $$ LANGUAGE plpgsql;
  SELECT compute_rmse(score, 0.9) FROM predictions;
  ```
- **Table-Valued Function** (SQL Server):
  ```sql
  CREATE FUNCTION GetUserFeatures (@user_id INT)
  RETURNS TABLE
  AS
  RETURN (
      SELECT feature_id, feature
      FROM features
      WHERE user_id = @user_id
  );
  SELECT * FROM GetUserFeatures(12345);
  ```
- **Aggregate Function** (PostgreSQL):
  ```sql
  CREATE AGGREGATE custom_avg(FLOAT) (
      SFUNC = float8_accum,
      STYPE = FLOAT[],
      FINALFUNC = float8_avg
  );
  ```

---

## 💡 Use Cases in AI/ML

- **Metric Calculation**: Compute RMSE or MAE for model evaluation (e.g., `SELECT compute_rmse(actual, predicted)`).
- **Feature Engineering**: Generate derived features (e.g., `CREATE FUNCTION normalize_feature(value FLOAT)`).
- **Data Filtering**: Return ML-ready datasets (e.g., `SELECT * FROM GetUserFeatures(12345)`).
- **Pipeline Reusability**: Encapsulate preprocessing logic for consistent ML workflows.

---

## 🔑 Key Features

- **Scalar UDFs**: Return single values (e.g., calculations).
- **Table-Valued UDFs**: Return result sets for complex queries.
- **Aggregate UDFs**: Create custom aggregations (e.g., weighted averages).
- **Cross-DB Support**: Available in PostgreSQL (`plpgsql`), SQL Server (`T-SQL`), MySQL (`DELIMITER`).

---

## ✅ Best Practices

- **Keep It Focused**: Design UDFs for specific tasks (e.g., one metric per function).
- **Optimize Logic**: Avoid heavy computations inside UDFs—offload to stored procedures if needed.
- **Use Descriptive Names**: Name functions clearly (e.g., `compute_rmse` vs. `func1`).
- **Test Edge Cases**: Verify UDFs handle nulls, zeros, and large inputs correctly.

---

## ⚠️ Common Pitfalls

- **Performance Drag**: UDFs can slow queries if overused—avoid in high-frequency joins.
- **Null Handling**: Failing to account for `NULL` inputs causes errors (e.g., `IFNULL(param, 0)`).
- **Complexity Creep**: Overcomplicating UDFs reduces maintainability—keep logic simple.
- **DB Limitations**: MySQL UDFs lack advanced features (e.g., no `RETURNS TABLE`)—check compatibility.

---

## 📝 Additional Notes

- **Database Variations**: PostgreSQL uses `plpgsql` for flexibility, SQL Server uses `T-SQL`, MySQL is limited to simple UDFs.
- **Performance**: Scalar UDFs may be slower than inline expressions—use `DETERMINISTIC` in MySQL for caching.
- **Security**: Restrict UDF execution permissions to prevent misuse.
- **Debugging**: Log UDF outputs with `RAISE NOTICE` (PostgreSQL) or `PRINT` (SQL Server) for testing.