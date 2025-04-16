# 🎉 Master Pivot Queries - Reshape Your ML Data Like a Pro!

## 🌟 Welcome

**Pivot Queries** transform rows into columns, perfect for summarizing ML data, like turning model scores into a model-by-date table. They’re your trick for readable ML reports. This guide will walk you through learning pivot queries with ML-themed examples, powering up your *ML-Interview-Preparation-Hub*! 🚀

---

## 🛤️ Learning Path

1. **Grasp the Concept**: Understand how pivoting reshapes data.
2. **Study the Syntax**: Learn pivot techniques (e.g., `CASE` or DB-specific pivot).
3. **Run Examples**: Try the queries below in a database like PostgreSQL or SQL Server.
4. **Test Outputs**: Verify pivoted results match expectations.
5. **Apply to ML**: Use pivots to format ML data for analysis.

---

## 📜 Syntax

```sql
-- Using CASE for pivot
SELECT row_key,
       MAX(CASE WHEN pivot_condition THEN value END) AS col1,
       MAX(CASE WHEN pivot_condition THEN value END) AS col2
FROM table_name
GROUP BY row_key;
```

- **Example 1: Pivot Scores by Model**:
  ```sql
  SELECT model_id,
         MAX(CASE WHEN prediction_date = '2025-04-01' THEN score END) AS apr_01_score,
         MAX(CASE WHEN prediction_date = '2025-04-02' THEN score END) AS apr_02_score
  FROM predictions
  GROUP BY model_id;
  ```
  *Pivots ML prediction scores into date columns per model.*

- **Example 2: Pivot Metrics by Date**:
  ```sql
  SELECT model_id,
         MAX(CASE WHEN eval_date = '2025-04-01' THEN accuracy END) AS apr_01_accuracy,
         MAX(CASE WHEN eval_date = '2025-04-02' THEN accuracy END) AS apr_02_accuracy
  FROM model_metrics
  GROUP BY model_id;
  ```
  *Reshapes ML metrics into date-based columns.*

- **Example 3: PostgreSQL Pivot (Tablefunc)**:
  ```sql
  SELECT * FROM crosstab(
      'SELECT model_id, prediction_date, AVG(score) AS avg_score
       FROM predictions
       GROUP BY model_id, prediction_date
       ORDER BY 1, 2',
      'SELECT DISTINCT prediction_date FROM predictions ORDER BY 1'
  ) AS ct(model_id INT, "2025-04-01" FLOAT, "2025-04-02" FLOAT);
  ```
  *Pivots ML scores by date (PostgreSQL-specific).*

---

## 💡 Practice Tips

- **Tool Up**: Use [SQLFiddle](http://sqlfiddle.com) or PostgreSQL for pivoting.
- **ML Use Case**: Pivots create ML dashboards, like model performance tables.
- **Try This**: Run the first example, check output columns, and compare with raw `SELECT`.
- **Note**: MySQL lacks native pivot—use `CASE`; PostgreSQL needs `crosstab` extension.

---

## 🚀 Next Steps

- **Deepen Skills**: Explore `Dynamic Queries` for flexible pivots or `Window Functions` for rankings.
- **Portfolio Boost**: Add a pivot query to `irohanportfolio.netlify.app`, showing ML data reshaping.
- **Challenge**: Pivot ML scores by model for a portfolio dataset.

Reshape like a champ, and let’s make your SQL skills sparkle! 🌟