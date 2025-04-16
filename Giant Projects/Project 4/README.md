# 📈 Project 4: Leaderboard Reporter

## 🌟 Overview

Welcome to **Advanced Analytics Dashboard**, where you’ll build an ML leaderboard using *Joins*, *CTEs*, and *Pivot Queries*! This project creates a dynamic report of model performance, ideal for your *ML-Interview-Preparation-Hub* portfolio to show analytics prowess. 🚀

## 📊 Project Details

- **Scenario**: You’re an ML engineer creating a leaderboard. Your task is to join predictions and models, compute metrics, and pivot for reporting.
- **Goals**: Merge data, calculate rankings, pivot results, and export a CSV.
- **SQL Skills**: *Joins* (INNER), *CTEs* (recursive), *Pivot Queries*.

## 📋 Tasks

1. Use `predictions` and `models` tables.
2. Insert sample data for 2025.
3. Write a CTE to compute average scores by model.
4. Join with `models` to include training dates.
5. Pivot scores by month using *Pivot Queries*.
6. Export the leaderboard to a CSV.
7. Document for portfolio use.

## 💻 Sample Solution

```sql
-- Task 1: Tables exist (predictions, models)

-- Task 2: Insert Sample Data
INSERT INTO models VALUES
(101, '2025-01-01'),
(102, '2025-02-01');
INSERT INTO predictions VALUES
(1, 101, 0.85, '2025-01-15', 'BERT_v1'),
(2, 102, 0.90, '2025-01-20', 'XGBoost_v2'),
(3, 101, 0.87, '2025-02-10', 'BERT_v1'),
(4, 102, 'XGBoost_v2');

-- Task 3 & 4: CTE and Join
WITH avg_scores AS (
    SELECT p.model_id,
           DATE_TRUNC('month', p.prediction_date) AS month,
           AVG(p.score) AS avg_score
    FROM predictions p
    GROUP BY p.model_id, month
)
SELECT a.model_id, a.month, a.avg_score, m.trained_date
FROM avg_scores a
INNER JOIN models m ON a.model_id = m.model_id;

-- Task 5: Pivot (PostgreSQL, manual pivot for simplicity)
SELECT model_id,
       MAX(CASE WHEN month = '2025-01-01' THEN avg_score END) AS jan_score,
       MAX(CASE WHEN month = '2025-02-01' THEN avg_score END) AS feb_score
FROM avg_scores
GROUP BY model_id;

-- Task 6: Export (Pseudo-code)
-- COPY (SELECT ...) TO 'leaderboard.csv' WITH CSV HEADER;

-- Task 7: Document (See Portfolio Tips)
```

**Explanation**:
- *DML* adds test data.
- *CTEs* compute monthly averages.
- *Joins* link models and scores.
- *Pivot Queries* reshape data for reporting.

## 🎯 Expected Outcome

- A pivoted leaderboard table.
- A CSV file (`leaderboard.csv`) with model rankings.
- A portfolio-ready report showcasing ML analytics.

## 💼 Portfolio Tips

- Add `leaderboard.csv` to `irohanportfolio.netlify.app`.
- Write a README explaining the leaderboard and ML use (e.g., model comparison).
- Visualize with Python’s `plotly` (e.g., bar chart of scores).
- Tag skills: *Joins*, *CTEs*, *Pivot Queries*.

## 🔥 Challenge

Add a *Window Function* to rank models globally across all months.

---