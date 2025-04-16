# 🎉 Master BEFORE Triggers - Validate Your ML Data First!

## 🌟 Welcome

**BEFORE Triggers** run before a database event, ideal for validating or modifying ML data, like ensuring valid prediction scores. They’re your gatekeeper for data quality. This guide will teach you `BEFORE` triggers with ML-themed examples, leveling up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Understand Timing**: Learn how `BEFORE` triggers act pre-event.
2. **Study Syntax**: See how to use `NEW` and `OLD` in `BEFORE` triggers.
3. **Run Examples**: Try the triggers below in a database like MySQL.
4. **Test Validation**: Insert or update data to see trigger effects.
5. **ML Spin**: Use `BEFORE` triggers to clean ML datasets.

---

## 📜 Syntax

```sql
DELIMITER //
CREATE TRIGGER trigger_name
BEFORE {INSERT | UPDATE | DELETE}
ON table_name
FOR EACH ROW
BEGIN
    -- Trigger logic
END //
DELIMITER ;
```

- **Example 1: Cap Prediction Score**:
  ```sql
  DELIMITER //
  CREATE TRIGGER cap_score
  BEFORE INSERT ON predictions
  FOR EACH ROW
  BEGIN
      IF NEW.score > 1 THEN
          SET NEW.score = 1;
      END IF;
  END //
  DELIMITER ;
  ```
  *Caps ML prediction scores at 1 before insertion.*

- **Example 2: Default Model Name**:
  ```sql
  DELIMITER //
  CREATE TRIGGER set_default_model
  BEFORE INSERT ON predictions
  FOR EACH ROW
  BEGIN
      IF NEW.model_name IS NULL THEN
          SET NEW.model_name = 'Unknown';
      END IF;
  END //
  DELIMITER ;
  ```
  *Sets a default name for ML predictions.*

- **Example 3: Block Low Scores**:
  ```sql
  DELIMITER //
  CREATE TRIGGER block_low_score
  BEFORE UPDATE ON predictions
  FOR EACH ROW
  BEGIN
      IF NEW.score < 0.1 THEN
          SIGNAL SQLSTATE '45000'
          SET MESSAGE_TEXT = 'Score too low for update';
      END IF;
  END //
  DELIMITER ;
  ```
  *Prevents ML score updates below 0.1.*

---

## 💡 Practice Tips

- **Tool Time**: Use [pgAdmin](https://www.pgadmin.org) or MySQL Workbench to test triggers.
- **ML Use Case**: `BEFORE` triggers ensure ML data quality, like validating scores before saving.
- **Try This**: Create `cap_score`, insert a row with `score = 1.5`, and verify it’s capped at 1.
- **Note**: Use `NEW` to modify incoming data—`OLD` is read-only in `BEFORE`.

---

## 🚀 Next Steps

- **Level Up**: Try `AFTER Triggers` for post-event actions or `Creating Triggers` for basics.
- **Portfolio Win**: Add a `BEFORE` trigger to `irohanportfolio.netlify.app`, showing ML data validation.
- **Challenge**: Write a trigger to validate ML scores for a portfolio dataset.

Validate like a pro, and let’s rock your SQL journey! 🌟