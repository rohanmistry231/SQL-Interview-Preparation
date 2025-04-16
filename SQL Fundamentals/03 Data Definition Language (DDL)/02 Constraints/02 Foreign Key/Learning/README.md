# 🎉 Master Foreign Key - Connect Your ML Data!

## 🌟 Welcome

The **Foreign Key** links tables, ensuring ML data like predictions reference valid models. It’s your key to relational integrity for AI pipelines. This guide will teach you `FOREIGN KEY` with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Links**: Learn how `FOREIGN KEY` enforces relationships.
2. **Study Syntax**: See how to define it in `CREATE TABLE` or `ALTER TABLE`.
3. **Run Examples**: Try the commands below in a database like MySQL.
4. **Test Constraints**: Insert invalid keys to see errors.
5. **ML Spin**: Use foreign keys to tie ML predictions to models.

---

## 📜 Syntax

```sql
-- In CREATE TABLE
CREATE TABLE table_name (
    column_name datatype,
    ...,
    FOREIGN KEY (column_name) REFERENCES parent_table(parent_column)
);

-- In ALTER TABLE
ALTER TABLE table_name
ADD FOREIGN KEY (column_name) REFERENCES parent_table(parent_column);
```

- **Example 1: Predictions to Models**:
  ```sql
  CREATE TABLE models (
      model_id INT PRIMARY KEY,
      model_name VARCHAR(50)
  );
  CREATE TABLE predictions (
      prediction_id INT PRIMARY KEY,
      model_id INT,
      score FLOAT,
      FOREIGN KEY (model_id) REFERENCES models(model_id)
  );
  ```
  *Links `predictions` to `models`, ensuring valid ML model references.*

- **Example 2: Metrics to Models**:
  ```sql
  CREATE TABLE model_metrics (
      metric_id INT PRIMARY KEY,
      model_id INT,
      accuracy FLOAT,
      FOREIGN KEY (model_id) REFERENCES models(model_id)
  );
  ```
  *Connects `model_metrics` to `models` for ML performance tracking.*

- **Example 3: Add Foreign Key**:
  ```sql
  ALTER TABLE predictions
  ADD FOREIGN KEY (model_id) REFERENCES models(model_id);
  ```
  *Adds a foreign key to an existing ML predictions table.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: Foreign keys ensure ML data (e.g., predictions) aligns with valid entities like models.
- **Try This**: Create `models` and `predictions`, insert a `prediction` with an invalid `model_id`, and check the error.
- **Note**: Parent table must exist with a primary key—test inserts to confirm enforcement.

---

## 🚀 Next Steps

- **Level Up**: Try `Primary Key` for unique IDs or `Not Null` for mandatory fields.
- **Portfolio Win**: Add a `FOREIGN KEY` schema to `irohanportfolio.netlify.app`, showing ML relationships.
- **Challenge**: Link a metrics table to models in a portfolio ML dataset.

Connect like a champ, and let’s rock your SQL journey! 🌟