# ⏰ DateTime Functions Interview Questions

## 🌟 Overview

**DateTime Functions** are a cornerstone of SQL interviews, testing your ability to handle time-series data critical for AI/ML tasks. From extracting date parts to calculating time gaps or aggregating trends, these functions power prediction analysis, model scheduling, and more. These FAANG-style questions, covering `DATE_TRUNC`, `DATEDIFF`, `EXTRACT`, and beyond, will prep you to shine in ML interviews—let’s get started! 🚀

---

## 📚 Interview Questions

### Question 1: Extract Prediction Year
- **Difficulty**: Easy
- **Problem**: Given a `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE, model_name VARCHAR`), extract the year from `prediction_date` for all predictions.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- PostgreSQL
  SELECT prediction_id, EXTRACT(YEAR FROM prediction_date) AS prediction_year
  FROM predictions;
  ```
  **Explanation**: `EXTRACT(YEAR ...)` pulls the year from `prediction_date`. For MySQL:
  ```sql
  SELECT prediction_id, YEAR(prediction_date) AS prediction_year
  FROM predictions;
  ```
  Simple and common in ML to filter or group by year for trend analysis.
  </details>

### Question 2: Days Since Prediction
- **Difficulty**: Medium
- **Problem**: Calculate the number of days between today and each `prediction_date` in the `predictions` table, filtering for predictions since January 2025.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- MySQL
  SELECT prediction_id, DATEDIFF(CURDATE(), prediction_date) AS days_since
  FROM predictions
  WHERE prediction_date >= '2025-01-01';
  ```
  **Explanation**: `DATEDIFF` computes days between current date and `prediction_date`. For PostgreSQL:
  ```sql
  SELECT prediction_id, 
         CURRENT_DATE - prediction_date AS days_since
  FROM predictions
  WHERE prediction_date >= '2025-01-01';
  ```
  Useful for ML monitoring, like checking prediction recency.
  </details>

### Question 3: Monthly Prediction Trends
- **Difficulty**: Medium
- **Problem**: Aggregate average `score` by month for predictions in 2025 from the `predictions` table, ordered chronologically.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- PostgreSQL
  SELECT DATE_TRUNC('month', prediction_date) AS month,
         AVG(score) AS avg_score
  FROM predictions
  WHERE prediction_date BETWEEN '2025-01-01' AND '2025-12-31'
  GROUP BY month
  ORDER BY month;
  ```
  **Explanation**: `DATE_TRUNC('month', ...)` groups by month, averaging scores. For MySQL:
  ```sql
  SELECT DATE_FORMAT(prediction_date, '%Y-%m-01') AS month,
         AVG(score) AS avg_score
  FROM predictions
  WHERE prediction_date BETWEEN '2025-01-01' AND '2025-12-31'
  GROUP BY month
  ORDER BY month;
  ```
  Key for ML time-series analysis, like tracking model performance.
  </details>

### Question 4: Recent Model Performance
- **Difficulty**: Hard
- **Problem**: Join `predictions` with a `models` table (`model_id INT, trained_date DATE`) to find average `score` for predictions made within 30 days of each model’s `trained_date` in 2025.
- **Solution**:
  <details>
  <summary>Answer</summary>
  ```sql
  -- PostgreSQL
  SELECT m.model_id, 
         AVG(p.score) AS avg_score
  FROM models m
  JOIN predictions p ON p.model_id = m.model_id
  WHERE p.prediction_date BETWEEN m.trained_date AND m.trained_date + INTERVAL '30 days'
    AND p.prediction_date BETWEEN '2025-01-01' AND '2025-12-31'
  GROUP BY m.model_id;
  ```
  **Explanation**: Joins on `model_id`, filters predictions within 30 days of `trained_date` using `INTERVAL`. For MySQL:
  ```sql
  SELECT m.model_id, 
         AVG(p.score) AS avg_score
  FROM models m
  JOIN predictions p ON p.model_id = m.model_id
  WHERE p.prediction_date BETWEEN m.trained_date AND DATE_ADD(m.trained_date, INTERVAL 30 DAY)
    AND p.prediction_date BETWEEN '2025-01-01' AND '2025-12-31'
  GROUP BY m.model_id;
  ```
  Tests datetime joins and intervals, common in ML model evaluation.
  </details>

---

## 💡 Tips for Acing DateTime Interview Questions

- **Know Key Functions**: Master `DATE_TRUNC`, `EXTRACT` (PostgreSQL), `DATE_FORMAT`, `DATEDIFF` (MySQL) for time manipulation.
- **Test Date Ranges**: Use `SELECT` to verify filters before aggregating or joining.
- **Optimize with Indexes**: Suggest indexing datetime columns (e.g., `CREATE INDEX ON predictions(prediction_date)`).
- **Explain Logic**: Walk through how you handle time periods or intervals in interviews.

---

## 📝 Note

These questions are your edge! Adapt them (e.g., different time periods, aggregations) and add to your portfolio to impress recruiters. Got a specialized query gem? Share it to make this repo epic! 🌟