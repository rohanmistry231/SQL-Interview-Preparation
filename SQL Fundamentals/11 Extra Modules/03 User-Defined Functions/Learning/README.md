# 🎉 Master User-Defined Functions - Customize Your ML Calculations!

## 🌟 Welcome

**User-Defined Functions (UDFs)** let you create reusable SQL logic, like scaling ML scores or classifying models. They’re your tool for tailored computations. This guide will show you UDFs with ML examples, boosting your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Idea**: Understand how UDFs return values for queries.
2. **Learn Syntax**: Study `CREATE FUNCTION` syntax.
3. **Run Examples**: Try the functions below in a database like MySQL.
4. **Test Outputs**: Use UDFs in `SELECT` and verify results.
5. **ML Angle**: Apply UDFs to ML data processing.

---

## 📜 Syntax

```sql
DELIMITER //
CREATE FUNCTION function_name(param datatype) RETURNS datatype
BEGIN
    -- Logic
    RETURN value;
END //
DELIMITER ;
```

- **Example 1: Scale Score**:
  ```sql
  DELIMITER //
  CREATE FUNCTION ScaleScore(score FLOAT) RETURNS FLOAT
  BEGIN
      RETURN score * 100;
  END //
  DELIMITER ;
  SELECT prediction_id, ScaleScore(score) AS scaled_score
  FROM predictions;
  ```
  *Scales ML prediction scores by 100.*

- **Example 2: Classify Accuracy**:
  ```sql
  DELIMITER //
  CREATE FUNCTION ClassifyAccuracy(accuracy FLOAT) RETURNS VARCHAR(20)
  BEGIN
      IF accuracy >= 0.9 THEN
          RETURN 'Excellent';
      ELSEIF accuracy >= 0.7 THEN
          RETURN 'Good';
      ELSE
          RETURN 'Needs Work';
      END IF;
  END //
  DELIMITER ;
  SELECT model_id, ClassifyAccuracy(accuracy) AS rating
  FROM model_metrics;
  ```
  *Classifies ML model accuracy.*

- **Example 3: Date Flag**:
  ```sql
  DELIMITER //
  CREATE FUNCTION IsRecent(evalDate DATE) RETURNS BOOLEAN
  BEGIN
      RETURN evalDate >= '2025-04-01';
  END //
  DELIMITER ;
  SELECT metric_id, IsRecent(eval_date) AS is_recent
  FROM model_metrics;
  ```
  *Flags recent ML metric dates.*

---

## 💡 Practice Tips

- **Get Hands-On**: Use [DBeaver](https://dbeaver.io) or PostgreSQL for UDFs.
- **ML Use Case**: UDFs simplify ML calculations, like normalizing scores.
- **Try This**: Create `ScaleScore`, run `SELECT ScaleScore(0.85)`, and verify output (85).
- **Tip**: Ensure `RETURN` matches declared type—mismatches cause errors.

---

## 🚀 Next Steps

- **Go Deeper**: Explore `Dynamic Queries` for flexibility or `Window Functions` for analytics.
- **Portfolio Boost**: Add a UDF to `irohanportfolio.netlify.app`, explaining ML data logic.
- **Challenge**: Write a UDF for ML score scaling in a portfolio dataset.

Compute like a boss, and let’s make your SQL skills soar! 🌟