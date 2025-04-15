# 🛠️ Creating Procedures - Building Reusable Logic

## 🌟 Overview

**Creating Stored Procedures** involves defining a named set of SQL statements stored in the database, executable as a single unit. Written using Data Definition Language (DDL), stored procedures encapsulate complex logic, improve performance through precompilation, and enhance security by controlling access.

In AI/ML, creating procedures is key for **automating repetitive tasks**, like cleaning datasets or logging model metrics, streamlining pipelines. For freshers, it’s a **core interview topic**, often tested in questions about reusable code, database optimization, and production workflows.

---

## 📜 Syntax

```sql
-- Generic SQL (varies by database)
CREATE PROCEDURE procedure_name
AS
BEGIN
    -- SQL statements
END;
```

- **Basic Example** (SQL Server syntax for portability):
  ```sql
  CREATE PROCEDURE CleanTrainingData
  AS
  BEGIN
      DELETE FROM training_data WHERE feature1 IS NULL;
  END;
  ```
- **With Logic** (PostgreSQL-style for clarity):
  ```sql
  CREATE PROCEDURE UpdateModelStatus()
  LANGUAGE SQL
  AS $$
      UPDATE models
      SET status = 'active'
      WHERE accuracy > 0.9;
  $$;
  ```

---

## 💡 Use Cases in AI/ML

- **Data Preprocessing**: Create a procedure to normalize `training_data` features.
- **Model Logging**: Define a procedure to insert `predictions` into `logs`.
- **ETL Automation**: Build a procedure to transform `staging_table` for ML pipelines.
- **Experiment Tracking**: Create a procedure to update `experiments` with results.
- **Batch Scoring**: Define logic to score `test_data` for model evaluation.

---

## 🔑 Key Features

- **Precompiled**: Executes faster than ad-hoc queries.
- **Reusable**: Callable multiple times without rewriting.
- **Modular**: Encapsulates complex logic for clarity.
- **Secure**: Limits direct table access, reducing risks.

---

## ✅ Best Practices

- **Name Clearly**: Use descriptive names (e.g., `CleanTrainingData`) for readability.
- **Keep Simple**: Avoid overly complex logic to ease maintenance.
- **Comment Code**: Add comments to explain purpose and steps.
- **Test First**: Create in a sandbox to verify functionality.

---

## ⚠️ Common Pitfalls

- **Syntax Errors**: Database-specific syntax (e.g., MySQL vs. SQL Server) causes failures.
- **Overcomplication**: Packing too much logic makes debugging hard.
- **No Error Handling**: Omitting checks risks silent failures.
- **Name Conflicts**: Duplicate procedure names overwrite existing ones.

---

## 📝 Additional Notes

- **Database Variations**:
  - **MySQL**: Uses `DELIMITER` and `CREATE PROCEDURE ... BEGIN ... END`.
  - **PostgreSQL**: Supports `CREATE PROCEDURE` or `CREATE FUNCTION` with `LANGUAGE SQL`.
  - **SQL Server**: Uses `CREATE PROCEDURE ... AS BEGIN ... END`.
  - **Oracle**: Employs `CREATE OR REPLACE PROCEDURE` with PL/SQL blocks.
- **Versioning**: Use `OR REPLACE` (where supported) to update procedures safely.
- **Permissions**: Ensure proper `CREATE` privileges for the schema.