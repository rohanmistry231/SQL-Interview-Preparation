# 🎉 Master COALESCE - Clean Your ML Data with Ease!

## 🌟 Welcome

**COALESCE** picks the first non-null value from a list, ideal for filling gaps in ML datasets like missing model names or scores. It’s your tool for ensuring clean, usable data. This guide will show you how to learn `COALESCE` with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Concept**: See how `COALESCE` handles nulls by selecting the first non-null.
2. **Learn Syntax**: Study `COALESCE` with multiple arguments.
3. **Run Examples**: Try the queries below in a database like MySQL.
4. **Test Nulls**: Add nulls to data and apply `COALESCE`.
5. **ML Spin**: Use `COALESCE` to prep clean data for ML pipelines.

---

## 📜 Syntax

```sql
SELECT COALESCE(column1, column2, ..., default_value) AS alias
FROM table_name;
```

- **Example 1: Default Model Name**:
  ```sql
  SELECT prediction_id,
         COALESCE(model_name, 'Unknown') AS model_name
  FROM predictions;
  ```
  *Replaces null `model_name`s with 'Unknown', like cleaning ML metadata.*

- **Example 2: Fallback Score**:
  ```sql
  SELECT prediction_id, model_id,
         COALESCE(score, 0.0) AS cleaned_score
  FROM predictions;
  ```
  *Sets null `score`s to 0.0, great for ML model evaluation.*

- **Example 3: Multiple Columns**:
  ```sql
  SELECT prediction_id,
         COALESCE(model_name, (SELECT model_name FROM models WHERE models.model_id = predictions.model_id), 'Generic') AS final_name
  FROM predictions;
  ```
  *Tries `model_name`, then `models` table, then 'Generic', useful for robust ML data prep.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: `COALESCE` ensures no nulls in features or labels, critical for ML training.
- **Try This**: Add 5 rows to `predictions` with some `model_name` nulls, then use `COALESCE`. Check with `SELECT COUNT(*) WHERE model_name IS NULL`.
- **Note**: List enough arguments to cover null cases—test with varied data.

---

## 🚀 Next Steps

- **Level Up**: Combine `COALESCE` with `CASE` for advanced logic or `NULLIF` for null creation.
- **Portfolio Win**: Add a `COALESCE` query to `irohanportfolio.netlify.app`, showing ML data cleaning.
- **Challenge**: Clean null `score`s with a default for a portfolio ML report.

Clean like a pro, and let’s rock your SQL journey! 🌟