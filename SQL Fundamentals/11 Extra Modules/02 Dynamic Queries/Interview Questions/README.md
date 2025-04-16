# 🎯 Dynamic Queries Interview Questions

## 🌟 Overview

**Dynamic Queries** shine in SQL interviews by testing your ability to build flexible, runtime-generated SQL. In AI/ML, they’re key for automating ETL pipelines or querying variable ML datasets. Expect questions on `EXECUTE`, `sp_executesql`, or string concatenation, focusing on adaptability and safety. These ML-themed challenges will prep you for FAANG-style interviews—let’s get coding! 🚀

---

## 📚 Interview Questions

### Question 1: Dynamic Feature Filter

- **Difficulty**: Easy
- **Problem**: Given a `features` table (`feature_id INT, user_id INT, model_id INT, feature FLOAT`), write a dynamic query to filter by `user_id` based on a variable input.
- **Solution**:Answer\`\`\`sql -- PostgreSQL PREPARE feature_query AS SELECT \* FROM features WHERE user_id = $1; EXECUTE feature_query(12345); \`\`\` \*\*Explanation\*\*: The \`PREPARE\` statement creates a reusable query, and \`EXECUTE\` runs it with \`user_id = 12345\`. For SQL Server: \`\`\`sql DECLARE @sql NVARCHAR(MAX), @user_id INT = 12345; SET @sql = N'SELECT \* FROM features WHERE user_id = @uid'; EXEC sp_executesql @sql, N'@uid INT', @user_id; \`\`\` Parameters prevent SQL injection.

### Question 2: Dynamic Table Selection

- **Difficulty**: Medium
- **Problem**: Write a dynamic query to select all columns from a table (`predictions` or `features`) based on a variable table name.
- **Solution**:Answer\`\`\`sql -- SQL Server DECLARE @table NVARCHAR(100) = 'predictions'; DECLARE @sql NVARCHAR(MAX) = N'SELECT \* FROM ' + QUOTENAME(@table); EXEC sp_executesql @sql; \`\`\` \*\*Explanation\*\*: \`QUOTENAME\` safely escapes the table name, preventing injection. For PostgreSQL: \`\`\`sql DO $$ DECLARE table_name TEXT := 'predictions'; query TEXT; BEGIN query := format('SELECT \* FROM %I', table_name); EXECUTE query; END $$; \`\`\` The \`format\` function ensures safe table name handling.

### Question 3: Dynamic Metric Query

- **Difficulty**: Hard
- **Problem**: Given a `predictions` table, write a dynamic query to compute a metric (`AVG`, `MAX`, or `MIN`) on `score` for a given `model_id`, with both metric and `model_id` as variables.
- **Solution**:Answer\`\`\`sql -- SQL Server DECLARE @metric NVARCHAR(10) = 'AVG', @model_id INT = 101; DECLARE @sql NVARCHAR(MAX) = N'SELECT ' + @metric + '(score) FROM predictions WHERE model_id = @mid'; EXEC sp_executesql @sql, N'@mid INT', @model_id; \`\`\` \*\*Explanation\*\*: The query dynamically builds the aggregate (\`AVG\`, etc.) and uses a parameter for \`model_id\`. For PostgreSQL: \`\`\`sql DO $$ DECLARE metric TEXT := 'AVG'; model_id INT := 101; query TEXT; BEGIN query := format('SELECT %s(score) FROM predictions WHERE model_id = %s', metric, model_id); EXECUTE query; END $$; \`\`\` Validate \`@metric\` to prevent injection (e.g., restrict to \`AVG\`, \`MAX\`, \`MIN\`).

---

## 💡 Tips for Acing Dynamic Query Interviews

- **Master Parameters**: Use `$1` or `@param` to avoid SQL injection—big in security-focused questions.
- **Practice String Building**: Get comfy with `format` (PostgreSQL) or `QUOTENAME` (SQL Server).
- **Debug Dynamically**: Log generated SQL to catch errors before execution.
- **Know Limits**: Understand DB-specific syntax (e.g., MySQL’s `PREPARE` is less flexible).

---

## 📝 Note

These questions are your launchpad! Modify them (e.g., add filters, change tables) and push solutions to your portfolio for recruiter cred. Got a dynamic SQL brain-teaser? Share it to make this repo epic! 🌟