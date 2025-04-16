# 📊 Pivot Queries - Reshaping Data for ML Insights

## 🌟 Overview

**Pivot Queries** transform rows into columns, making complex data easier to analyze, like turning a long list into a tidy table. Using `PIVOT` and `UNPIVOT`, you can reshape datasets for reporting or ML preprocessing. In AI/ML, pivot queries are key for summarizing model performance, comparing features across categories, or preparing data for visualizations, saving time in data wrangling.

---

## 📜 Syntax

```sql
SELECT *
FROM table_name
PIVOT (
    aggregate_function(column_to_aggregate)
    FOR pivot_column IN (value1, value2, ...)
) AS alias;
```

- **Basic PIVOT**:
  ```sql
  SELECT *
  FROM predictions
  PIVOT (
      AVG(score)
      FOR model_id IN (101, 102)
  ) AS p;
  ```
- **UNPIVOT** (reverse):
  ```sql
  SELECT *
  FROM pivoted_table
  UNPIVOT (
      score FOR model_id IN (model_101, model_102)
  ) AS u;
  ```
- **Dynamic PIVOT** (SQL Server):
  ```sql
  DECLARE @columns NVARCHAR(MAX), @sql NVARCHAR(MAX);
  SELECT @columns = STRING_AGG(QUOTENAME(model_id), ',')
  FROM (SELECT DISTINCT model_id FROM predictions) AS m;
  SET @sql = '
  SELECT *
  FROM predictions
  PIVOT (
      AVG(score)
      FOR model_id IN (' + @columns + ')
  ) AS p;';
  EXEC sp_executesql @sql;
  ```

---

## 💡 Use Cases in AI/ML

- **Model Comparison**: Pivot prediction scores by model for side-by-side analysis (e.g., `PIVOT ... FOR model_id IN (101, 102)`).
- **Feature Summarization**: Aggregate features by category (e.g., `PIVOT ... FOR feature_type IN (age, income)`).
- **Time-Series Reporting**: Pivot metrics by date for trend analysis (e.g., `PIVOT ... FOR month IN (Jan, Feb)`).
- **Dashboard Prep**: Reshape data for ML visualizations (e.g., pivot accuracy by dataset).

---

## 🔑 Key Features

- **Data Transformation**: Converts rows to columns for intuitive reporting.
- **Aggregation**: Supports `SUM`, `AVG`, `COUNT`, etc., for summarized pivots.
- **Dynamic Pivoting**: Allows runtime column generation (e.g., in SQL Server).
- **Reversibility**: `UNPIVOT` restores pivoted data to its original form.

---

## ✅ Best Practices

- **Choose Aggregates Wisely**: Use `AVG` or `SUM` for meaningful summaries, not just `COUNT`.
- **Limit Pivot Values**: Avoid pivoting on high-cardinality columns (e.g., thousands of `user_id`s).
- **Name Columns Clearly**: Use aliases to make pivoted column names readable (e.g., `model_101` vs. `101`).
- **Test Performance**: Verify pivot queries scale with large datasets using `EXPLAIN`.

---

## ⚠️ Common Pitfalls

- **Missing Values**: Unlisted pivot values (e.g., `model_id = 103`) are excluded—ensure all values are covered.
- **Over-Aggregation**: Aggregating unsuitable columns (e.g., IDs) distorts results.
- **Static PIVOT Limits**: Hardcoding values fails if new categories appear—use dynamic pivots where needed.
- **Performance Lag**: Pivoting large tables without indexes slows queries—index pivot columns first.

---

## 📝 Additional Notes

- **Database Variations**: SQL Server uses `PIVOT`/`UNPIVOT`; PostgreSQL/MySQL require manual pivoting with `CASE` or `GROUP BY`.
- **Workaround for MySQL**: Use `SUM(CASE WHEN model_id = 101 THEN score END) AS model_101`.
- **Dynamic Challenges**: Dynamic pivots (SQL Server) need careful string handling to avoid injection.
- **Storage**: Pivoted results may require temporary tables for further processing.