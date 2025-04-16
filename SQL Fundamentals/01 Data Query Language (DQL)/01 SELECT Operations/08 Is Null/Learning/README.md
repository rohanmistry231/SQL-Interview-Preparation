# 🎉 Master IS NULL - Handle Missing ML Data!

## 🌟 Welcome

The **IS NULL** operator finds rows with missing values, crucial for cleaning ML datasets before training. Whether it’s absent scores or undefined model names, `IS NULL` helps you spot gaps. This guide will show you how to learn `IS NULL` with ML examples, powering your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Know the Deal**: Understand `IS NULL` checks for missing data.
2. **Learn Syntax**: Study `IS NULL` and `IS NOT NULL`.
3. **Run Examples**: Try the queries below in a database like PostgreSQL.
4. **Test Scenarios**: Add nulls to data and query them.
5. **ML Angle**: Use `IS NULL` to clean datasets for ML pipelines.

---

## 📜 Syntax

```sql
SELECT column1, column2, ... FROM table_name WHERE column IS NULL;
-- OR
SELECT column1, column2, ... FROM table_name WHERE column IS NOT NULL;
```

- **Example 1: Missing Names**:
  ```sql
  SELECT prediction_id, model_id FROM predictions WHERE model_name IS NULL;
  ```
  *Finds rows with no `model_name`, like spotting incomplete ML metadata.*

- **Example 2: Non-Null Scores**:
  ```sql
  SELECT * FROM predictions WHERE score IS NOT NULL;
  ```
  *Grabs predictions with valid `score`s, great for ML model training.*

- **Example 3: Combined Check**:
  ```sql
  SELECT model_id, score FROM predictions 
  WHERE model_name IS NULL AND score IS NOT NULL;
  ```
  *Filters for missing names but valid scores, useful for ML data quality checks.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or MySQL.
- **ML Use Case**: `IS NULL` helps identify missing features or labels for ML preprocessing.
- **Try This**: Insert 5 rows with some `model_name` as `NULL`, then use `IS NULL`. Verify with `SELECT COUNT(*)`.
- **Watch Out**: Don’t use `= NULL`—it fails! Always use `IS NULL`.

---

## 🚀 Next Steps

- **Level Up**: Combine `IS NULL` with `WHERE` or `AND, OR, NOT` for advanced cleaning.
- **Portfolio Win**: Add an `IS NULL` query to `irohanportfolio.netlify.app`, showing ML data cleanup.
- **Challenge**: Find `NULL` `score`s for a portfolio ML quality report.

Clean data like a champ, and let’s rock your SQL game! 🌟