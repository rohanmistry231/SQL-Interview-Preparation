# 🎉 Master ROLLBACK - Undo ML Data Mistakes!

## 🌟 Welcome

The **ROLLBACK** command discards transaction changes, perfect for reverting ML data errors like incorrect predictions or score updates. It’s your safety net for data integrity. This guide will teach you `ROLLBACK` with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Undo**: Learn how `ROLLBACK` cancels uncommitted changes.
2. **Study Syntax**: See the straightforward `ROLLBACK` command.
3. **Run Examples**: Try the commands below in a database like MySQL.
4. **Test Reverts**: Make changes, rollback, and check data.
5. **ML Spin**: Use `ROLLBACK` to fix ML dataset errors before saving.

---

## 📜 Syntax

```sql
ROLLBACK;
```

- **Example 1: Undo Insert**:
  ```sql
  BEGIN;
  INSERT INTO predictions VALUES (1, 101, 0.9, '2025-04-01', 'NeuralNet');
  ROLLBACK;
  ```
  *Discards a new ML prediction, keeping the table unchanged.*

- **Example 2: Revert Update**:
  ```sql
  BEGIN;
  UPDATE predictions SET score = 0.1 WHERE prediction_id = 1;
  ROLLBACK;
  ```
  *Cancels an ML score update, restoring original data.*

- **Example 3: Cancel Batch Changes**:
  ```sql
  BEGIN;
  INSERT INTO predictions VALUES (2, 102, 0.85, '2025-04-02', 'XGBoost');
  DELETE FROM predictions WHERE prediction_id = 1;
  ROLLBACK;
  ```
  *Undoes multiple ML data changes in one go.*

---

## 💡 Practice Tips

- **Tool Time**: Practice on [DB Fiddle](https://www.db-fiddle.com) or PostgreSQL.
- **ML Use Case**: `ROLLBACK` saves ML datasets from bad updates, like fixing wrong prediction scores.
- **Try This**: Start a transaction, update `score` in `predictions`, rollback, then verify with `SELECT * FROM predictions`.
- **Note**: `ROLLBACK` only works before `COMMIT`—test changes with `SELECT` first.

---

## 🚀 Next Steps

- **Level Up**: Try `COMMIT` to save changes or `SAVEPOINT` for partial rollbacks.
- **Portfolio Win**: Add a `ROLLBACK` example to `irohanportfolio.netlify.app`, showing ML error recovery.
- **Challenge**: Update and rollback ML scores for a portfolio dataset.

Undo like a pro, and let’s rock your SQL journey! 🌟