# 📚 Multiple Column Update - Revamp Multiple Fields at Once

## 🌟 Overview

The **Multiple Column Update** is an `UPDATE` statement that modifies **multiple columns** for selected rows in a single statement by setting new values. It’s an efficient way to adjust several attributes simultaneously, like updating both scores and dates in ML predictions. In AI/ML, multiple column updates are ideal for aligning datasets, correcting metadata, or applying batch fixes.

---

## 📜 Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
[WHERE condition];
```

- **Basic Example**:
  ```sql
  UPDATE predictions
  SET score = 0.88, prediction_date = '2025-04-15'
  WHERE prediction_id = 2;
  ```
- **With Transformation**:
  ```sql
  UPDATE predictions
  SET score = score * 100, model_name = UPPER(model_name)
  WHERE score < 1;
  ```
- **Multiple Attributes**:
  ```sql
  UPDATE predictions
  SET model_id = 102, model_name = 'XGBoost_v1'
  WHERE model_name = 'Old_Model';
  ```

---

## 💡 Use Cases in AI/ML

- **Dataset Alignment**: Update scores and dates (e.g., `UPDATE predictions SET score = 0.9, prediction_date = '2025-04-16' WHERE prediction_id = 3`).
- **Metadata Correction**: Revise model IDs and names (e.g., `UPDATE predictions SET model_id = 103, model_name = 'CNN' WHERE model_id = 100`).
- **Data Standardization**: Adjust multiple fields (e.g., `UPDATE predictions SET score = score / 100, model_name = 'Default' WHERE score > 100`).
- **Batch Updates**: Fix multiple attributes (e.g., `UPDATE predictions SET score = 0.5, prediction_date = NULL WHERE model_id = 104`).

---

## 🔑 Key Features

- **Multi-Column Efficiency**: Updates several columns in one statement, reducing queries.
- **Flexible Values**: Supports literals, expressions, or NULLs for each column.
- **Conditional Targeting**: Uses `WHERE` to select rows, or updates all if omitted.
- **Constraint Enforcement**: Ensures all updates comply with table rules.

---

## ✅ Best Practices

- **Explicit Conditions**: Use `WHERE` to avoid updating unintended rows.
- **Verify Compatibility**: Match values to column types and constraints.
- **Preview Changes**: Run `SELECT` with the `WHERE` clause to check rows first.
- **Use Transactions**: Enclose updates in `BEGIN`/`COMMIT` for consistency.

---

## ⚠️ Common Pitfalls

- **No WHERE Clause**: Updates all rows if `WHERE` is missing, risking data loss.
- **Column Mismatch**: Incorrect value types or constraints cause errors.
- **Overlapping Updates**: Conflicting `SET` clauses (e.g., redundant updates) may confuse logic.
- **Performance Issues**: Large updates without indexes slow down execution.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL/PostgreSQL/SQL Server: Support multiple column updates identically.
  - PostgreSQL: `RETURNING` retrieves updated rows’ data.
- **Optimization**: Index `WHERE` columns for faster updates.
- **Error Handling**: Use `ON CONFLICT` (PostgreSQL) or `IGNORE` (MySQL) for edge cases.