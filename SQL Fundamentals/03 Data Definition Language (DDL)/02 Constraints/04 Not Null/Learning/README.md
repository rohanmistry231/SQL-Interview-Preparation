# 🎉 Master NOT NULL - Ensure Your ML Data Stays Complete!

## 🌟 Welcome

The **Not Null** constraint forces a column to have a value, ideal for mandatory ML fields like prediction scores or metric IDs. It’s your shield against missing data. This guide will teach you `NOT NULL` with ML examples, supercharging your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand the Rule**: Learn how `NOT NULL` bans null values.
2. **Study Syntax**: See how to apply it in `CREATE TABLE` or `ALTER TABLE`.
3. **Run Examples**: Try the commands below in a database like MySQL.
4. **Test Nulls**: Try inserting nulls to see errors.
5. **ML Spin**: Use `NOT NULL` to enforce complete ML datasets.

---

## 📜 Syntax

```sql
-- In CREATE TABLE
CREATE TABLE table_name (
    column_name datatype NOT NULL,
    ...
);

-- In ALTER TABLE
ALTER TABLE table_name
MODIFY COLUMN column_name datatype NOT NULL;
```

- **Example 1: Mandatory Prediction ID**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT NOT NULL,
      model_id INT,
      score FLOAT
  );
  ```
  *Ensures `prediction_id` is always set for ML predictions.*

- **Example 2: Required Accuracy**:
  ```sql
  CREATE TABLE model_metrics (
      metric_id INT,
      model_id INT,
      accuracy FLOAT NOT NULL
  );
  ```
  *Forces `accuracy` values for ML metrics.*

- **Example 3: Add Not Null**:
  ```sql
  ALTER TABLE predictions
  MODIFY COLUMN score FLOAT NOT NULL;
  ```
  *Makes `score` mandatory in an existing ML table.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: `NOT NULL` ensures critical ML fields, like scores, are always populated for modeling.
- **Try This**: Create `predictions`, try inserting a row with null `score`, and check the error. Verify with `DESCRIBE predictions`.
- **Note**: Existing nulls block `NOT NULL` additions—clean data with `UPDATE` first.

---

## 🚀 Next Steps

- **Level Up**: Pair `NOT NULL` with `Default` for fallback values or `Primary Key` for IDs.
- **Portfolio Win**: Add a `NOT NULL` table to `irohanportfolio.netlify.app`, showing ML data completeness.
- **Challenge**: Create a table with a non-null ML score column for a portfolio dataset.

Stay complete like a pro, and let’s rock your SQL game! 🌟