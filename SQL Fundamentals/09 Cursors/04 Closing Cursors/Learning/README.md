# 🎉 Master Closing Cursors - Wrap Up Your ML Data Loop!

## 🌟 Welcome

**Closing Cursors** releases cursor resources after processing ML data, like after summarizing predictions. It’s your cleanup step for efficient database use. This guide will teach you closing cursors with ML examples, supercharging your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Cleanup**: Learn why closing cursors frees resources.
2. **Study Syntax**: See the `CLOSE` statement.
3. **Run Examples**: Try the code below in a database like MySQL.
4. **Test Closure**: Run a procedure and verify cursor closure.
5. **ML Spin**: Use closing to maintain ML data pipelines.

---

## 📜 Syntax

```sql
DELIMITER //
CREATE PROCEDURE procedure_name()
BEGIN
    DECLARE cursor_name CURSOR FOR SELECT ...;
    OPEN cursor_name;
    -- Fetch logic
    CLOSE cursor_name;
END //
DELIMITER ;
```

- **Example 1: Close Prediction Cursor**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE CleanPredictions()
  BEGIN
      DECLARE v_model_id INT;
      DECLARE done INT DEFAULT 0;
      DECLARE pred_cursor CURSOR FOR 
          SELECT model_id FROM predictions;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
      OPEN pred_cursor;
      read_loop: LOOP
          FETCH pred_cursor INTO v_model_id;
          IF done THEN
              LEAVE read_loop;
          END IF;
      END LOOP;
      CLOSE pred_cursor;
  END //
  DELIMITER ;
  ```
  *Closes a cursor after reading ML predictions.*

- **Example 2: Close Summary Cursor**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE UpdateSummary()
  BEGIN
      DECLARE v_model_id INT;
      DECLARE v_avg_score FLOAT;
      DECLARE done INT DEFAULT 0;
      DECLARE summary_cursor CURSOR FOR 
          SELECT model_id, AVG(score) AS avg_score 
          FROM predictions 
          GROUP BY model_id;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
      OPEN summary_cursor;
      read_loop: LOOP
          FETCH summary_cursor INTO v_model_id, v_avg_score;
          IF done THEN
              LEAVE read_loop;
          END IF;
          INSERT INTO prediction_summary (model_id, avg_score)
          VALUES (v_model_id, v_avg_score);
      END LOOP;
      CLOSE summary_cursor;
  END //
  DELIMITER ;
  ```
  *Closes a cursor after summarizing ML data.*

- **Example 3: Close Filtered Cursor**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE ProcessFiltered()
  BEGIN
      DECLARE v_model_id INT;
      DECLARE done INT DEFAULT 0;
      DECLARE filter_cursor CURSOR FOR 
          SELECT model_id FROM predictions WHERE score >= 0.9;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
      OPEN filter_cursor;
      read_loop: LOOP
          FETCH filter_cursor INTO v_model_id;
          IF done THEN
              LEAVE read_loop;
          END IF;
      END LOOP;
      CLOSE filter_cursor;
  END //
  DELIMITER ;
  ```
  *Closes a cursor for high-scoring ML predictions.*

---

## 💡 Practice Tips

- **Tool Time**: Use [DBeaver](https://dbeaver.io) or pgAdmin to test cursors.
- **ML Use Case**: Closing cursors ensures clean ML data pipelines, avoiding resource leaks.
- **Try This**: Run `UpdateSummary`, then check no cursors remain open (no errors on procedure rerun).
- **Note**: Always close cursors—open cursors can lock resources until the session ends.

---

## 🚀 Next Steps

- **Level Up**: Revisit `Fetching Data` for processing or `Declaring Cursors` for setup.
- **Portfolio Win**: Add a cursor-closing example to `irohanportfolio.netlify.app`, showing ML pipeline cleanup.
- **Challenge**: Close a cursor after processing ML data in a portfolio dataset.

Wrap up like a pro, and let’s rock your SQL game! 🌟