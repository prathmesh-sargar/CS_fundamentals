
# ⚙️ SECTION 4 — SQL (Structured Query Language)

---

### 💡 1. What is SQL?

* **SQL (Structured Query Language)** is the **standard language** used to store, manage, and retrieve data from relational databases.
* SQL allows you to **create, modify, query, and control** access to data.

🧠 *In short:*

> “SQL is how you talk to your database.”

---

### 🧰 2. Types of SQL Commands

| Type    | Full Form                    | Purpose                              | Examples                      |
| ------- | ---------------------------- | ------------------------------------ | ----------------------------- |
| **DDL** | Data Definition Language     | Define structure of database objects | CREATE, ALTER, DROP, TRUNCATE |
| **DML** | Data Manipulation Language   | Manipulate data inside tables        | INSERT, UPDATE, DELETE        |
| **DCL** | Data Control Language        | Control access to data               | GRANT, REVOKE                 |
| **TCL** | Transaction Control Language | Manage transactions                  | COMMIT, ROLLBACK, SAVEPOINT   |
| **DQL** | Data Query Language          | Query and fetch data                 | SELECT                        |

---

## 🧱 3. DDL (Data Definition Language)

Used to **define and modify structure** of tables.

### 🧩 CREATE

Creates a new table.

```sql
CREATE TABLE Students (
  Student_ID INT PRIMARY KEY,
  Name VARCHAR(50),
  Age INT,
  City VARCHAR(30)
);
```

---

### 🧩 ALTER

Modifies existing table structure.

```sql
ALTER TABLE Students ADD COLUMN Phone VARCHAR(15);
ALTER TABLE Students DROP COLUMN Age;
ALTER TABLE Students MODIFY COLUMN Name VARCHAR(100);
```

---

### 🧩 DROP

Deletes entire table **(structure + data)**.

```sql
DROP TABLE Students;
```

---

### 🧩 TRUNCATE

Removes all rows but **keeps the structure**.

```sql
TRUNCATE TABLE Students;
```

💬 *In short:* TRUNCATE = faster DELETE without WHERE.

---

### 🧩 RENAME

Renames a table.

```sql
RENAME TABLE Students TO Learners;
```

---

## 💾 4. DML (Data Manipulation Language)

Used for **adding, modifying, and removing** data from tables.

### 🧩 INSERT

```sql
INSERT INTO Students (Student_ID, Name, Age, City)
VALUES (101, 'Prathmesh', 21, 'Pune');
```

---

### 🧩 UPDATE

```sql
UPDATE Students
SET City = 'Mumbai'
WHERE Student_ID = 101;
```

---

### 🧩 DELETE

```sql
DELETE FROM Students
WHERE Age < 18;
```

💬 *Remember:* Without WHERE → deletes *all* rows!

---

## 🔍 5. DQL (Data Query Language)

Used to **query/fetch** data from tables.

### 🧩 SELECT

Basic:

```sql
SELECT * FROM Students;
```

Specific columns:

```sql
SELECT Name, City FROM Students;
```

With conditions:

```sql
SELECT * FROM Students WHERE City = 'Pune';
```

With sorting:

```sql
SELECT * FROM Students ORDER BY Age DESC;
```

---

## 🧩 6. Clauses in SQL

### 🧠 WHERE

Filters rows.

```sql
SELECT * FROM Students WHERE City = 'Pune';
```

---

### 🧠 ORDER BY

Sorts result.

```sql
SELECT * FROM Students ORDER BY Name ASC;
```

---

### 🧠 GROUP BY

Groups rows having same values.

```sql
SELECT City, COUNT(*) FROM Students GROUP BY City;
```

---

### 🧠 HAVING

Applies condition **after GROUP BY**.

```sql
SELECT City, COUNT(*) 
FROM Students
GROUP BY City
HAVING COUNT(*) > 2;
```

💬 *Tip:* WHERE → filters rows before grouping;
HAVING → filters groups after grouping.

---

### 🧠 DISTINCT

Removes duplicate values.

```sql
SELECT DISTINCT City FROM Students;
```

---

## 🧮 7. Aggregate Functions

Used for calculations across multiple rows.

| Function    | Description   | Example       |
| ----------- | ------------- | ------------- |
| **COUNT()** | Counts rows   | `COUNT(*)`    |
| **SUM()**   | Adds values   | `SUM(Salary)` |
| **AVG()**   | Average value | `AVG(Marks)`  |
| **MIN()**   | Minimum value | `MIN(Age)`    |
| **MAX()**   | Maximum value | `MAX(Salary)` |

🧠 *Example:*

```sql
SELECT AVG(Age) AS Avg_Age FROM Students;
```

---

## 🧩 8. DCL (Data Control Language)

Used to **control access** to database.

### GRANT

Gives permission.

```sql
GRANT SELECT, UPDATE ON Students TO user1;
```

### REVOKE

Removes permission.

```sql
REVOKE UPDATE ON Students FROM user1;
```

💬 *In short:*

> DBA uses DCL to secure access and prevent unauthorized actions.

---

## 🔁 9. TCL (Transaction Control Language)

Used to manage **transactions** — group of SQL statements executed as one unit.

### 🧩 COMMIT

Saves changes permanently.

```sql
COMMIT;
```

---

### 🧩 ROLLBACK

Undo changes if error occurs.

```sql
ROLLBACK;
```

---

### 🧩 SAVEPOINT

Marks a checkpoint in a transaction.

```sql
SAVEPOINT SP1;
ROLLBACK TO SP1;
```

💬 *Example Flow:*

```sql
BEGIN;
UPDATE Students SET Age = 25 WHERE ID=101;
SAVEPOINT A;
DELETE FROM Students WHERE Age < 18;
ROLLBACK TO A;
COMMIT;
```

🧠 *Tip:* Transactions maintain **ACID properties** (Atomicity, Consistency, Isolation, Durability).

---

## 🤝 10. JOINS (Very Important)

Joins combine rows from two or more tables based on a related column.

### 🧩 INNER JOIN

Returns only **matching rows**.

```sql
SELECT s.Name, c.Course_Name
FROM Students s
INNER JOIN Courses c
ON s.Course_ID = c.Course_ID;
```

---

### 🧩 LEFT JOIN

Returns **all rows from left table** + matching from right.

```sql
SELECT s.Name, c.Course_Name
FROM Students s
LEFT JOIN Courses c
ON s.Course_ID = c.Course_ID;
```

---

### 🧩 RIGHT JOIN

Returns **all rows from right table** + matching from left.

```sql
SELECT s.Name, c.Course_Name
FROM Students s
RIGHT JOIN Courses c
ON s.Course_ID = c.Course_ID;
```

---

### 🧩 FULL OUTER JOIN

Returns **all rows** from both tables (matched + unmatched).

```sql
SELECT s.Name, c.Course_Name
FROM Students s
FULL OUTER JOIN Courses c
ON s.Course_ID = c.Course_ID;
```

---

### 🧩 CROSS JOIN

Creates a **cartesian product** of both tables.

```sql
SELECT * FROM Students CROSS JOIN Courses;
```

💬 *Tip:* Avoid unless needed — can explode data size.

---

## 🔁 11. Subqueries (Nested Queries)

A **query inside another query**.

🧠 *Example:*

```sql
SELECT Name, Age
FROM Students
WHERE Age > (SELECT AVG(Age) FROM Students);
```

→ Inner query gives average age, outer query lists students above that age.

---

### Types of Subqueries:

| Type           | Description                  | Example            |
| -------------- | ---------------------------- | ------------------ |
| **Single-row** | Returns one value            | `=` `<` `>`        |
| **Multi-row**  | Returns multiple values      | `IN`, `ANY`, `ALL` |
| **Correlated** | Inner query depends on outer | Usually slower     |

🧠 *Example (multi-row):*

```sql
SELECT Name FROM Students 
WHERE Course_ID IN (SELECT Course_ID FROM Courses WHERE Duration > 6);
```

---

## ⚙️ 12. Set Operations

Used to combine results from multiple queries.

| Operator           | Meaning                               | Example                                        |
| ------------------ | ------------------------------------- | ---------------------------------------------- |
| **UNION**          | Combine results, removes duplicates   | `SELECT City FROM A UNION SELECT City FROM B;` |
| **UNION ALL**      | Combines all (keeps duplicates)       | `SELECT ... UNION ALL SELECT ...;`             |
| **INTERSECT**      | Common results                        | `SELECT ... INTERSECT SELECT ...;`             |
| **MINUS / EXCEPT** | Returns rows from first not in second | `SELECT ... MINUS SELECT ...;`                 |

---

## 🧠 13. Views

A **virtual table** based on the result of a query.

```sql
CREATE VIEW Pune_Students AS
SELECT Name, City FROM Students WHERE City = 'Pune';
```

💬 *In short:* View = saved SQL query used as a table.

---

## 🔥 14. Index

* Improves speed of data retrieval.
* Works like an index in a book.

```sql
CREATE INDEX idx_name ON Students(Name);
```

💬 *Tip:* Speeds up SELECT but slows down INSERT/UPDATE/DELETE.

---

## ⚡ Quick Revision Recap

```
DDL → Structure  (CREATE, ALTER, DROP)
DML → Data       (INSERT, UPDATE, DELETE)
DQL → Query      (SELECT)
DCL → Control    (GRANT, REVOKE)
TCL → Transaction (COMMIT, ROLLBACK)
Joins → Combine tables
Subqueries → Query inside query
```

---

## 🎤 Interview-Ready Answers

**Q1:** Difference between DELETE, TRUNCATE, DROP
🗣️ *Say:*

> “DELETE removes rows one by one with rollback option, TRUNCATE removes all rows but keeps structure, and DROP removes table structure completely.”

**Q2:** Difference between WHERE and HAVING
🗣️ *Say:*

> “WHERE filters rows before grouping, HAVING filters after GROUP BY.”

**Q3:** Explain different types of JOINs
🗣️ *Say:*

> “INNER returns matches, LEFT keeps all from left, RIGHT keeps all from right, and FULL returns everything from both.”

**Q4:** What are transactions and why are they important?
🗣️ *Say:*

> “A transaction is a unit of work that ensures data consistency. It follows ACID properties — Atomicity, Consistency, Isolation, and Durability.”

**Q5:** What is a View and why use it?
🗣️ *Say:*

> “A view is a virtual table based on a query. It simplifies complex queries and helps restrict data access for security.”

---

✅ **Section 4 Complete — SQL (DDL, DML, DCL, TCL, Joins, Subqueries, Clauses, Functions)**
You now have the full toolkit for both **SQL queries and theory-based questions** 💪

---
