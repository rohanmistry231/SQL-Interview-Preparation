# ➕ Single Row Insert - Adding One Record at a Time

## 🌟 Overview

The **Single Row Insert** is an `INSERT` statement that adds **exactly one record** to a table by specifying explicit values for its columns. It’s the simplest form of data insertion, ideal for adding individual entries with precision. In AI/ML, single row inserts are used for tasks like logging specific events, adding test records, or initializing small datasets.

---

## 📜 Syntax

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

- **Basic Example**:
  ```sql
  INSERT INTO customers (customer_id, name, age)
  VALUES (1, 'Alice Smith', 25);
  ```
- **All Columns**:
  ```sql
  INSERT INTO products (product_id, name, price, stock)
  VALUES (101, 'Laptop', 999.99, 50);
  ```

---

## 💡 Use Cases in AI/ML

- **Test Data Creation**: Add a single record for testing (e.g., `INSERT INTO users (user_id, name) VALUES (999, 'Test User')`).
- **Event Logging**: Record a specific event (e.g., `INSERT INTO logs (log_id, event, timestamp) VALUES (1, 'Model Trained', '2024-04-15')`).
- **Metadata Updates**: Insert a model’s details (e.g., `INSERT INTO models (model_id, name, version) VALUES (1, 'Classifier', '1.0')`).
- **Manual Corrections**: Add a corrected record (e.g., `INSERT INTO orders (order_id, customer_id, amount) VALUES (1001, 5, 49.99)`).

---

## 🔑 Key Features

- **Explicit Values**: Requires values to match specified columns in order and type.
- **Optional Columns**: Omit non-required columns if they have defaults or allow NULL.
- **Single Execution**: Adds one row per statement, ensuring precision.
- **Constraint Awareness**: Respects primary keys, foreign keys, and other constraints.

---

## ✅ Best Practices

- **Specify Columns**: List columns explicitly to avoid errors if table structure changes.
- **Match Data Types**: Ensure values align with column types (e.g., strings in quotes, numbers unquoted).
- **Use Transactions**: Wrap inserts in `BEGIN`/`COMMIT` for safety in critical operations.
- **Validate Constraints**: Check for unique keys or foreign key requirements before inserting.

---

## ⚠️ Common Pitfalls

- **Missing Columns**: Omitting required columns without defaults causes errors.
- **Type Mismatch**: Providing incorrect data types (e.g., string for integer) fails the insert.
- **Constraint Violations**: Duplicate primary keys or invalid foreign keys halt execution.
- **Order Errors**: Misaligning values with columns leads to incorrect data or errors.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL/PostgreSQL/SQL Server: Syntax is identical for single row inserts.
  - PostgreSQL: Supports `RETURNING` to retrieve inserted values (e.g., `INSERT ... RETURNING id`).
- **Defaults**: Columns with `DEFAULT` values can be omitted if the default is desired.
- **Performance**: Single row inserts are slower for bulk data; use multiple row inserts for efficiency.