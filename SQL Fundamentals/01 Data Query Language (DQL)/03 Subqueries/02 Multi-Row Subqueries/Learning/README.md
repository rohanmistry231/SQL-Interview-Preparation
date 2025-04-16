# 🎉 Master Multi-Row Subqueries - Grab ML Data Lists with Ease!

## 🌟 Welcome

**Multi-Row Subqueries** return multiple rows, ideal for filtering ML data with operators like `IN` or `ANY`. Think of grabbing all predictions from top models or scores in a range. This guide will teach you multi-row subqueries with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Idea**: See how multi-row subqueries return lists for filtering.
2. **Learn Syntax**: Study operators like `IN`, `ANY`, or `ALL` with subqueries.
3. **Run Examples**: Try the queries below in a database like MySQL.
4. **Experiment**: Change subquery conditions to test different lists.
5. **ML Spin**: Use multi-row subqueries to select ML model data dynamically.

---

## 📜 Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE column IN (SELECT column FROM table_name WHERE condition);
-- OR
WHERE column > ANY (SELECT column FROM table_name WHERE condition);
```

- **Example 1: Filter by Top Models**:
  ```sql
  SELECT prediction_id, model_id, score
  FROM predictions
  WHERE model_id IN (SELECT model_id FROM models WHERE created_date > '2025-01-01');
  ```
  *Fetches predictions from newer models, like selecting recent ML experiments.*

- **Example 2: Scores Above Any**:
  ```sql
  SELECT prediction_id, score
  FROM predictions
  WHERE score > ANY (SELECT score FROM predictions WHERE model_id = 101);
  ```
  *Grabs `score`s higher than any from `model_id 101`, great for ML comparisons.*

- **Example 3: Model Name Filter**:
  ```sql
  SELECT model_id, model_name
  FROM predictions
  WHERE model_name IN (SELECT model_name FROM models WHERE model_name LIKE 'Neural%');
  ```
  *Finds predictions for neural network models, useful for ML category analysis.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: Multi-row subqueries help filter datasets (e.g., models by date, scores by threshold) for ML pipelines.
- **Try This**: Add 5 `model_id`s to `models`, then use `IN` to filter `predictions`. Check with `SELECT COUNT(*)`.
- **Note**: Use `IN` for simple lists; `ANY`/`ALL` for comparisons—test both to see differences.

---

## 🚀 Next Steps

- **Level Up**: Try `Correlated Subqueries` for row-specific logic or `Nested Subqueries` for deeper queries.
- **Portfolio Win**: Add a multi-row subquery to `irohanportfolio.netlify.app`, showing ML data filtering.
- **Challenge**: Filter predictions for models created in 2025 for a portfolio ML report.

List like a champ, and let’s rock your SQL journey! 🌟