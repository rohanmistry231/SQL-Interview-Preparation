# ⚙️ Default - Setting Fallback Values

## 🌟 Overview

The **Default** constraint in SQL specifies a **default value** for a column when no value is provided during an insert. It simplifies data entry and ensures consistency for optional fields. In AI/ML, `Default` constraints are useful for initializing datasets with standard values, reducing NULLs, and streamlining data preparation for models.

---

## 📜 Syntax

```sql
CREATE TABLE table_name (
    column_name datatype DEFAULT default_value,
    ...
);
```

- **Basic Example**:
  ```sql
  CREATE TABLE users (
      user_id INT PRIMARY KEY,
      status VARCHAR(20) DEFAULT 'active'
  );
  ```
- **With Other Constraints**:
  ```sql
  CREATE TABLE orders (
      order_id INT PRIMARY KEY,
      order_date DATE DEFAULT CURRENT_DATE,
      amount DECIMAL(10,2) DEFAULT 0.00
  );
  ```

---

## 💡 Use Cases in AI/ML

- **Data Initialization**: Set defaults for features (e.g., `DEFAULT 0` for `score` in a `results` table).
- **Consistency**: Ensure standard values (e.g., `DEFAULT 'pending'` for `status` in an `orders` table).
- **Missing Data Handling**: Reduce NULLs (e.g., `DEFAULT 'unknown'` for `region` in a `users` table).
- **Automation**: Use dynamic defaults (e.g., `DEFAULT CURRENT_TIMESTAMP` for `created_at` in a `logs` table).

---

## 🔑 Key Features

- **Automatic Values**: Supplies `default_value` when no value is specified in `INSERT`.
- **Column-Level**: Applies to individual columns, not table-wide.
- **Expression Support**: Allows constants, functions (e.g., `CURRENT_DATE`), or expressions in some databases.
- **Optional Use**: Ignored if a value is explicitly provided.

---

## ✅ Best Practices

- **Choose Logical Defaults**: Use values that make sense (e.g., `0` for numbers, `'active'` for status).
- **Pair with NOT NULL**: Combine with `NOT NULL` for required fields to avoid NULLs.
- **Keep Simple**: Avoid complex expressions to maintain clarity.
- **Document Defaults**: Comment why defaults are chosen for team understanding.

---

## ⚠️ Common Pitfalls

- **Unexpected Values**: Defaults may insert unwanted data if overlooked (e.g., `DEFAULT 0` skews averages).
- **Overuse**: Applying defaults to all columns reduces flexibility for valid NULLs.
- **Database Differences**: Expression support varies (e.g., MySQL limits dynamic defaults).
- **Migration Issues**: Changing defaults on existing tables may not affect old rows.

---

## 📝 Additional Notes

- **Database Variations**:
  - MySQL: Supports constants and some functions (e.g., `CURRENT_TIMESTAMP`).
  - PostgreSQL: Allows expressions and sequences (e.g., `nextval()`).
  - SQL Server: Supports constants and limited functions.
- **Performance**: Minimal impact, as defaults are applied during inserts.
- **Alternatives**: Use application logic for complex default values if needed.