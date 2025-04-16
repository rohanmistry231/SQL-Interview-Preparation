# ⏰ Project 2: Time-Series Model Tracker

## 🌟 Overview

Dive into **Time-Series Model Tracker**, where you’ll analyze ML prediction trends over time using *DateTime Functions*, *Window Functions*, and *Aggregations*! This project tracks model performance across months, perfect for your *ML-Interview-Preparation-Hub* portfolio to show off time-series skills. 🚀

## 📊 Project Details

- **Scenario**: You’re an ML analyst monitoring prediction scores. Your task is to aggregate scores by month, calculate running averages, and identify top models.
- **Goals**: Process time-series data, compute trends, and export a report.
- **SQL Skills**: *DateTime Functions* (DATE_TRUNC), *Window Functions* (RANK, AVG), *DQL* (SELECT, GROUP BY).

## 📋 Tasks

1. Use the `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE, model_name VARCHAR`).
2. Insert sample data for 2025 predictions.
3. Aggregate average `score` by month using *DateTime Functions*.
4. Calculate a running average score per model with *Window Functions*.
5. Rank models by monthly score.
6. Export results to a CSV for ML reporting.
7. Document the process for your portfolio.

## 💻 Sample Solution

```sql
-- Task 1: Table exists (predictions)

-- Task 2: Insert Sample Data
INSERT INTO predictions VALUES
(1, 101, 0.85, '2025-01-15', 'BERT_v1'),
(2, 102, 0.90, '2025-01-20', 'XGBoost_v2'),
(3, 101, 0.87, '2025-02-10', 'BERT_v1'),
(4, 102, 0.88, '2025-02-15', 'XGBoost_v2'),
(5, 103, 0.92, '2025-03-05', 'LSTM_v3'),
(6, 101, 0.86, '2025-03-20', 'BERT_v1'),
(7, 102, 0.91, '2025-04-01', 'XGBoost_v2'),
(8, 103, 0.89, '2025-04-10', 'LSTM_v3');

-- Task 3: Monthly Aggregation
CREATE TABLE monthly_trends AS
SELECT DATE_TRUNC('month', prediction_date) AS month,
       model_id,
       AVG(score) AS avg_score
FROM predictions
GROUP BY month, model_id;

-- Task 4: Running Average
SELECT model_id,
       prediction_date,
       score,
       AVG(score) OVER (PARTITION BY model_id ORDER BY prediction_date) AS running_avg
FROM predictions;

-- Task 5: Rank Models
SELECT month,
       model_id,
       avg_score,
       RANK() OVER (PARTITION BY month ORDER BY avg_score DESC) AS score_rank
FROM monthly_trends;

-- Task 6: Export (Pseudo-code)
-- COPY (SELECT month, model_id, avg_score FROM monthly_trends) TO 'monthly_trends.csv' WITH CSV HEADER;

-- Task 7: Document (See Portfolio Tips)
```

**Explanation**:
- *DML* inserts time-series data.
- *DateTime Functions* (DATE_TRUNC) group by month.
- *Window Functions* compute running averages and ranks.
- *DQL* creates trend tables for analysis.

## 🎯 Expected Outcome

- A `monthly_trends` table with aggregated scores.
- A CSV file (`monthly_trends.csv`) with model performance.
- A portfolio-ready report showcasing time-series ML skills.

## 💼 Portfolio Tips

- Add `monthly_trends.csv` to `irohanportfolio.netlify.app`.
- Write a README explaining trends and ML use (e.g., model monitoring).
- Plot trends with Python’s `matplotlib` (e.g., score vs. month).
- Tag skills: *DateTime Functions*, *Window Functions*, *DQL*.

## 🔥 Challenge

Add a *CTE* to compute month-over-month score changes for each model.

---