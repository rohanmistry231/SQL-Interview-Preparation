# 🎉 Master Multiple Column Update - Revamp Your ML Data in One Go!

## 🌟 Welcome

**Multiple Column Update** changes several columns at once, ideal for updating ML prediction scores and model names together. It’s your shortcut for batch data fixes. This guide will teach you multi-column `UPDATE` with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Idea**: See how `UPDATE` handles multiple columns in one query.
2. **Learn Syntax**: Study the `SET` clause with comma-separated assignments.
3. **Run Examples**: Try the queries below in a database like MySQL.
4. **Tweak Updates**: Modify multiple columns to test outcomes.
5. **ML Spin**: Use multi-column updates to align ML datasets for training.

---

## 📜 Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
[WHERE condition];
```

- **Example 1: Update Score and Name**:
  ```sql
  UPDATE predictions
  SET score = 0.95, model_name = 'DeepLearning'
  WHERE model_id = 102;
  ```
  *Updates `score` and `model_name` for `model_id 102`, like refining ML results.*

- **Example 2: Fix Date and Score**:
  ```sql
  UPDATE predictions
  SET prediction_date = '2025-04-02', score = 0.88
  WHERE prediction_id = 3;
  ```
  *Corrects `prediction_date` and `score`, great for ML time-series fixes.*

- **Example 3: Standardize Multiple Fields**:
  ```sql
  UPDATE predictions
  SET model_name = 'XGBoost', score = 0.9
  WHERE score < 0.5;
  ```
  *Sets low `score`s to 0.9 and updates `model_name`, useful for ML data normalization.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: Multi-column updates streamline ML data prep by fixing multiple features at once, like scores and metadata.
- **Try This**: Add 5 rows to `predictions`, update `score` and `model_name` for `model_id = 103`, then check with `SELECT * FROM predictions`.
- **Note**: Preview changes with `SELECT`—bulk updates without `WHERE` can overwrite everything!

---

## 🚀 Next Steps

- **Level Up**: Try `Update with Conditions` for targeted edits or `Single Column Update` for focused changes.
- **Portfolio Win**: Add a multi-column update query to `irohanportfolio.netlify.app`, showing ML data refinement.
- **Challenge**: Update `score` and `prediction_date` for low scores in a portfolio ML dataset.

Revamp like a champ, and let’s rock your SQL journey! 🌟