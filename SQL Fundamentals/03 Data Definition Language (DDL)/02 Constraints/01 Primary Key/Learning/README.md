# 🎉 Master Primary Key - Lock in Unique ML Records!

## 🌟 Welcome

The **Primary Key** ensures every row in a table is unique, perfect for identifying ML predictions or model metrics without duplicates. It’s your foundation for data integrity. This guide will walk you through learning `PRIMARY KEY` with ML-themed examples, powering up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Grasp the Role**: Understand how `PRIMARY KEY` enforces uniqueness and non-null values.
2. **Study the Syntax**: Learn to define it in `CREATE TABLE` or `ALTER TABLE`.
3. **Run Examples**: Try the commands below in a database like PostgreSQL or MySQL.
4. **Test Uniqueness**: Insert duplicate keys to see errors.
5. **Apply to ML**: Use primary keys to track unique ML records like predictions.

---

## 📜 Syntax

```sql
-- In CREATE TABLE
CREATE TABLE table_name (
    column_name datatype PRIMARY KEY,
    ...
);

-- In ALTER TABLE
ALTER TABLE table_name
ADD PRIMARY KEY (column_name);
```

- **Example 1: Predictions Table**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      prediction_date DATE,
      model_name VARCHAR(50)
  );
  ```
  *Sets `prediction_id` as the unique identifier for ML predictions.*

- **Example 2: Model Metrics Table**:
  ```sql
  CREATE TABLE model_metrics (
      metric_id INT PRIMARY KEY,
      model_id INT,
      accuracy FLOAT,
      log_date DATE
  );
  ```
  *Makes `metric_id` unique for ML performance records.*

- **Example 3: Add Primary Key**:
  ```sql
  CREATE TABLE feature_store (
      feature_id INT,
      value FLOAT
  );
  ALTER TABLE feature_store
  ADD PRIMARY KEY (feature_id);
  ```
  *Adds a primary key to an existing ML feature table.*

---

## 💡 Practice Tips

- **Tool Up**: Use [SQLFiddle](http://sqlfiddle.com) or a local DB to test primary keys.
- **ML Use Case**: Primary keys ensure unique ML records, like prediction IDs, for reliable data pipelines.
- **Try This**: Create `predictions`, insert two rows with the same `prediction_id`, and observe the error. Verify with `SELECT *`.
- **Debug**: Primary keys reject nulls and duplicates—test with `INSERT` to confirm enforcement.

---

## 🚀 Next Steps

- **Deepen Skills**: Explore `Foreign Key` for table relationships or `Unique` for other columns.
- **Portfolio Boost**: Add a `PRIMARY KEY` table to `irohanportfolio.netlify.app`, explaining its ML tracking role.
- **Challenge**: Create a table with a primary key for ML metrics in a portfolio dataset.

Lock in like a pro, and let’s make your SQL skills sparkle! 🌟