# 🎉 Master Fetching Data with Cursors - Process Your ML Data!

## 🌟 Welcome

**Fetching Data** with cursors pulls rows from your query, perfect for analyzing ML predictions one by one, like computing model stats. It’s your core loop action. This guide will show you fetching data with ML examples, boosting your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Get the Action**: Understand how `FETCH` retrieves cursor rows.
2. **Learn Syntax**: Study fetching into variables.
3. **Run Examples**: Try the code below in a database like PostgreSQL.
4. **Test Loops**: Fetch rows and process them to verify.
5. **ML Angle**: Use fetching to analyze ML datasets.

---

## 📜 Syntax

```sql
DELIMITER //
CREATE PROCEDURE procedure_name()
BEGIN
    DECLARE variable1 datatype;
    DECLARE cursor_name CURSOR FOR SELECT ...;
    OPEN cursor_name;
    FETCH cursor_name INTO variable1, ...;
    -- Loop and process
END //
DELIMITER ;
```

- **Example 1: Fetch Predictions**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE SummarizePredictions()
  BEGIN
      DECLARE v_model_id INT;
      DECLARE v_score FLOAT;
      DECLARE done INT DEFAULT 0;
      DECLARE pred_cursor CURSOR FOR 
          SELECT model_id, score FROM predictions;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
      OPEN pred_cursor;
      read_loop: LOOP
          FETCH pred_cursor INTO v_model_id, v_score;
          IF done THEN
              LEAVE read_loop;
          END IF;
          -- Example: Insert summary
          INSERT INTO prediction_summary (model_id, avg_score, total_predictions)
          VALUES (v_model_id, v_score, 1)
          ON DUPLICATE KEY UPDATE total_predictions = total_predictions + 1, avg_score = (avg_score + v_score) / 2;
      END LOOP;
      CLOSE pred_cursor;
  END //
  DELIMITER ;
  ```
  *Fetches ML predictions to build a summary.*

- **Example 2: Fetch High Scores**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE LogHighScores()
  BEGIN
      DECLARE v_model_id INT;
      DECLARE v_score FLOAT;
      DECLARE done INT DEFAULT 0;
      DECLARE score_cursor CURSOR FOR 
          SELECT model_id, score FROM predictions WHERE score >= 0.9;
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
      OPEN score_cursor;
      read_loop: LOOP
          FETCH score_cursor INTO v_model_id, v_score;
          IF done THEN
              LEAVE read_loop;
          END IF;
          -- Example: Log high scores
          INSERT INTO prediction_summary (model_id, avg_score)
          VALUES (v_model_id, v_score);
      END LOOP;
      CLOSE score_cursor;
  END //
  DELIMITER ;
  ```
  *Processes high-scoring ML predictions.*

- **Example 3: Fetch Recent Data**:
  ```sql
  DELIMITER //
  CREATE PROCEDURE TrackRecent()
  BEGIN
      DECLARE v_model_id INT;
      DECLARE v_score FLOAT;
      DECLARE done INT DEFAULT 0;
      DECLARE recent_cursor CURSOR FOR 
          SELECT model_id, score FROM predictions WHERE prediction_date >= '2025-04-01';
      DECLARE CONTINUE HANDLER FOR NOT FOUND SET done = 1;
      OPEN recent_cursor;
      read_loop: LOOP
          FETCH recent_cursor INTO v_model_id, v_score;
          IF done THEN
              LEAVE read_loop;
          END IF;
          -- Example: Update summary
          UPDATE prediction_summary 
          SET avg_score = v_score, total_predictions = total_predictions + 1
          WHERE model_id = v_model_id;
      END LOOP;
      CLOSE recent_cursor;
  END //
  DELIMITER ;
  ```
  *Fetches recent ML predictions for updates.*

---

## 💡 Practice Tips

- **Get Hands-On**: Use MySQL Workbench or [SQLFiddle](http://sqlfiddle.com) to test fetching.
- **ML Use Case**: Fetching processes ML data, like summarizing predictions for model evaluation.
- **Try This**: Create `prediction_summary`, run `SummarizePredictions`, and check inserted rows.
- **Tip**: Use a `done` flag with a `NOT FOUND` handler to exit loops cleanly.

---

## 🚀 Next Steps

- **Go Deeper**: Explore `Closing Cursors` to finish up or `Opening Cursors` for setup.
- **Portfolio Boost**: Add a fetch example to `irohanportfolio.netlify.app`, explaining ML data processing.
- **Challenge**: Fetch ML predictions to summarize in a portfolio dataset.

Process like a boss, and let’s make your SQL skills soar! 🌟