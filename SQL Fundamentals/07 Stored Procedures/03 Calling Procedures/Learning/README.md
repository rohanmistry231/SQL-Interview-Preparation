# 🎉 Master Calling Stored Procedures - Run Your ML Automation!

## 🌟 Welcome

**Calling Stored Procedures** executes your saved SQL logic, like running ML data summaries or filtered queries. It’s your way to trigger automation. This guide will show you how to call procedures with ML examples, boosting your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Idea**: Understand how to invoke procedures with `CALL`.
2. **Learn Syntax**: Study calling with or without parameters.
3. **Run Examples**: Try the calls below in a database like PostgreSQL.
4. **Test Outputs**: Verify procedure results match expectations.
5. **ML Angle**: Use calls to automate ML data tasks.

---

## 📜 Syntax

```sql
CALL procedure_name([parameter1, parameter2, ...]);
```

- **Example 1: Simple Call**:
  ```sql
  -- Assume procedure: GetPredictionCount
  CALL GetPredictionCount();
  ```
  *Runs a procedure to count ML predictions.*

- **Example 2: Parameter Call**:
  ```sql
  -- Assume procedure: GetPredictionsByModel(IN modelId INT)
  CALL GetPredictionsByModel(101);
  ```
  *Fetches ML predictions for model ID 101.*

- **Example 3: Output Parameter**:
  ```sql
  -- Assume procedure: CountHighScores(IN minScore FLOAT, OUT total INT)
  SET @total = 0;
  CALL CountHighScores(0.9, @total);
  SELECT @total AS high_score_count;
  ```
  *Gets the count of high-scoring ML predictions.*

---

## 💡 Practice Tips

- **Get Hands-On**: Use MySQL Workbench or [SQLFiddle](http://sqlfiddle.com) to call procedures.
- **ML Use Case**: Calling procedures automates ML workflows, like generating model reports.
- **Try This**: Create a procedure to list predictions, call it, and verify with a manual `SELECT`.
- **Tip**: For `OUT` parameters, use session variables (e.g., `@total`) and `SELECT` to view results.

---

## 🚀 Next Steps

- **Go Deeper**: Explore `Parameters` for dynamic calls or `Dropping Procedures` to clean up.
- **Portfolio Boost**: Add a `CALL` example to `irohanportfolio.netlify.app`, explaining ML automation.
- **Challenge**: Call a procedure to summarize ML data in a portfolio dataset.

Execute like a boss, and let’s make your SQL skills soar! 🌟