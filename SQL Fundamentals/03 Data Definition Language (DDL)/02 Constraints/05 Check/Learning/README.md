# 🎉 Master CHECK - Guard Your ML Data Quality!

## 🌟 Welcome

The **Check** constraint enforces rules on column values, perfect for ensuring ML scores stay within valid ranges or dates make sense. It’s your gatekeeper for data quality. This guide will show you `CHECK` with ML examples, boosting your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Rule**: Understand how `CHECK` validates data.
2. **Learn Syntax**: Study defining it in `CREATE TABLE` or `ALTER TABLE`.
3. **Run Examples**: Try the commands below in a database like PostgreSQL.
4. **Test Limits**: Insert invalid values to trigger errors.
5. **ML Angle**: Use `CHECK` to keep ML data within realistic bounds.

---

## 📜 Syntax

```sql
-- In CREATE TABLE
CREATE TABLE table_name (
    column_name datatype CHECK (condition),
    ...
);

-- In ALTER TABLE
ALTER TABLE table_name
ADD CONSTRAINT constraint_name CHECK (condition);
```

- **Example 1: Valid Scores**:
  ```sql
  CREATE TABLE predictions (
      prediction_id INT,
      score FLOAT CHECK (score >= 0 AND score <= 1)
  );
  ```
  *Ensures `score`s are between 0 and 1 for ML predictions.*

- **Example 2: Positive Accuracy**:
  ```sql
  CREATE TABLE model_metrics (
      metric_id INT,
      accuracy FLOAT CHECK (accuracy > 0)
  );
  ```
  *Forces `accuracy` to be positive for ML metrics.*

- **Example 3: Add Check Constraint**:
  ```sql
  ALTER TABLE predictions
  ADD CONSTRAINT valid_date CHECK (prediction_date >= '2025-01-01');
  ```
  *Restricts `prediction_date` to 2025 onward in an ML table.*

---

## 💡 Practice Tips

- **Get Hands-On**: Use [SQLFiddle](http://sqlfiddle.com) or PostgreSQL (MySQL support varies).
- **ML Use Case**: `CHECK` keeps ML data valid, like ensuring scores or metrics fit model expectations.
- **Try This**: Create `predictions`, insert a `score` of 1.5, and verify the error. Check with `SELECT *`.
- **Tip**: Name constraints for clarity—unnamed ones are hard to drop later.

---

## 🚀 Next Steps

- **Go Deeper**: Combine `CHECK` with `Not Null` or `Default` for robust rules.
- **Portfolio Boost**: Add a `CHECK` table to `irohanportfolio.netlify.app`, explaining ML data validation.
- **Challenge**: Create a table with a score range check for a portfolio ML dataset.

Guard like a boss, and let’s make your SQL skills soar! 🌟