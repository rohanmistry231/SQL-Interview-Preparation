# 🎉 Master DEFAULT - Set Smart ML Data Fallbacks!

## 🌟 Welcome

The **Default** constraint assigns a fallback value when no data is provided, ideal for setting standard ML scores or dates. It’s your trick for consistent datasets. This guide will teach you `DEFAULT` with ML examples, supercharging your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Fallbacks**: Learn how `DEFAULT` fills missing values.
2. **Study Syntax**: See how to set it in `CREATE TABLE` or `ALTER TABLE`.
3. **Run Examples**: Try the commands below in a database like MySQL.
4. **Test Defaults**: Insert rows without values to see defaults applied.
5. **ML Spin**: Use `DEFAULT` to streamline ML data entry.

---

## 📜 Syntax

```sql
-- In CREATE TABLE
CREATE TABLE table_name (
    column_name datatype DEFAULT value,
    ...
);

-- In ALTER TABLE
ALTER TABLE table_name
ALTER COLUMN column_name SET DEFAULT value;
```

- **Example 1: Default Score**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT,
      score FLOAT DEFAULT 0.5
  );
  ```
  *Sets `score` to 0.5 if unspecified, like a baseline for ML predictions.*

- **Example 2: Default Date**:
  ```sql
  CREATE TABLE model_metrics (
      metric_id INT,
      log_date DATE DEFAULT '2025-01-01'
  );
  ```
  *Uses a default `log_date` for ML metrics.*

- **Example 3: Add Default**:
  ```sql
  ALTER TABLE predictions
  ALTER COLUMN model_name SET DEFAULT 'Unknown';
  ```
  *Adds a default `model_name` to an ML table.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: `DEFAULT` simplifies ML data prep by auto-filling fields like scores or labels.
- **Try This**: Create `predictions`, insert a row without `score`, and check the default with `SELECT *`.
- **Note**: Defaults don’t apply to explicit nulls—test with `INSERT` variations.

---

## 🚀 Next Steps

- **Level Up**: Pair `DEFAULT` with `Not Null` for mandatory defaults or `Check` for value rules.
- **Portfolio Win**: Add a `DEFAULT` table to `irohanportfolio.netlify.app`, showing ML data consistency.
- **Challenge**: Create a table with a default ML score for a portfolio dataset.

Fallback like a pro, and let’s rock your SQL game! 🌟