
# ⚙️ SECTION 7 — INDEXING IN DBMS

---

### 💡 1. What is Indexing?

**Indexing** is a **data structure technique** used to **speed up data retrieval** from a database.

🧠 *In simple terms:*

> “An index in a database works like an index in a book — instead of scanning every page, you directly jump to the location.”

💬 *Without index:* Full table scan (slow).
💬 *With index:* Fast lookup using tree or hash structure.

---

### ⚙️ 2. Why Indexing is Needed

| Without Index                        | With Index                    |
| ------------------------------------ | ----------------------------- |
| Sequential scan of entire table      | Jumps directly to target data |
| Slow for large datasets              | Very fast lookup              |
| Consumes more CPU                    | Optimized search              |
| Example: 10M rows = very slow search | Uses B+ Tree or Hash index    |

✅ **Use index for:**

* WHERE clause conditions
* JOIN operations
* Sorting (ORDER BY)
* Searching/filtering large data

❌ **Avoid index for:**

* Columns with too many duplicates (like gender)
* Tables with heavy INSERT/UPDATE (index maintenance overhead)

---

### 🧩 3. How Indexing Works

An index is like a **pointer** that stores a mapping of key values → location of actual data.

🧠 *Example:*

```
Student Table
----------------
ID | Name     | City
1  | Prathmesh | Pune
2  | Riya      | Mumbai
3  | Aarav     | Delhi
```

➡ Create index on `Name`

**Index Structure:**

```
Name     → Record Address
Aarav    → 3
Prathmesh → 1
Riya     → 2
```

💬 *So when DBMS searches Name='Riya', it goes to index first → gets record 2 instantly.*

---

### ⚙️ 4. Types of Indexes in DBMS

| Type                    | Description                               | Example / Notes                   |
| ----------------------- | ----------------------------------------- | --------------------------------- |
| **Primary Index**       | Created automatically on Primary Key      | Unique, sorted                    |
| **Secondary Index**     | Created manually on non-key columns       | For faster lookups                |
| **Clustered Index**     | Alters physical order of data             | Only **one** per table            |
| **Non-Clustered Index** | Stores index separately from table        | Many per table allowed            |
| **Composite Index**     | Created on multiple columns               | `(col1, col2)`                    |
| **Unique Index**        | Ensures all values are unique             | Auto created on PK/Unique columns |
| **Dense Index**         | Every search key value appears in index   | Fast but large                    |
| **Sparse Index**        | Only some entries stored (on block level) | Smaller, slower                   |

---

### 📦 5. Primary vs Secondary Index

| Feature  | Primary Index               | Secondary Index            |
| -------- | --------------------------- | -------------------------- |
| Based On | Primary Key                 | Non-key attribute          |
| Unique   | Yes                         | May not be unique          |
| Sorting  | Data stored in sorted order | Data not physically sorted |
| Count    | One per table               | Multiple possible          |

💬 *Example:*
→ In `Employee` table, primary index on `Emp_ID`, secondary index on `Dept`.

---

### 🧱 6. Clustered vs Non-Clustered Index

| Feature      | Clustered Index                 | Non-Clustered Index             |
| ------------ | ------------------------------- | ------------------------------- |
| Data Storage | Data rows are physically sorted | Separate structure from table   |
| Count        | One per table                   | Many allowed                    |
| Access Speed | Faster (no extra lookup)        | Slightly slower (extra pointer) |
| Example      | Primary Key                     | Secondary Key                   |

🧠 *Analogy:*
Clustered = dictionary pages sorted alphabetically.
Non-clustered = separate bookmark list pointing to pages.

---

### 🌲 7. B-Tree Index (Balanced Tree)

* Most **commonly used index** in DBMS.
* Self-balanced tree data structure used for **range and equality searches**.

🧩 **Features:**

* Each node contains keys & pointers.
* Root node → internal nodes → leaf nodes.
* Keys are stored in sorted order.
* Search, insert, delete = O(log n).

🧠 *Example Flow:*

```
Search Key = 25
Root → compares → left/right node → leaf node → record pointer.
```

💬 *Used in:* MySQL, Oracle, PostgreSQL (default index type).

---

### 🌲 8. B+ Tree Index

An improved version of B-Tree used by **almost all modern DBMS**.

🧩 **Features:**

* All data records stored only in **leaf nodes**.
* Leaf nodes are linked (for range queries).
* Faster for sequential and range-based queries.

🧠 *In short:*

> “B+ Tree = B-Tree + Linked Leaf Nodes (for faster traversal).”

---

### 🧮 9. Hash Indexing

Used for **exact match lookups** (not range-based).

🧩 **Working:**

* Hash function maps key → bucket address.
* Ideal for equality searches like `WHERE id = 101`.

💬 *Example:*

```
hash(101) = 3 → Bucket 3 → Record found
```

✅ Super fast for: `=` conditions
❌ Not suitable for: `>`, `<`, `BETWEEN`, `LIKE`

🧠 *In short:*

> “Hash Index = Key → Hash Function → Bucket (instant lookup).”

---

### ⚙️ 10. Dense vs Sparse Index

| Feature | Dense Index            | Sparse Index        |
| ------- | ---------------------- | ------------------- |
| Entries | Every record has entry | One entry per block |
| Speed   | Faster                 | Slower              |
| Space   | More                   | Less                |
| Use     | Small tables           | Large tables        |

🧠 *Example:*
Dense = index for every page of book.
Sparse = index for each chapter.

---

### 🧩 11. Multilevel Index

* Instead of one huge index → create **index of indexes**.
* Makes lookup even faster for large databases.

🧠 *Example:*

```
Level 1: Index of Index Pages
Level 2: Actual Index Entries
Level 3: Data Blocks
```

💬 *Used for:* Very large datasets (millions of rows).

---

### 🧠 12. Composite Index

* Created on **two or more columns** together.

```sql
CREATE INDEX idx_student ON Students(Name, City);
```

💬 *Best for queries using both columns in WHERE clause.*

🧩 *Example:*
Query → `WHERE Name='Riya' AND City='Pune'`
→ DB uses composite index efficiently.

---

### 🧾 13. Index Creation & Deletion (SQL Commands)

```sql
-- Create Index
CREATE INDEX idx_name ON Students(Name);

-- Create Unique Index
CREATE UNIQUE INDEX idx_email ON Students(Email);

-- Drop Index
DROP INDEX idx_name;
```

💬 *Note:* In MySQL → use `ALTER TABLE DROP INDEX`.

---

### ⚡ 14. Advantages of Indexing

✅ Faster data retrieval
✅ Better performance in SELECT, JOIN, ORDER BY
✅ Efficient searching and sorting
✅ Optimizes WHERE clause queries

---

### ⚠️ 15. Disadvantages of Indexing

❌ Slows down INSERT, UPDATE, DELETE (index must be updated)
❌ Takes extra disk space
❌ Needs regular maintenance (rebuild/reorganize)

🧠 *Rule:*

> Use indexes on frequently searched columns, not on every column.

---

### ⚙️ 16. Index vs Primary Key

| Feature    | Index          | Primary Key               |
| ---------- | -------------- | ------------------------- |
| Purpose    | Improve speed  | Uniquely identify records |
| Unique     | Optional       | Always unique             |
| Nulls      | Can have nulls | Cannot                    |
| Count      | Many per table | One only                  |
| Created On | Any column     | Specific column only      |

---

### ⚡ Quick Recap

```
Index = Shortcut for fast data retrieval
Primary Index → Auto on PK
Secondary Index → On non-key
Clustered Index → Reorders data physically
Non-Clustered → Separate structure
B+ Tree → Default in RDBMS
Hash Index → Exact match
Dense vs Sparse → Speed vs Space
```

---

### 🎤 Interview-Ready Answers

**Q1:** What is an index in DBMS?
🗣️ *Say:*

> “An index is a data structure that improves the speed of data retrieval by creating pointers to data rows — just like an index in a book.”

---

**Q2:** Difference between Clustered and Non-Clustered Index?
🗣️ *Say:*

> “Clustered Index reorders the actual data rows in the table and there can be only one per table, while Non-Clustered Index creates a separate structure without changing physical order.”

---

**Q3:** What’s the difference between B-Tree and B+ Tree?
🗣️ *Say:*

> “In B-Tree, data is stored in internal and leaf nodes. In B+ Tree, data is stored only in leaf nodes which are linked — making range queries faster.”

---

**Q4:** What are Dense and Sparse Indexes?
🗣️ *Say:*

> “In Dense Index, every record has an index entry; in Sparse Index, only some records (like one per block) are indexed. Dense = faster, Sparse = more space efficient.”

---

**Q5:** When should we avoid using an index?
🗣️ *Say:*

> “Avoid indexing columns with high duplicate values or tables with frequent insert/update operations since maintaining the index will slow down performance.”

---

✅ **Section 7 Complete — Indexing in DBMS (Concept, Types, Trees, Advantages & SQL Commands)**
You’re now ready to explain database performance optimization like a pro dev 🧠💪

---
