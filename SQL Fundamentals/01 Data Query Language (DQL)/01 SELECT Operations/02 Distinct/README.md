# 🎯 DISTINCT - Eliminating Duplicates in Query Results

## 🌟 Overview

The **DISTINCT** keyword in SQL removes duplicate rows from the result set of a `SELECT` query, ensuring each row is unique based on the selected columns. It’s essential for summarizing data, identifying unique values, and cleaning datasets in AI/ML workflows.

---

## 📜 Syntax

```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

- **Single Column**:
  ```sql
  SELECT DISTINCT department
  FROM employees;
  ```
- **Multiple Columns**:
  ```sql
  SELECT DISTINCT city, state
  FROM customers;
  ```

---

## 💡 Use Cases in AI/ML

- **Data Cleaning**: Identify unique categories for feature encoding (e.g., `SELECT DISTINCT product_category FROM products`).
- **Exploratory Analysis**: List unique user behaviors (e.g., `SELECT DISTINCT user_id FROM logins`).
- **Deduplication**: Ensure no duplicate records in training data (e.g., `SELECT DISTINCT customer_id, purchase_date FROM orders`).
- **Metadata Extraction**: Retrieve unique values for model metadata (e.g., `SELECT DISTINCT region FROM sales`).

---

## 🔑 Key Features

- **Row-Level Uniqueness**: DISTINCT applies to the entire selected row, not individual columns.
- **Multi-Column Support**: Uniqueness is based on the combination of all specified columns.
- **NULL Handling**: NULL values are considered equal, so only one NULL appears in the result.

---

## ✅ Best Practices

- **Use Sparingly**: DISTINCT can be resource-intensive on large datasets; consider alternatives like `GROUP BY` if possible.
- **Select Specific Columns**: Only include columns necessary for uniqueness to minimize processing.
- **Combine with ORDER BY**: Sort results for clarity (e.g., `SELECT DISTINCT department FROM employees ORDER BY department`).
- **Test Performance**: Run `EXPLAIN` to check query cost, especially for large tables.

---

## ⚠️ Common Pitfalls

- **Performance Overhead**: DISTINCT on large datasets or multiple columns can slow queries due to sorting or hashing.
- **Unexpected Results**: When using multiple columns, uniqueness is based on the combination, not individual columns.
- **NULL Confusion**: Be aware that NULLs are treated as identical, which may affect results.

---

## 📝 Additional Notes

- **Database Variations**: Most databases (MySQL, PostgreSQL, SQL Server) support DISTINCT identically, but performance varies.
- **DISTINCT ON**: PostgreSQL offers `DISTINCT ON` for selecting the first row of each group (not standard SQL).
- **Alternatives**: For better performance, consider `GROUP BY` or indexing unique columns.