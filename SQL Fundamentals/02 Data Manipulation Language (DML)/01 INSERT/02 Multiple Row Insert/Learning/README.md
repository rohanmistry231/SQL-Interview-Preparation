# 🎉 Master Multiple Row Insert - Bulk Up Your ML Data Fast!

## 🌟 Welcome

**Multiple Row Insert** adds several rows at once, ideal for loading batches of ML predictions or feature sets efficiently. It’s your shortcut for scaling datasets. This guide will teach you multi-row `INSERT` with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Idea**: See how multi-row `INSERT` stacks values for bulk entry.
2. **Learn Syntax**: Study the comma-separated value list format.
3. **Run Examples**: Try the queries below in a database like MySQL.
4. **Tweak Batches**: Add or remove rows to test efficiency.
5. **ML Spin**: Use multi-row inserts to populate ML training or test datasets.

---

## 📜 Syntax

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES 
    (value1a, value2a, ...),
    (value1b, value2b, ...),
    ...;
```

- **Example 1: Batch Predictions**:
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, prediction_date, model_name)
  VALUES 
      (4, 101, 0.88, '2025-04-03', 'NeuralNet'),
      (5, 102, 0.76, '2025-04-03', 'XGBoost'),
      (6, 103, 0.92, '2025-04-03', 'DeepLearning');
  ```
  *Adds three predictions at once, like logging a day’s ML outputs.*

- **Example 2: Partial Columns**:
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score)
  VALUES 
      (7, 104, 0.85),
      (8, 105, 0.91);
  ```
  *Inserts two rows with `score` only, great for quick ML data batches.*

- **Example 3: Mixed Data**:
  ```sql
  INSERT INTO predictions (prediction_id, model_id, score, model_name)
  VALUES 
      (9, 106, 0.79, 'RandomForest'),
      (10, 107, 0.94, 'GradientBoost');
  ```
  *Loads varied ML model data, useful for diverse dataset creation.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: Multi-row inserts speed up loading ML experiment results or feature batches for training.
- **Try This**: Insert 5 rows into `predictions` with different `score`s, then check with `SELECT COUNT(*) FROM predictions`.
- **Note**: Ensure consistent column counts per row—mismatches break the query. Test small batches first.

---

## 🚀 Next Steps

- **Level Up**: Try `Insert from Select` for dynamic bulk inserts or `Single Row Insert` for precision.
- **Portfolio Win**: Add a multi-row insert query to `irohanportfolio.netlify.app`, showing ML dataset creation.
- **Challenge**: Insert 3 predictions with varied `model_name`s for a portfolio ML dataset.

Bulk up like a champ, and let’s rock your SQL journey! 🌟