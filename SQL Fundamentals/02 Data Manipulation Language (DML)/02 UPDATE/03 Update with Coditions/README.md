# 🔄 Update with Conditions - Fine-Tune Data Selectively

## 🌟 Overview

The **Update with Conditions** is an `UPDATE` statement that modifies rows based on specific **conditions** defined in a `WHERE` clause, allowing targeted changes like adjusting ML predictions by score or date. It’s a powerful technique for selective data refinement. In AI/ML, conditional updates are crucial for correcting subsets of data, maintaining quality, or applying rules to specific records.

---

## 📜 Syntax

```sql
UPDATE table_name
SET column_name = value, ...
WHERE condition;
```

- **Basic Example**:
  ```sql
  UPDATE predictions
  SET score = 0.9
  WHERE model_id = 101 AND score < 0.8;
  ```
- **Multi-Column**:
  ```sql
  UPDATE predictions
  SET score = 0.85, model_name = 'Updated_Model'
  WHERE prediction_date < '2025-04-01';
  ```
- **Complex Condition**:
  ```sql
  UPDATE predictions
  SET score = score + 0.1
  WHERE model_name LIKE 'BERT%' AND score IS NOT NULL;
  ```

---

## 💡 Use Cases in AI/ML

- **Selective Correction**: Adjust scores for specific models (e.g., `UPDATE predictions SET score = 0.95 WHERE model_id = 102`).
- **Data Filtering**: Update old records (e.g., `UPDATE predictions SET model_name = 'Archive' WHERE prediction_date < '2025-01-01'`).
- **Conditional Standardization**: Normalize data (e.g., `UPDATE predictions SET score = 1 WHERE score > 1 AND model_id = 103`).
- **Model Updates**: Revise metadata for certain conditions (e.g., `UPDATE predictions SET model_name = 'CNN_v2' WHERE score > 0.9`).

---

## 🔑 Key Features

- **Precision Targeting**: `WHERE` clause filters rows, ensuring only intended records change.
- **Flexible Conditions**: Supports comparisons, logical operators, and patterns (e.g., `LIKE`).
- **Single or Multi-Column**: Can update one or more columns based on conditions.
- **Constraint Compliance**: Validates updates against table rules.

---

## ✅ Best Practices

- **Test Conditions**: Run `SELECT COUNT(*) WHERE ...` to estimate affected rows.
- **Use Indexes**: Ensure `WHERE` columns are indexed for speed.
- **Be Specific**: Craft precise conditions to avoid unintended updates.
- **Backup Data**: Use transactions (`BEGIN`/`COMMIT`) to allow rollbacks.

---

## ⚠️ Common Pitfalls

- **Vague Conditions**: Broad `WHERE` clauses update too many rows.
- **Logic Errors**: Incorrect operators (e.g., `AND` vs. `OR`) affect wrong rows.
- **Constraint Issues**: Updates violating keys or types fail.
- **Missing Rows**: Overly strict conditions may update nothing, missing targets.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL/PostgreSQL/SQL Server: Conditional updates follow the same syntax.
  - PostgreSQL: Supports `RETURNING` for updated data inspection.
- **Performance Tip**: Avoid complex conditions on unindexed columns.
- **Safety**: Use `LIMIT` (MySQL) or test in a sandbox to prevent errors.