# 🎉 Master DISTINCT - Clean Up Your ML Data!

## 🌟 Welcome

The **DISTINCT** keyword removes duplicate rows, ensuring your ML datasets are clean and unique. Think of it as deduplicating model IDs or feature categories before training. This guide will show you how to learn `DISTINCT` with ML-focused examples, powering up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Concept**: Understand `DISTINCT` eliminates duplicate rows or values.
2. **Learn the Syntax**: Study how `DISTINCT` fits into `SELECT`.
3. **Run Examples**: Try the queries below in a database like PostgreSQL.
4. **Play Around**: Change columns to see how duplicates vanish.
5. **ML Twist**: Use `DISTINCT` to prep unique data for model analysis.

---

## 📜 Syntax

```sql
SELECT DISTINCT column1, column2, ... FROM table_name;
-- OR
SELECT DISTINCT ON (column) * FROM table_name; -- PostgreSQL-specific
```

- **Example 1: Unique Models**:
  ```sql
  SELECT DISTINCT model_id FROM predictions;
  ```
  *Fetches unique `model_id`s, like getting a list of models for ML evaluation.*

- **Example 2: Unique Combinations**:
  ```sql
  SELECT DISTINCT model_id, model_name FROM predictions;
  ```
  *Removes duplicate pairs, ensuring clean model metadata for ML pipelines.*

- **Example 3: PostgreSQL DISTINCT ON**:
  ```sql
  SELECT DISTINCT ON (model_id) model_id, score FROM predictions;
  ```
  *Keeps the first `score` per `model_id`, useful for selecting top predictions.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or MySQL.
- **ML Use Case**: `DISTINCT` helps create unique feature lists or model inventories for ML preprocessing.
- **Try This**: Insert duplicate `model_id`s into `predictions`, then use `DISTINCT` to clean them. Verify with `SELECT COUNT(DISTINCT model_id)`.
- **Watch Out**: `DISTINCT` on multiple columns deduplicates combinations—test single vs. multi-column queries.

---

## 🚀 Next Steps

- **Level Up**: Pair `DISTINCT` with `WHERE` to filter unique rows or `ORDER BY` to sort them.
- **Portfolio Win**: Add a `DISTINCT` query to `irohanportfolio.netlify.app`, showing how it cleans ML data.
- **Challenge**: Fetch unique `model_name`s for a portfolio ML report.

Keep those datasets clean, and let’s rock your SQL journey! 🌟