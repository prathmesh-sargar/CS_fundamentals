

# 🧾 UNIT 1 – Quick Summary (Revision Sheet)

---

### 📌 OS = Resource Manager

* **Definition**: OS manages hardware + software resources, hides complexity, provides environment for execution.
* **Functions**:

  * Hardware Access
  * User ↔ Hardware Interface
  * Resource Management (CPU, Memory, File, I/O, Security)
  * Abstraction (hides complexity)
  * Protection + Isolation

---

### 📌 Why OS?

Without OS →
❌ Apps too complex (handle hardware directly)
❌ No memory protection
❌ One app can hog all resources

With OS →
✅ Resource sharing
✅ Protection
✅ Efficiency

---

### 📌 Goals of OS

* Max CPU utilization
* Less starvation
* Priority jobs execution

---

### 📌 Types of OS

1. **Single Process OS** → Only 1 process at a time.
2. **Batch OS** → Jobs grouped & executed in batches (CPU idle during I/O, starvation possible).
3. **Multiprogramming** → Multiple jobs in memory, CPU switches when one waits.
4. **Multitasking** → Time-sharing, responsive, multiple tasks run “simultaneously” on single CPU.
5. **Multiprocessing** → Multiple CPUs → parallel execution, more throughput, reliability.
6. **Distributed OS** → Many interconnected systems work as one.
7. **RTOS** → Real-time deadlines (Robots, Air traffic).

---

### 📌 Program vs Process vs Thread

* **Program** = Code on disk (not running).
* **Process** = Program under execution.
* **Thread** = Lightweight execution unit inside a process.

---

### 📌 Multitasking vs Multithreading

| Feature | Multitasking                     | Multithreading                           |
| ------- | -------------------------------- | ---------------------------------------- |
| Unit    | Multiple **processes**           | Multiple **threads** inside same process |
| Memory  | Each process has separate memory | Threads share same memory                |
| Cost    | Heavy (context switching)        | Light, faster                            |
| Example | Running Chrome + VS Code         | Multiple tabs inside Chrome              |

---

### 📌 Easy Mnemonics & Analogies

* **Batch OS = Train coaches** (all passengers loaded → then train moves).
* **Multiprogramming = Chef cooking** (while rice boils → cuts veggies).
* **Multitasking = Juggling** (time-sharing).
* **Multiprocessing = Multiple chefs** in kitchen.
* **RTOS = Fire alarm** (instant response).

---

### 🎯 Must-Remember for Placements

1. OS = Resource Manager + Abstraction Layer.
2. Multiprogramming vs Multitasking (most asked).
3. Real-time OS examples.
4. Threads vs Processes difference.

---
