# 🎯 Unique - Ensuring Distinct Values

## 🌟 Overview

The **Unique** constraint in SQL ensures that **all values in a column (or combination of columns)** are distinct, preventing duplicate entries while allowing NULLs (unlike primary keys). It’s ideal for columns that must remain unique but aren’t necessarily primary identifiers. In AI/ML, unique constraints maintain data quality by preventing redundant records, such as duplicate emails or IDs, in datasets.

---

## 📜 Syntax

```sql
CREATE TABLE table_name (
    column_name datatype UNIQUE,
    ...
);
-- OR for multiple columns
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...,
    CONSTRAINT unique_name UNIQUE (column1, column2)
);
```

- **Single Column Example**:
  ```sql
  CREATE TABLE users (
      user_id INT PRIMARY KEY,
      email VARCHAR(255) UNIQUE
  );
  ```
- **Composite Unique Example**:
  ```sql
  CREATE TABLE registrations (
      event_id INT,
      user_id INT,
      CONSTRAINT unique_registration UNIQUE (event_id, user_id)
  );
  ```

---

## 💡 Use Cases in AI/ML

- **Identifier Uniqueness**: Prevent duplicate entries (e.g., `email` in a `users` table).
- **Data Cleaning**: Ensure unique feature values (e.g., `experiment_id` in an `experiments` table).
- **Reference Keys**: Support foreign keys referencing unique columns (e.g., `code` in a `products` table).
- **Deduplication**: Avoid redundant records in training data (e.g., `session_id` in a `logins` table).

---

## 🔑 Key Features

- **Distinct Values**: No two rows can have the same non-NULL value(s) in the unique column(s).
- **NULL Handling**: Allows multiple NULLs (unlike primary keys, which prohibit NULLs).
- **Multiple per Table**: A table can have several unique constraints.
- **Indexing**: Automatically creates an index for performance.

---

## ✅ Best Practices

- **Choose Wisely**: Apply to columns needing uniqueness (e.g., `email`, not `name`).
- **Allow NULLs Thoughtfully**: Use when NULLs are valid (e.g., optional unique fields).
- **Name Constraints**: Use descriptive names (e.g., `unique_email`) for clarity.
- **Combine with Indexes**: Leverage the automatic index for query optimization.

---

## ⚠️ Common Pitfalls

- **Duplicate Attempts**: Inserting duplicates causes errors (e.g., same `email` twice).
- **NULL Confusion**: Expecting unique constraints to restrict NULLs (they don’t).
- **Overuse**: Adding too many unique constraints slows inserts and updates.
- **Conflict with Primary Key**: Redundant unique constraints on primary key columns waste resources.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL: Treats multiple NULLs as distinct; supports `ON DUPLICATE KEY`.
  - PostgreSQL: Allows `NULLS NOT DISTINCT` for unique constraints (newer versions).
  - SQL Server: Permits one NULL per unique column by default.
- **Performance**: Unique constraints add overhead but improve query speed via indexes.
- **Alternatives**: Use primary keys for non-NULL unique identifiers.