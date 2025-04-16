# 🛠️ Dynamic Queries Projects - Flexible ML Pipelines

## 🌟 Overview

**Dynamic Queries** let you craft SQL that adapts on the fly, perfect for ML pipelines with variable inputs. Using `EXECUTE` or `sp_executesql`, these projects will have you building flexible feature queries and ETL flows, creating portfolio gems that scream versatility. Get ready to impress recruiters with your *ML-Interview-Preparation-Hub*! 🚀

---

## 📈 Projects

### Project 1: Dynamic Feature Selector
- **Description**: Build a dynamic query to fetch features for a given `user_id`, showcasing runtime flexibility for ML preprocessing.
- **Tasks**:
  1. Use the `features` table (`feature_id INT, user_id INT, model_id INT, feature FLOAT, category VARCHAR`).
  2. Write a PostgreSQL `PREPARE`/`EXECUTE` query to select features by `user_id` input.
  3. Test with multiple `user_id` values (e.g., 12345, 67890).
  4. Save the query in a script and document its use in feature engineering.
  5. Add to your portfolio with a README explaining the ML pipeline context.
- **Expected Outcome**: A reusable query script that fetches features dynamically, ready for your portfolio.
- **Challenge Level**: Beginner

### Project 2: Automated Model Metric Report
- **Description**: Create a dynamic query to generate model metrics (e.g., `AVG`, `MAX`) for any `model_id`, automating ML evaluation.
- **Tasks**:
  1. Use the `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE`).
  2. Write a SQL Server `sp_executesql` query to compute a metric (`AVG`, `MAX`, `MIN`) for a variable `model_id`.
  3. Allow runtime selection of the metric and `model_id` via parameters.
  4. Output results to a temporary table for reporting.
  5. Document in your portfolio with query code, sample outputs, and ML use case.
- **Expected Outcome**: A dynamic report generator for model metrics, showcasing pipeline automation in your portfolio.
- **Challenge Level**: Intermediate

---

## 🚀 How to Use These Projects

1. **Choose a Project**: Start with Beginner for quick setup or tackle Intermediate for deeper skills.
2. **Set Up**: Use a DB (PostgreSQL, SQL Server) with the sample tables.
3. **Code & Test**: Build the queries, validate with `EXPLAIN`, and ensure safe parameterization.
4. **Showcase**: Save scripts and outputs, then add a README to `irohanportfolio.netlify.app` with ML context.
5. **Customize**: Add filters or metrics to make projects uniquely yours!

> **Pro Tip**: Pair with a Python script to automate query execution for a portfolio wow-factor!

---

## 📝 Note

These projects are your playground! Tweak them (e.g., new tables, extra parameters) and add to your portfolio to stand out. Got a dynamic query idea? Share it to level up this repo! 🌟