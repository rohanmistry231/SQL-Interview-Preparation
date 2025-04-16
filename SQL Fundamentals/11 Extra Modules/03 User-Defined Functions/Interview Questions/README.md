# 🎯 User-Defined Functions Interview Questions

## 🌟 Overview

**User-Defined Functions (UDFs)** are a hot topic in SQL interviews, testing your ability to encapsulate logic for ML tasks. From scalar functions for metrics to table-valued functions for datasets, UDFs are key in AI/ML for preprocessing and evaluation. These ML-themed questions will sharpen your skills for FAANG-style challenges—let’s dive in! 🚀

---

## 📚 Interview Questions

### Question 1: Scalar Function for RMSE
- **Difficulty**: Easy
- **Problem**: Write a scalar UDF to compute the Root Mean Squared Error (RMSE) between `score` and a predicted value in the `predictions` table (`prediction_id INT, model_id INT, score FLOAT`).
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- PostgreSQL
  CREATE FUNCTION compute_rmse(actual FLOAT, predicted FLOAT) RETURNS FLOAT AS $$
  BEGIN
      RETURN SQRT(ABS(actual - predicted));
  END;
  $$ LANGUAGE plpgsql;
  SELECT prediction_id, compute_rmse(score, 0.9) AS rmse
  FROM predictions;
  ```
  **Explanation**: The UDF calculates the square root of the absolute difference, simulating RMSE per row. For SQL Server:
  ```sql
  CREATE FUNCTION compute_rmse (@actual FLOAT, @predicted FLOAT)
  RETURNS FLOAT
  AS
  BEGIN
      RETURN SQRT(ABS(@actual - @predicted));
  END;
  ```
  Apply it with `SELECT dbo.compute_rmse(score, 0.9)`.
  </details>

### Question 2: Table-Valued Function for Features
- **Difficulty**: Medium
- **Problem**: Create a table-valued UDF to return all `feature` values for a given `user_id` from the `features` table (`feature_id INT, user_id INT, model_id INT, feature FLOAT`).
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- SQL Server
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
  **Explanation**: The UDF returns a table of `feature_id` and `feature` for the input `user_id`. For PostgreSQL:
  ```sql
  CREATE FUNCTION GetUserFeatures(user_id INT)
  RETURNS TABLE (feature_id INT, feature FLOAT) AS $$
  BEGIN
      RETURN QUERY
      SELECT f.feature_id, f.feature
      FROM features f
      WHERE f.user_id = GetUserFeatures.user_id;
  END;
  $$ LANGUAGE plpgsql;
  ```
  Use with `SELECT * FROM GetUserFeatures(12345)`.
  </details>

### Question 3: Normalize Feature Function
- **Difficulty**: Medium
- **Problem**: Write a scalar UDF to normalize a `feature` value from the `features` table to a 0-1 scale, given min and max values.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- PostgreSQL
  CREATE FUNCTION normalize_feature(value FLOAT, min_val FLOAT, max_val FLOAT) RETURNS FLOAT AS $$
  BEGIN
      IF max_val = min_val THEN
          RETURN 0;
      END IF;
      RETURN (value - min_val) / (max_val - min_val);
  END;
  $$ LANGUAGE plpgsql;
  SELECT feature_id, normalize_feature(feature, 0, 100) AS norm_feature
  FROM features;
  ```
  **Explanation**: The UDF applies min-max normalization, handling division-by-zero cases. For SQL Server:
  ```sql
  CREATE FUNCTION normalize_feature (@value FLOAT, @min_val FLOAT, @max_val FLOAT)
  RETURNS FLOAT
  AS
  BEGIN
      IF @max_val = @min_val
          RETURN 0;
      RETURN (@value - @min_val) / (@max_val - @min_val);
  END;
  ```
  Handles edge cases safely.
  </details>

---

## 💡 Tips for Acing UDF Interviews

- **Focus on Clarity**: Write simple, single-purpose UDFs to impress interviewers.
- **Handle Edge Cases**: Account for `NULL`, zeros, or invalid inputs in your logic.
- **Test Performance**: Compare UDFs vs. inline queries with `EXPLAIN` for optimization questions.
- **Know DB Syntax**: Be ready for `plpgsql` (PostgreSQL) vs. `T-SQL` (SQL Server) differences.

---

## 📝 Note

These questions are your springboard! Customize them (e.g., new metrics, complex outputs) and add to your portfolio to stand out. Got a killer UDF question? Share it to boost this repo! 🌟