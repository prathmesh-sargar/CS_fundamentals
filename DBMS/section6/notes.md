
# ⚙️ SECTION 6 — TRANSACTIONS, ACID PROPERTIES & RECOVERY

---

### 💡 1. What is a Transaction?

A **transaction** is a **unit of work** that performs one or more operations on a database — such as insert, update, or delete.

🧠 *In simple words:*

> “A transaction is a logical unit of work that must be executed completely or not at all.”

💬 *Example:*
When you transfer money:

* Step 1: Debit ₹1000 from Account A
* Step 2: Credit ₹1000 to Account B

Both must succeed together. If one fails → rollback the other.

---

### ⚙️ 2. Properties of a Transaction — **ACID**

| Property | Full Form   | Description                                                                 |
| -------- | ----------- | --------------------------------------------------------------------------- |
| **A**    | Atomicity   | All steps in a transaction are treated as one. If one fails → rollback all. |
| **C**    | Consistency | Database remains valid before and after transaction.                        |
| **I**    | Isolation   | Transactions don’t interfere with each other.                               |
| **D**    | Durability  | Once committed, changes stay permanently even after crash.                  |

---

### 🔍 Example of ACID:

**Example:** Money Transfer (A → B)

| Step | Operation             | Result                       |
| ---- | --------------------- | ---------------------------- |
| 1    | Debit ₹1000 from A    | Success                      |
| 2    | Credit ₹1000 to B     | Success                      |
| ✅    | Transaction committed | Both successful → DB updated |
| ❌    | If Step 2 fails       | Rollback Step 1              |

🧠 *Think:*

> ACID ensures reliability in every real-world DB system (like banks, e-commerce, etc.)

---

## 🧩 3. States of a Transaction

Transactions go through multiple states 👇

```
Active → Partially Committed → Committed
          ↓
       Failed → Aborted
```

| State                   | Meaning                                    |
| ----------------------- | ------------------------------------------ |
| **Active**              | Executing operations                       |
| **Partially Committed** | All operations done, but not committed yet |
| **Committed**           | All changes saved permanently              |
| **Failed**              | Error occurred, can’t continue             |
| **Aborted**             | Changes rolled back to previous state      |

💬 *In short:*

> Commit = Save permanently
> Abort = Undo everything

---

## 🔁 4. Transaction Control Commands (TCL)

These are used in SQL to manage transactions.

| Command             | Description                    |
| ------------------- | ------------------------------ |
| **COMMIT**          | Save changes permanently       |
| **ROLLBACK**        | Undo uncommitted changes       |
| **SAVEPOINT**       | Mark a point to rollback later |
| **SET TRANSACTION** | Start a transaction manually   |

🧠 *Example:*

```sql
BEGIN;
UPDATE accounts SET balance = balance - 1000 WHERE id = 1;
UPDATE accounts SET balance = balance + 1000 WHERE id = 2;
COMMIT;
```

If any step fails → `ROLLBACK;`

---

## 🔄 5. Concurrency Control

Concurrency = when **multiple users access the same DB simultaneously**.
DBMS must ensure that **transactions don’t interfere** and data stays consistent.

🧠 *Example:*
Two users booking the last movie ticket at the same time — only one should get it.

💬 *Goal:* Avoid problems like:

* Lost Updates
* Dirty Reads
* Uncommitted Data Access
* Inconsistent Reads

---

### ⚠️ 6. Concurrency Problems

| Problem               | Description                                                  | Example                                      |
| --------------------- | ------------------------------------------------------------ | -------------------------------------------- |
| **Lost Update**       | Two transactions update same data → one overwrites the other | Both users update same record; last one wins |
| **Dirty Read**        | One transaction reads uncommitted data of another            | T1 reads T2’s uncommitted balance            |
| **Unrepeatable Read** | Value changes between reads in same transaction              | T1 reads data, T2 updates it in between      |
| **Phantom Read**      | New rows appear/disappear during repeated reads              | T1 counts records, T2 inserts new ones       |

💬 *These issues are fixed by Isolation Levels.*

---

## 🧱 7. Isolation Levels

| Level                | Dirty Read | Non-repeatable Read | Phantom Read | Example DB          |
| -------------------- | ---------- | ------------------- | ------------ | ------------------- |
| **Read Uncommitted** | ❌          | ❌                   | ❌            | Fastest, least safe |
| **Read Committed**   | ✅          | ❌                   | ❌            | Default in Oracle   |
| **Repeatable Read**  | ✅          | ✅                   | ❌            | Default in MySQL    |
| **Serializable**     | ✅          | ✅                   | ✅            | Safest, but slowest |

✅ = Prevented ❌ = Not Prevented

💬 *In short:*

> Higher isolation → more accuracy, less performance.

---

### 🧩 Locking Mechanisms (to ensure Isolation)

To prevent simultaneous access conflicts, DBMS uses **locks**.

| Lock Type              | Description                                   | Example                  |
| ---------------------- | --------------------------------------------- | ------------------------ |
| **Shared Lock (S)**    | Allows reading, not writing                   | Multiple readers allowed |
| **Exclusive Lock (X)** | Allows writing, no one else can read/write    | Writer lock              |
| **Binary Lock**        | Either locked (1) or unlocked (0)             |                          |
| **Timestamp Ordering** | Order transactions by time to avoid conflicts |                          |

💬 *Think:* Locks = traffic signals for database operations 🚦

---

## 🔥 8. Schedule & Serializability

* **Schedule:** Order in which operations of multiple transactions execute.
* **Serializable Schedule:** Equivalent to executing transactions one after another — no interference.

🧠 *Types of Schedules:*

| Type                      | Meaning                                      |
| ------------------------- | -------------------------------------------- |
| **Serial Schedule**       | One transaction executes fully, then another |
| **Non-Serial Schedule**   | Interleaved execution                        |
| **Conflict-Serializable** | Order can be rearranged to make it serial    |

💬 *Goal:* Achieve same result as serial schedule → maintain consistency.

---

## 💾 9. Recovery in DBMS

When system crashes, DB must **recover to a consistent state**.
Recovery ensures **Atomicity** & **Durability**.

---

### 🧩 Types of Failures

| Type                    | Description                    |
| ----------------------- | ------------------------------ |
| **Transaction Failure** | Logical error or invalid input |
| **System Crash**        | Power failure, OS crash        |
| **Media Failure**       | Disk corruption                |
| **Application Error**   | Bug in code                    |

---

### 🧠 10. Recovery Techniques

Used by DBMS to restore consistent state after a crash.

| Method              | Description                                    |
| ------------------- | ---------------------------------------------- |
| **Rollback (Undo)** | Undo incomplete transactions                   |
| **Redo**            | Reapply committed transactions after crash     |
| **Checkpoint**      | Save DB state periodically for faster recovery |

---

### 🧩 Log-Based Recovery

* Every action is **recorded in a log file** before execution (Write-Ahead Logging).
* Log contains: Transaction ID, Operation, Old Value, New Value.
* On crash:

  * Undo → uncommitted transactions
  * Redo → committed transactions

🧠 *Example Log Entry:*

```
<T1, Write, AccountA, Old: 5000, New: 4000>
<T1, Commit>
```

💬 *In short:*

> Log = black box of your DB — helps rebuild data after crash.

---

### 🧩 Checkpoints

A **checkpoint** is a snapshot of DB at a particular time.
If crash occurs → restart from last checkpoint, not from the beginning.

🧠 *Think:*

> Like “save game” in databases 🎮

---

### ⚙️ 11. Shadow Paging (Another Recovery Method)

* Keeps **two copies** of pages:

  * **Shadow page** → original (stable copy)
  * **Current page** → working copy
* After commit → replace shadow with current.

💬 *Benefit:* No need for log — quick recovery.
❌ *Drawback:* Takes more storage.

---

## ⚡ Quick Recap:

```
Transaction = Logical unit of work
ACID = Atomicity, Consistency, Isolation, Durability
TCL = COMMIT, ROLLBACK, SAVEPOINT
Concurrency = Multi-user control
Locks = Prevent conflicts
Isolation Levels = Balance accuracy & speed
Recovery = Undo/Redo using logs & checkpoints
```

---

### 🎤 Interview-Ready Answers

**Q1:** What is a transaction?
🗣️ *Say:*

> “A transaction is a logical unit of work that performs multiple operations and must execute completely or not at all.”

---

**Q2:** Explain ACID properties.
🗣️ *Say:*

> “ACID stands for Atomicity, Consistency, Isolation, and Durability — ensuring reliable and consistent database transactions.”

---

**Q3:** What is the difference between COMMIT and ROLLBACK?
🗣️ *Say:*

> “COMMIT saves all changes permanently, while ROLLBACK undoes uncommitted changes.”

---

**Q4:** What are concurrency issues?
🗣️ *Say:*

> “When multiple transactions run simultaneously, they may cause conflicts like dirty reads, lost updates, or phantom reads.”

---

**Q5:** What are Isolation Levels in DBMS?
🗣️ *Say:*

> “Isolation Levels define how transactions interact. From least to most strict: Read Uncommitted, Read Committed, Repeatable Read, Serializable.”

---

**Q6:** What is the purpose of a Checkpoint?
🗣️ *Say:*

> “Checkpoint stores the database’s state periodically so that after a crash, recovery starts from that point instead of from the beginning.”

---

✅ **Section 6 Complete — Transactions, ACID, Concurrency & Recovery**
You now understand the heart of how DBMS maintains integrity even during failures 💪

---

