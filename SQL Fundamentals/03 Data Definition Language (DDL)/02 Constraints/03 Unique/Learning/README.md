# 🎉 Master UNIQUE - Keep Your ML Data Distinct!

## 🌟 Welcome

The **Unique** constraint prevents duplicate values in a column, perfect for ensuring ML model names or feature IDs stay distinct. It’s your guard against redundant data. This guide will show you `UNIQUE` with ML examples, boosting your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Concept**: Understand how `UNIQUE` enforces distinct values.
2. **Learn Syntax**: Study defining it in `CREATE TABLE` or `ALTER TABLE`.
3. **Run Examples**: Try the commands below in a database like PostgreSQL.
4. **Test Duplicates**: Insert repeated values to trigger errors.
5. **ML Angle**: Use `UNIQUE` to maintain clean ML metadata.

---

## 📜 Syntax

```sql
-- In CREATE TABLE
CREATE TABLE table_name (
    column_name datatype UNIQUE,
    ...
);

-- In ALTER TABLE
ALTER TABLE table_name
ADD UNIQUE (column_name);
```

- **Example 1: Unique Model Names**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(50) UNIQUE
  );
  ```
  *Ensures no duplicate `model_name`s in ML models.*

- **Example 2: Unique Feature IDs**:
  ```sql
  CREATE TABLE feature_store (
      feature_id INT UNIQUE,
      value FLOAT
  );
  ```
  *Keeps `feature_id`s distinct for ML feature tracking.*

- **Example 3: Add Unique Constraint**:
  ```sql
  ALTER TABLE predictions
  ADD UNIQUE (model_name);
  ```
  *Applies `UNIQUE` to `model_name` in an existing ML table.*

---

## 💡 Practice Tips

- **Get Hands-On**: Use [SQLFiddle](http://sqlfiddle.com) or MySQL.
- **ML Use Case**: `UNIQUE` prevents duplicate ML metadata, like model or feature names, for clean datasets.
- **Try This**: Create `models`, insert two rows with the same `model_name`, and verify the error. Check with `SELECT *`.
- **Tip**: `UNIQUE` allows nulls (unlike `PRIMARY KEY`)—test with null inserts.

---

## 🚀 Next Steps

- **Go Deeper**: Explore `Primary Key` for stricter uniqueness or `Check` for value rules.
- **Portfolio Boost**: Add a `UNIQUE` table to `irohanportfolio.netlify.app`, explaining ML data cleanliness.
- **Challenge**: Create a table with a unique ML feature column for a portfolio dataset.

Stay distinct like a boss, and let’s make your SQL skills soar! 🌟