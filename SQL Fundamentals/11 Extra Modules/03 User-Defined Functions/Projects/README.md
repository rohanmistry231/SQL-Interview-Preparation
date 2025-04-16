# 🛠️ User-Defined Functions Projects - Custom ML Logic

## 🌟 Overview

**User-Defined Functions (UDFs)** are your secret weapon for custom SQL logic, from metrics to feature preprocessing. These projects will have you crafting scalar and table-valued UDFs for ML tasks, producing portfolio-worthy tools that show off your AI/ML chops. Let’s build some reusable logic for your *ML-Interview-Preparation-Hub*! 🚀

---

## 📈 Projects

### Project 1: RMSE Metric Function
- **Description**: Create a scalar UDF to compute RMSE for model evaluation, perfect for ML performance tracking.
- **Tasks**:
  1. Use the `predictions` table (`prediction_id INT, model_id INT, score FLOAT, prediction_date DATE`).
  2. Write a PostgreSQL UDF to calculate RMSE between `score` and a predicted value.
  3. Test the UDF on sample data (e.g., `score` vs. 0.9).
  4. Create a query to apply the UDF across all predictions.
  5. Add to your portfolio with a README detailing the UDF and its ML use case.
- **Expected Outcome**: A reusable RMSE function with sample outputs, ready for your portfolio.
- **Challenge Level**: Beginner

### Project 2: Feature Normalization Pipeline
- **Description**: Build a UDF-based pipeline to normalize features and return a processed dataset, streamlining ML preprocessing.
- **Tasks**:
  1. Use the `features` table (`feature_id INT, user_id INT, model_id INT, feature FLOAT, category VARCHAR`).
  2. Create a scalar UDF to normalize `feature` values to 0-1 using min-max scaling.
  3. Write a table-valued UDF to return normalized features for a `model_id`.
  4. Combine both UDFs in a query to process features.
  5. Document in your portfolio with code, outputs, and ML pipeline context.
- **Expected Outcome**: A normalization pipeline with UDFs, showcasing preprocessing skills in your portfolio.
- **Challenge Level**: Intermediate

---

## 🚀 How to Use These Projects

1. **Select a Project**: Go Beginner for quick results or Intermediate for a deeper dive.
2. **Set Up**: Use a DB (PostgreSQL, SQL Server) with the sample tables.
3. **Code & Test**: Write UDFs, test edge cases (e.g., `NULL`, zeros), and verify outputs.
4. **Showcase**: Save code and results, then add a README to `irohanportfolio.netlify.app` with ML insights.
5. **Enhance**: Add new metrics or UDFs to personalize your projects!

> **Pro Tip**: Integrate UDFs with Python (e.g., via `psycopg2`) for a portfolio that screams ML expertise!

---

## 📝 Note

These projects are your stage—shine on it! Customize them (e.g., new metrics, complex UDFs) and push to your portfolio for recruiter cred. Got a UDF project spark? Share it to make this repo epic! 🌟