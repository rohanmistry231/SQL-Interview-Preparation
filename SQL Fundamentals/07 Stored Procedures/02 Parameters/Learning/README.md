# 🎉 Master Parameters in Stored Procedures - Make Your ML Queries Dynamic!

## 🌟 Welcome

**Parameters** in stored procedures allow dynamic inputs, like filtering ML predictions by model or date. They’re your trick for flexible automation. This guide will teach you parameters with ML-themed examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Inputs**: Learn how parameters customize procedures.
2. **Study Syntax**: See `IN`, `OUT`, and `INOUT` parameter types.
3. **Run Examples**: Try the procedures below in a database like MySQL.
4. **Test Flexibility**: Pass different values to parameters.
5. **ML Spin**: Use parameters for tailored ML data tasks.

---

## 📜 Syntax

```sql
DELIMITER //
CREATE PROCEDURE procedure_name(IN param_name datatype, OUT param_name datatype)
BEGIN
    -- SQL statements using parameters
END //
DELIMITER ;
```

- **Example 1: Filter by Model**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE GetPredictionsByModel(IN modelId INT)
  BEGIN
      SELECT prediction_id, score
      FROM predictions
      WHERE model_id = modelId;
  END //
  DELIMITER ;
  ```
  *Fetches ML predictions for a given model ID.*

- **Example 2: Count by Score**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE CountHighScores(IN minScore FLOAT, OUT total INT)
  BEGIN
      SELECT COUNT(*) INTO total
      FROM predictions
      WHERE score >= minScore;
  END //
  DELIMITER ;
  ```
  *Counts ML predictions above a score threshold.*

- **Example 3: Date Range**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE GetPredictionsByDate(IN startDate DATE)
  BEGIN
      SELECT prediction_id, score, prediction_date
      FROM predictions
      WHERE prediction_date >= startDate;
  END //
  DELIMITER ;
  ```
  *Retrieves ML predictions after a specified date.*

---

## 💡 Practice Tips

- **Tool Time**: Use [pgAdmin](https://www.pgadmin.org) or MySQL Workbench to test parameters.
- **ML Use Case**: Parameters enable dynamic ML queries, like filtering predictions for specific models.
- **Try This**: Create `GetPredictionsByModel`, call with `modelId = 101`, and verify with `SELECT * FROM predictions WHERE model_id = 101`.
- **Note**: Declare `OUT` parameters carefully—use `SELECT INTO` to assign values.

---

## 🚀 Next Steps

- **Level Up**: Try `Calling Procedures` to use parameters or `Creating Procedures` for basics.
- **Portfolio Win**: Add a parameterized procedure to `irohanportfolio.netlify.app`, showing ML flexibility.
- **Challenge**: Write a procedure with a score parameter for a portfolio ML dataset.

Flex like a pro, and let’s rock your SQL journey! 🌟