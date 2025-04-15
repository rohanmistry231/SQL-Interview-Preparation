# 🔑 Primary Key - Uniquely Identifying Rows

## 🌟 Overview

The **Primary Key** constraint in SQL is a rule that **uniquely identifies each row** in a table, ensuring no duplicate or NULL values are allowed in the designated column(s). It’s the cornerstone of relational database design, providing a reliable way to reference records. In AI/ML, primary keys are essential for organizing datasets, linking tables, and ensuring data integrity in training data and model outputs.

---

## 📜 Syntax

```sql
CREATE TABLE table_name (
    column_name datatype PRIMARY KEY,
    ...
);
-- OR for multiple columns
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...,
    CONSTRAINT pk_name PRIMARY KEY (column1, column2)
);
```

- **Single Column Example**:
  ```sql
  CREATE TABLE customers (
      customer_id INT PRIMARY KEY,
      name VARCHAR(100)
  );
  ```
- **Composite Key Example**:
  ```sql
  CREATE TABLE order_details (
      order_id INT,
      product_id INT,
      quantity INT,
      CONSTRAINT pk_order_details PRIMARY KEY (order_id, product_id)
  );
  ```

---

## 💡 Use Cases in AI/ML

- **Dataset Identification**: Assign unique IDs to records (e.g., `prediction_id` in a `predictions` table).
- **Data Linking**: Enable joins with other tables (e.g., `user_id` in `users` links to `orders`).
- **Deduplication**: Prevent duplicate entries in training data (e.g., `model_id` in a `models` table).
- **Indexing**: Optimize queries by automatically indexing primary key columns for ML pipelines.

---

## 🔑 Key Features

- **Uniqueness**: Ensures no two rows have the same value(s) in the primary key column(s).
- **Non-NULL**: Prohibits NULL values in the key column(s).
- **Single per Table**: Only one primary key (single or composite) is allowed per table.
- **Automatic Indexing**: Most databases create an index on the primary key for performance.

---

## ✅ Best Practices

- **Use Simple Keys**: Prefer single-column keys (e.g., `id INT`) for simplicity and performance.
- **Choose Stable Values**: Select columns unlikely to change (e.g., IDs over names).
- **Auto-Increment**: Use auto-incrementing integers (e.g., `SERIAL` in PostgreSQL) for ease.
- **Name Constraints**: Use explicit names (e.g., `CONSTRAINT pk_customers`) for clarity.

---

## ⚠️ Common Pitfalls

- **Duplicate Values**: Attempting to insert duplicates causes errors (e.g., `INSERT ... VALUES (1, ...)` twice).
- **NULL Values**: Trying to insert NULL into a primary key column fails.
- **Complex Keys**: Overusing composite keys can complicate queries and joins.
- **Modification Issues**: Changing primary key values is tricky due to dependencies.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL: Requires `NOT NULL` implicitly; supports `AUTO_INCREMENT`.
  - PostgreSQL: Uses `SERIAL` for auto-incrementing keys; supports `IF NOT EXISTS`.
  - SQL Server: Uses `IDENTITY(1,1)` for auto-increment.
- **Performance**: Primary keys improve query speed but add overhead to inserts.
- **Dependencies**: Cannot drop a primary key if referenced by foreign keys without `CASCADE`.