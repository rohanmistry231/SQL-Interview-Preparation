# ⚖️ Case Statements - Dynamic If-Then-Else Logic

## 🌟 Overview

The **CASE Statement** in SQL provides **if-then-else** logic within a query, allowing you to transform, categorize, or compute values based on conditions. It’s like a decision tree embedded in your SQL, enabling dynamic data manipulation without external processing. In AI/ML, `CASE` statements are vital for feature engineering, data categorization, and creating derived columns for modeling.

---

## 📜 Syntax

```sql
SELECT 
    column1,
    CASE 
        WHEN condition1 THEN result1
        WHEN condition2 THEN result2
        ...
        [ELSE result_else]
    END AS alias
FROM table_name;
```

- **Simple CASE Example**:
  ```sql
  SELECT 
      first_name,
      CASE 
          WHEN salary > 100000 THEN 'High'
          WHEN salary > 50000 THEN 'Medium'
          ELSE 'Low'
      END AS salary_level
  FROM employees;
  ```
- **Searched CASE Example**:
  ```sql
  SELECT 
      product_name,
      CASE department
          WHEN 'Electronics' THEN 'Tech'
          WHEN 'Clothing' THEN 'Fashion'
          ELSE 'Other'
      END AS category
  FROM products;
  ```

---

## 💡 Use Cases in AI/ML

- **Feature Engineering**: Categorize data for models (e.g., `CASE WHEN age < 30 THEN 'Young' ELSE 'Adult' END AS age_group`).
- **Data Labeling**: Assign labels for classification tasks (e.g., `CASE WHEN score > 0.8 THEN 'Positive' ELSE 'Negative' END AS sentiment`).
- **Dynamic Metrics**: Compute conditional values (e.g., `CASE WHEN stock = 0 THEN 'Out of Stock' ELSE 'Available' END AS status`).
- **Report Formatting**: Transform data for visualization (e.g., `CASE WHEN revenue > 1000 THEN 'High' ELSE 'Low' END AS revenue_tier`).

---

## 🔑 Key Features

- **Two Forms**: 
  - **Simple CASE**: Compares a single expression to multiple values.
  - **Searched CASE**: Evaluates multiple boolean conditions.
- **Flexible Placement**: Used in `SELECT`, `WHERE`, `ORDER BY`, or `GROUP BY` clauses.
- **ELSE Clause**: Optional; defaults to NULL if omitted.
- **Nested CASE**: Can embed CASE within CASE for complex logic.

---

## ✅ Best Practices

- **Keep It Simple**: Limit conditions to 3-5 for readability; use subqueries or CTEs for complex logic.
- **Use Descriptive Aliases**: Name the output column clearly (e.g., `AS age_group`).
- **Order Conditions Logically**: Place most likely or restrictive conditions first for efficiency.
- **Include ELSE**: Explicitly define an `ELSE` to handle unexpected cases and avoid NULLs.

---

## ⚠️ Common Pitfalls

- **Missing ELSE**: Omitting `ELSE` returns NULL for unmatched rows, which may skew results.
- **Overcomplication**: Too many conditions reduce readability; consider alternative approaches like lookup tables.
- **Performance**: Complex CASE statements in large datasets can slow queries; optimize surrounding clauses.
- **Type Mismatch**: Ensure all `THEN` results have compatible data types to avoid errors.

---

## 📝 Additional Notes

- **Database Variations**: CASE is standard across MySQL, PostgreSQL, and SQL Server.
- **Performance Tip**: Avoid CASE in `WHERE` clauses when possible; use `AND`/`OR` for better index usage.
- **Nested Limits**: Deeply nested CASE statements can be hard to debug; refactor using CTEs if needed.