# 🎉 Master Dynamic Queries - Build Flexible ML Data Pipelines!

## 🌟 Welcome

**Dynamic Queries** generate SQL code on the fly, ideal for ML tasks like querying variable model metrics. They’re your tool for adaptable data pulls. This guide will teach you dynamic queries with ML examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Flexibility**: Learn how dynamic SQL uses variables.
2. **Study Syntax**: See `PREPARE` and `EXECUTE` in procedures.
3. **Run Examples**: Try the queries below in a database like PostgreSQL.
4. **Test Variability**: Run queries with different inputs.
5. **ML Spin**: Use dynamic queries for ML data exploration.

---

## 📜 Syntax

```sql
DELIMITER //
CREATE PROCEDURE procedure_name(IN param VARCHAR(100))
BEGIN
    SET @sql = CONCAT('SELECT * FROM table_name WHERE column_name = ?', param);
    PREPARE stmt FROM @sql;
    EXECUTE stmt;
    DEALLOCATE PREPARE stmt;
END //
DELIMITER ;
```

- **Example 1: Dynamic Model Filter**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE GetPredictionsByModel(IN modelId INT)
  BEGIN
      SET @sql = CONCAT('SELECT prediction_id, score FROM predictions WHERE model_id = ', modelId);
      PREPARE stmt FROM @sql;
      EXECUTE stmt;
      DEALLOCATE PREPARE stmt;
  END //
  DELIMITER ;
  CALL GetPredictionsByModel(101);
  ```
  *Fetches ML predictions for a dynamic model ID.*

- **Example 2: Dynamic Date Query**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE GetMetricsByDate(IN evalDate DATE)
  BEGIN
      SET @sql = CONCAT('SELECT model_id, accuracy FROM model_metrics WHERE eval_date = ''', evalDate, '''');
      PREPARE stmt FROM @sql;
      EXECUTE stmt;
      DEALLOCATE PREPARE stmt;
  END //
  DELIMITER ;
  CALL GetMetricsByDate('2025-04-01');
  ```
  *Queries ML metrics for a variable date.*

- **Example 3: Dynamic Column**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE GetDynamicColumn(IN colName VARCHAR(50))
  BEGIN
      SET @sql = CONCAT('SELECT ', colName, ' FROM predictions');
      PREPARE stmt FROM @sql;
      EXECUTE stmt;
      DEALLOCATE PREPARE stmt;
  END //
  DELIMITER ;
  CALL GetDynamicColumn('score');
  ```
  *Selects a dynamic ML column.*

---

## 💡 Practice Tips

- **Tool Time**: Use MySQL Workbench or [pgAdmin](https://www.pgadmin.org) for dynamic SQL.
- **ML Use Case**: Dynamic queries adapt ML pipelines, like fetching variable metrics.
- **Try This**: Run `GetPredictionsByModel` with different IDs, verify with static `SELECT`.
- **Debug**: Print `@sql` with `SELECT @sql` to check query construction.

---

## 🚀 Next Steps

- **Level Up**: Try `User-Defined Functions` for reusable logic or `Pivot Queries` for reshaping.
- **Portfolio Win**: Add a dynamic query to `irohanportfolio.netlify.app`, showing ML flexibility.
- **Challenge**: Write a dynamic query for ML metrics in a portfolio dataset.

Adapt like a pro, and let’s rock your SQL journey! 🌟