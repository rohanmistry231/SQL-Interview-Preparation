# 🎉 Master CASE Statements - Label Your ML Data Like a Pro!

## 🌟 Welcome

**CASE Statements** let you add conditional logic to SQL, transforming data like labeling ML model performance or categorizing features. They’re your go-to for creating custom outputs in queries. This guide will walk you through learning `CASE` with ML-themed examples, powering up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Grasp the Basics**: Understand how `CASE` evaluates conditions to return values.
2. **Study the Syntax**: Learn simple and searched `CASE` formats.
3. **Run Examples**: Try the queries below in a database like PostgreSQL or MySQL.
4. **Experiment**: Modify conditions to test different outputs.
5. **Apply to ML**: Use `CASE` to label or categorize ML data for analysis.

---

## 📜 Syntax

```sql
-- Simple CASE
SELECT column1,
       CASE column
           WHEN value1 THEN result1
           WHEN value2 THEN result2
           ELSE result_default
       END AS alias
FROM table_name;

-- Searched CASE
SELECT column1,
       CASE
           WHEN condition1 THEN result1
           WHEN condition2 THEN result2
           ELSE result_default
       END AS alias
FROM table_name;
```

- **Example 1: Label Model Performance**:
  ```sql
  SELECT prediction_id, score,
         CASE
             WHEN score >= 0.9 THEN 'Excellent'
             WHEN score >= 0.7 THEN 'Good'
             ELSE 'Needs Improvement'
         END AS performance
  FROM predictions;
  ```
  *Labels predictions based on `score`, like classifying ML model outputs.*

- **Example 2: Categorize Models**:
  ```sql
  SELECT model_id, model_name,
         CASE model_name
             WHEN 'NeuralNet' THEN 'Deep Learning'
             WHEN 'XGBoost' THEN 'Gradient Boosting'
             ELSE 'Other'
         END AS model_type
  FROM predictions;
  ```
  *Groups models by type, great for ML dataset organization.*

- **Example 3: Flag Recent Predictions**:
  ```sql
  SELECT prediction_id, prediction_date,
         CASE
             WHEN prediction_date >= '2025-01-01' THEN 'Recent'
             ELSE 'Older'
         END AS recency
  FROM predictions;
  ```
  *Marks predictions by date, useful for ML time-series analysis.*

---

## 💡 Practice Tips

- **Tool Up**: Use [SQLFiddle](http://sqlfiddle.com) or a local DB to test `CASE`.
- **ML Use Case**: `CASE` is perfect for creating labels (e.g., performance tiers) or features for ML models.
- **Try This**: Create `predictions` with 10 rows, then use `CASE` to label `score < 0.8` as 'Low'. Verify with `SELECT COUNT(*)`.
- **Debug**: Check `ELSE` to avoid nulls—test queries with and without it.

---

## 🚀 Next Steps

- **Deepen Skills**: Pair `CASE` with `COALESCE` for null handling or `WHERE` for filtered logic.
- **Portfolio Boost**: Add a `CASE` query to `irohanportfolio.netlify.app`, explaining its ML labeling role.
- **Challenge**: Label `score`s as 'High', 'Medium', 'Low' for a portfolio ML report.

Label like a champ, and let’s make your SQL skills sparkle! 🌟