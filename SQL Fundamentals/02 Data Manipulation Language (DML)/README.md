# ✍️ Data Manipulation Language (DML) - Shaping Your Data

<div align="center">
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL Logo" />
</div>

<p align="center">Master DML to insert, update, and delete data with precision for AI/ML interviews! 🚀</p>

---

## 🌟 What is DML?

**Data Manipulation Language (DML)** is the subset of SQL used to **modify data** within a database. Unlike DQL (which retrieves data), DML focuses on adding (`INSERT`), modifying (`UPDATE`), and removing (`DELETE`) records. These operations are critical for maintaining and preparing datasets, ensuring data integrity, and supporting dynamic AI/ML workflows.

In AI/ML, DML is essential for tasks like populating training datasets, updating model metadata, or cleaning outdated records. For freshers, DML is a **core interview topic**, often tested in coding challenges and scenario-based questions about data management! 💡

---

## 🎯 Why DML Matters for AI/ML Interviews

DML is a **must-have skill** for AI/ML roles because:

1. **Data Preparation**: DML enables you to build and refine datasets for model training.
2. **Interview Essentials**: Questions frequently involve writing `INSERT`, `UPDATE`, or `DELETE` statements to manipulate data.
3. **Data Integrity**: Ensures accurate updates and deletions, critical for reliable ML pipelines.
4. **Real-World Impact**: Supports ETL processes, data versioning, and database maintenance.
5. **Universal Applicability**: Works across MySQL, PostgreSQL, SQL Server, and more.

Mastering DML will empower you to handle data manipulation tasks confidently and ace technical interviews! 🌟

---

## 🗺️ DML Roadmap

Our DML journey is structured into **leaf nodes**, each focusing on a key manipulation operation. Click the links below to explore in-depth theory, coding examples, and interview exercises for each topic! 📚

| Leaf Node | Description | Folder Link |
|-----------|-------------|-------------|
| **INSERT** | Add new records to a table, populating databases with fresh data. | [📂 01 INSERT](./01%20INSERT) |
| **UPDATE** | Modify existing records based on conditions, ensuring data accuracy. | [📂 02 UPDATE](./02%20UPDATE) |
| **DELETE** | Remove records from a table, cleaning up unwanted data. | [📂 03 DELETE](./03%20DELETE) |

---

## 🚀 How to Use This DML Section

1. **Start with INSERT**: Learn to add data, the foundation of populating databases.
2. **Progress to UPDATE and DELETE**: Master modifying and removing data for full control.
3. **Explore Each Folder**: Every leaf node folder contains:
   - **README.md**: Detailed theory and best practices.
   - **Coding**: Hands-on SQL queries to practice.
   - **Interview_Exercises**: Curated problems to ace interviews.
4. **Practice Regularly**: Spend 1-2 hours per leaf node, experimenting with data changes.
5. **Focus on Interview Favorites**: `INSERT` and `UPDATE` are common in fresher interviews, so prioritize them!

> **Pro Tip**: Always test DML statements with a `SELECT` query first to preview affected rows—interviewers value caution and accuracy!

---

## 💡 DML in AI/ML: Real-World Use Cases

DML powers critical AI/ML workflows:

- **Dataset Creation**: Use `INSERT` to populate tables with training data (e.g., `INSERT INTO training_data SELECT * FROM raw_data WHERE valid = 1`).
- **Data Correction**: Apply `UPDATE` to fix errors (e.g., `UPDATE customers SET email = 'corrected@domain.com' WHERE email IS NULL`).
- **Data Cleanup**: Leverage `DELETE` to remove outliers (e.g., `DELETE FROM predictions WHERE score < 0.1`).
- **Model Metadata**: Update model performance metrics (e.g., `UPDATE models SET accuracy = 0.95 WHERE model_id = 1`).
- **ETL Pipelines**: Combine DML operations to transform and load data for analysis.

DML ensures your data is ready for machine learning models and production systems! 🌍

---

## 📚 Tips for Success

- **Start Simple**: Practice basic `INSERT` statements before tackling complex `UPDATE` or `DELETE`.
- **Use Transactions**: Wrap DML in transactions (`BEGIN`/`COMMIT`) to ensure safe changes.
- **Test Changes**: Preview modifications with `SELECT` to avoid mistakes.
- **Practice Platforms**: Try LeetCode, HackerRank, or SQLZoo for DML challenges.
- **Understand Constraints**: Learn how primary keys, foreign keys, and triggers affect DML.

---

## 🤝 Contribute to This Journey

Have a clever DML trick or data manipulation scenario? Help make this resource even better! 🌟
1. Fork the repo.
2. Add content to the relevant leaf node folder.
3. Submit a Pull Request with a clear description.

---

<div align="center">
  <p>Let’s shape data with DML and crush those SQL interviews! Happy manipulating! ✨</p>
</div>