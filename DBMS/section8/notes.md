
# ⚙️ SECTION 8 — TYPES OF DATABASES

---

### 💡 1. Why Different Types of Databases Exist?

Every system doesn’t have the same data needs.

* Banks need **structured**, consistent data.
* Instagram needs **scalable**, unstructured, flexible data.

👉 That’s why we have **different DB types**, each built for a specific goal — **structure, speed, scalability, or flexibility.**

---

## 🧩 2. Main Types of Databases

| Type                                  | Structure                        | Example Systems           | Use Case                    |
| ------------------------------------- | -------------------------------- | ------------------------- | --------------------------- |
| **Relational Database (RDBMS)**       | Tables with rows & columns       | MySQL, PostgreSQL, Oracle | Banking, E-commerce         |
| **Hierarchical Database**             | Tree-like parent-child           | IBM IMS, Windows Registry | File systems, Legacy apps   |
| **Network Database**                  | Graph-like with multiple parents | CODASYL, IDMS             | Telecom, ERP                |
| **Object-Oriented Database (OODBMS)** | Stores objects (with methods)    | ObjectDB, db4o            | CAD/CAM, Multimedia         |
| **NoSQL Database**                    | Schema-less, non-relational      | MongoDB, Cassandra, Redis | Social media, IoT, Big Data |
| **Distributed Database**              | Data stored on multiple servers  | Google Spanner, Cassandra | Scalable cloud apps         |
| **Graph Database**                    | Node-edge relationships          | Neo4j, Amazon Neptune     | Recommendation engines      |
| **Time-Series Database**              | Optimized for time-based data    | InfluxDB, TimescaleDB     | IoT, stock data, sensors    |

---

## 🧱 3. Relational Database (RDBMS)

* Stores data in **tables (relations)**.
* Uses **SQL** for managing and querying data.
* Ensures **ACID properties** (Atomicity, Consistency, Isolation, Durability).

🧠 *Example:*

```sql
CREATE TABLE Students (
  StudentID INT PRIMARY KEY,
  Name VARCHAR(50),
  Marks INT
);
```

💬 *In short:*

> “Structured data + strong consistency = RDBMS.”

✅ **Pros:** Reliable, consistent, easy to query
❌ **Cons:** Not flexible for unstructured data, scaling is hard

🧩 *Popular RDBMS:* MySQL, Oracle, PostgreSQL, MS SQL Server

---

## 🌳 4. Hierarchical Database

* Data stored in **tree structure (parent → child)**.
* Each child has **only one parent**, but a parent can have many children.

🧠 *Example:*

```
College
 ├── Department
 │     ├── Faculty
 │     └── Courses
 └── Library
```

💬 *Used in:* File systems, old mainframe systems.

✅ **Pros:** Fast access if structure fits
❌ **Cons:** Rigid — difficult to modify relationships

---

## 🔗 5. Network Database

* Extends the hierarchical model by allowing **many-to-many relationships**.
* Each record can have **multiple parent and child records.**

🧠 *Example:*

```
Student ↔ Course ↔ Instructor
```

💬 *In short:*

> “Flexible connections but complex pointers.”

✅ **Pros:** Handles complex relationships
❌ **Cons:** Hard to maintain and navigate

🧩 *Used in:* Telecom, manufacturing, ERP systems

---

## 🧠 6. Object-Oriented Database (OODBMS)

* Stores data as **objects** (same as in Object-Oriented Programming).
* Objects contain both **data (attributes)** and **methods (functions)**.

🧠 *Example (Java-style):*

```java
class Student {
  int id;
  String name;
  void display() { ... }
}
```

💬 *In short:*

> “Combines database + object-oriented logic.”

✅ **Pros:** Works seamlessly with OOP languages
❌ **Cons:** Not widely supported

🧩 *Used in:* CAD/CAM, AI systems, multimedia apps

---

## ⚡ 7. NoSQL Database (Non-Relational)

* Stands for **“Not Only SQL.”**
* Designed for **large-scale**, **unstructured**, or **semi-structured** data.
* Schema-less → data can have **different formats**.

💬 *In short:*

> “NoSQL = Flexibility, scalability, and speed for big modern data.”

---

### 🧩 Types of NoSQL Databases

| Type                | Structure                   | Example          | Use Case                         |
| ------------------- | --------------------------- | ---------------- | -------------------------------- |
| **Document-based**  | JSON-like documents         | MongoDB, CouchDB | Dynamic web data                 |
| **Key-Value store** | Key-value pairs             | Redis, DynamoDB  | Caching, sessions                |
| **Column-family**   | Columns grouped by families | Cassandra, HBase | Analytics, logs                  |
| **Graph-based**     | Nodes & relationships       | Neo4j            | Social networks, recommendations |

🧠 *Example (Document in MongoDB):*

```json
{
  "_id": 1,
  "name": "Prathmesh",
  "skills": ["React", "Node", "MongoDB"]
}
```

✅ **Pros:** Highly scalable, flexible schema, fast
❌ **Cons:** Weaker consistency (usually eventual)

💬 *Best For:*
Big Data, IoT, Social Media, Real-time analytics

---

## ☁️ 8. Distributed Database

* Data is stored across **multiple locations or servers**, connected via network.
* Appears as a **single database** to the user.

🧠 *Example:* Google Spanner, Amazon Aurora, Cassandra

💬 *Used in:* Cloud apps, global-scale systems

✅ **Pros:** High availability, fault tolerance
❌ **Cons:** Complex synchronization

🧠 *In short:*

> “One DB across many machines = Distributed DB.”

---

## 🧩 9. Graph Database

* Designed for **data connected by relationships**.
* Uses **nodes (entities)** and **edges (connections)**.

🧠 *Example:*

```
(Prathmesh) —[FRIEND_OF]—> (Riya)
```

💬 *In short:*

> “Perfect for data where relationships matter more than rows.”

✅ **Pros:** Excellent for queries like recommendations or connections
❌ **Cons:** Slower for heavy computations

🧩 *Used in:*

* Social media (friends, followers)
* Recommendation systems (Netflix, Spotify)
* Fraud detection

---

## ⏱️ 10. Time-Series Database

* Optimized for **data that changes over time** (with timestamps).
* Handles massive sequential data streams.

🧠 *Example:*
Stock prices, IoT sensors, server logs.

🧩 *Used in:* InfluxDB, TimescaleDB, Prometheus.

💬 *In short:*

> “Best for tracking data over time — fast inserts, time queries.”

---

## ⚙️ 11. Centralized vs Distributed vs Federated DB

| Type            | Description                         | Example                 |
| --------------- | ----------------------------------- | ----------------------- |
| **Centralized** | All data stored in one location     | Local DB server         |
| **Distributed** | Data spread across multiple servers | Google Spanner          |
| **Federated**   | Integrates multiple independent DBs | Banking network systems |

---

## ⚡ 12. SQL vs NoSQL — The Classic Comparison

| Feature        | SQL (RDBMS)           | NoSQL                                                        |
| -------------- | --------------------- | ------------------------------------------------------------ |
| Data Structure | Tables (rows/columns) | Documents, Key-Value, Graph                                  |
| Schema         | Fixed                 | Flexible                                                     |
| Query Language | SQL                   | No fixed language (JSON, APIs)                               |
| Scalability    | Vertical (add power)  | Horizontal (add servers)                                     |
| Transactions   | ACID                  | BASE (Basically Available, Soft state, Eventual consistency) |
| Ideal For      | Structured data       | Unstructured / dynamic data                                  |
| Examples       | MySQL, PostgreSQL     | MongoDB, Cassandra, Firebase                                 |

🧠 *In short:*

> “SQL = Structured & consistent.”
> “NoSQL = Flexible & scalable.”

---

## 🧮 13. BASE Properties (NoSQL)

While RDBMS uses ACID, NoSQL uses **BASE** for eventual consistency.

| Property                 | Meaning                                          |
| ------------------------ | ------------------------------------------------ |
| **Basically Available**  | Data always available (even if stale)            |
| **Soft State**           | State may change over time without input         |
| **Eventual Consistency** | Data becomes consistent eventually after updates |

💬 *Think:* BASE trades consistency for scalability and speed.

---

### ⚡ Quick Recap:

```
RDBMS → Structured, Table-based
Hierarchical → Tree structure
Network → Graph with multiple parents
Object-Oriented → Data as objects
NoSQL → Schema-less, scalable
Distributed → Multi-server storage
Graph → Node-edge relationships
Time-Series → Time-stamped data
```

---

### 🎤 Interview-Ready Answers

**Q1:** What are the main types of databases?
🗣️ *Say:*

> “The main types are Relational, Hierarchical, Network, Object-Oriented, and NoSQL databases — each designed for specific data storage and performance needs.”

---

**Q2:** Difference between SQL and NoSQL databases?
🗣️ *Say:*

> “SQL stores structured data in tables with fixed schema and supports ACID transactions, while NoSQL stores unstructured or semi-structured data in flexible formats like JSON and focuses on scalability.”

---

**Q3:** When would you choose NoSQL over SQL?
🗣️ *Say:*

> “When dealing with large, dynamic, or unstructured data — like social media, IoT, or real-time analytics — NoSQL is better due to flexibility and horizontal scalability.”

---

**Q4:** What is a graph database used for?
🗣️ *Say:*

> “Graph databases are used to represent data through nodes and relationships — perfect for social networks, recommendations, and relationship-heavy data.”

---

**Q5:** What is the difference between centralized and distributed databases?
🗣️ *Say:*

> “Centralized DB stores data in one place; Distributed DB spreads it across multiple servers to improve scalability and reliability.”

---

✅ **Section 8 Complete — Types of Databases (SQL, NoSQL, Graph, Hierarchical, etc.)**
You’ve now mastered all DB architectures — from classic RDBMS to modern NoSQL and beyond 💪

---

