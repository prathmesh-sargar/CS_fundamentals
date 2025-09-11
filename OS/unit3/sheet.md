
# 🧾 UNIT 3 – Quick Summary (Process Management & Scheduling)

---

### 📌 Process Basics

* **Program** = Code on disk.
* **Process** = Program under execution (in memory).
* **Thread** = Lightweight execution unit inside process.

---

### 📌 PCB (Process Control Block)

* Data structure to track process info.
* Contains → PID, State, Program Counter, CPU registers, Memory info, Priority.
  👉 PCB = Aadhaar card of a process.

---

### 📌 Process States

1. New → Just created.
2. Ready → Waiting in queue for CPU.
3. Running → Currently executing.
4. Waiting → Blocked for I/O/event.
5. Terminated → Finished.

---

### 📌 Process Queues

* **Job Queue** → All jobs in secondary memory (LTS).
* **Ready Queue** → Ready jobs in RAM (STS).
* **Waiting Queue** → Waiting for I/O.
  👉 Dispatcher = Gives CPU to chosen process.

---

### 📌 Key Concepts

* **Swapping** → Move process between memory ↔ disk.
* **Context Switching** → Save current process state, load next → overhead.
* **Orphan Process** → Parent dead, child alive.
* **Zombie Process** → Child finished, parent didn’t read exit status → entry remains.

---

### 📌 Scheduling Basics

* **Non-preemptive** → Once CPU given, process keeps it.
* **Preemptive** → CPU can be taken away.

**Terms:**

* AT = Arrival Time
* BT = Burst Time
* CT = Completion Time
* TAT = CT – AT
* WT = TAT – BT
* Response Time = First CPU allocation – AT
* Throughput = Processes per unit time

---

### 📌 Scheduling Algorithms

1. **FCFS** → First come, first serve. (Non-preemptive)
   ⚠️ Convoy effect.
2. **SJF** → Shortest Job First.

   * Non-preemptive → starvation possible.
   * Preemptive (SRTF) → shorter jobs first.
3. **Priority Scheduling** → High priority first.
   ⚠️ Starvation → **Aging** fixes it.
4. **Round Robin (RR)** → Time Quantum (TQ). Fair, no starvation.
5. **MLQ** → Multi-level queues, fixed queues by process type.
   ⚠️ Starvation for lower queues.
6. **MLFQ** → Multi-level feedback queues. Processes can move between queues → reduces starvation.

---

### 🎯 Must-Remember for Placements

1. PCB = Aadhaar card of process.
2. Context Switching = Overhead but enables multitasking.
3. Convoy Effect → FCFS problem.
4. Round Robin best for **time-sharing**.
5. Aging prevents starvation in Priority Scheduling.
6. MLFQ is most flexible scheduling algorithm.

---

### 🧠 Analogies

* **FCFS = ATM queue**.
* **SJF = Small orders first at fast-food counter**.
* **RR = Cricket match, each player gets equal overs (time quantum)**.
* **MLQ = VIP queue vs normal queue**.
* **MLFQ = Dynamic queues (can move up if you wait too long)**.

---

✅ With this sheet, you can **revise Unit 3 in under 5 mins** and confidently answer placement questions.

---
