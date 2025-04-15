# 🔒 Constraints - Enforcing Data Integrity

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master constraints to ensure reliable, high-quality data for AI/ML interviews! 🚀</p>

---

## 🌟 What are Constraints?

**Constraints** in SQL are rules applied to table columns or relationships to **enforce data integrity** and consistency in a database. Defined using Data Definition Language (DDL), constraints prevent invalid data entry, ensuring tables store accurate and meaningful data. Common constraints include `PRIMARY KEY`, `FOREIGN KEY`, `UNIQUE`, `NOT NULL`, `CHECK`, and `DEFAULT`.

In AI/ML, constraints are critical for maintaining clean, reliable datasets for training models, preventing errors like duplicates or missing values. For freshers, constraints are a **key interview topic**, often tested in schema design questions to evaluate your understanding of data quality! 💡

---

## 🎯 Why Constraints Matter for AI/ML Interviews

Constraints are a **must-know** for AI/ML roles because:

1. **Data Quality**: Ensure datasets are accurate, complete, and consistent for ML models.
2. **Interview Essentials**: Questions often involve adding constraints to tables or explaining their impact.
3. **Error Prevention**: Block invalid data that could skew model performance.
4. **Database Design**: Enable robust schemas for efficient storage and querying.
5. **Universal Applicability**: Supported across MySQL, PostgreSQL, SQL Server, and more.

Mastering constraints will help you build trustworthy databases and shine in technical interviews! 🌟

---

## 🗺️ Constraints Roadmap

Our Constraints journey is structured into **sub-folders**, each focusing on a specific type of constraint. Click the links below to explore in-depth theory, coding examples, and interview exercises for each topic! 📚

| Sub-Folder | Description | Folder Link |
|------------|-------------|-------------|
| **Primary Key** | Uniquely identifies each row in a table. | [📂 01 Primary Key](./01%20Primary%20Key) |
| **Foreign Key** | Links tables to enforce referential integrity. | [📂 02 Foreign Key](./02%20Foreign%20Key) |
| **Unique** | Ensures column values are distinct across rows. | [📂 03 Unique](./03%20Unique) |
| **Not Null** | Requires columns to have non-NULL values. | [📂 04 Not Null](./04%20Not%20Null) |
| **Check** | Enforces custom conditions on column values. | [📂 05 Check](./05%20Check) |
| **Default** | Provides default values for columns when none is specified. | [📂 06 Default](./06%20Default) |

---

## 🚀 How to Use This Constraints Section

1. **Start with Primary Key**: Understand the foundation of unique row identification.
2. **Progress Logically**: Move to `Foreign Key`, `Unique`, and others to build comprehensive knowledge.
3. **Explore Folders**: Each sub-folder contains:
   - **README.md**: Detailed theory and best practices.
   - **Coding**: Hands-on SQL queries to practice.
   - **Interview_Exercises**: Curated problems to ace interviews.
4. **Practice Regularly**: Spend 1-2 hours per sub-folder, experimenting with constraint definitions.
5. **Focus on Interview Favorites**: `Primary Key`, `Foreign Key`, and `Not Null` are common in fresher interviews!

> **Pro Tip**: Test constraints with sample `INSERT` statements to see how they enforce rules—interviewers value hands-on understanding!

---

## 💡 Constraints in AI/ML: Real-World Use Cases

Constraints are vital in AI/ML workflows:

- **Data Integrity**: Use `PRIMARY KEY` to avoid duplicate records (e.g., `customer_id` in a `customers` table).
- **Relationships**: Apply `FOREIGN KEY` to link datasets (e.g., `orders.customer_id` references `customers.customer_id`).
- **Uniqueness**: Ensure unique identifiers with `UNIQUE` (e.g., `email` in a `users` table).
- **Completeness**: Enforce `NOT NULL` for required fields (e.g., `label` in a `training_data` table).
- **Validation**: Use `CHECK` to restrict values (e.g., `age > 0` in a `users` table).
- **Efficiency**: Set `DEFAULT` values to streamline data entry (e.g., `status = 'active'` in a `users` table).

Constraints ensure your data is clean and reliable for machine learning models! 🌍

---

## 📚 Tips for Success

- **Start Simple**: Practice `PRIMARY KEY` and `NOT NULL` before tackling `CHECK` or `FOREIGN KEY`.
- **Understand Impact**: Test how constraints affect DML operations like `INSERT` and `UPDATE`.
- **Use Sandbox**: Experiment in a test database to avoid breaking production schemas.
- **Practice Platforms**: Try LeetCode, HackerRank, or SQLZoo for constraint-related challenges.
- **Document Rules**: Add comments to DDL scripts to explain constraint purposes.

---

## 🤝 Contribute to This Journey

Have a clever constraint strategy or data integrity tip? Help make this resource even better! 🌟
1. Fork the repo.
2. Add content to the relevant sub-folder.
3. Submit a Pull Request with a clear description.

---

<div align="center">
  <p>Let’s enforce data quality with constraints and crush those SQL interviews! Happy designing! ✨</p>
</div>