# 🖥️ UNIT 3 – PROCESS MANAGEMENT & SCHEDULING

---

## 1️⃣ What is a Process?

* **Program** = Compiled code stored on disk (not running).
* **Process** = Program **under execution** (running in memory).

👉 Example: Chrome.exe (program on disk) → When you double click, it becomes a **process** in RAM.

---

## 2️⃣ How OS Creates a Process?

Steps:

1. Load program + static data into memory.
2. Allocate stack + heap.
3. Handle I/O tasks.
4. OS hands control to `main()` function.

---

## 3️⃣ Process Control Block (PCB)

* Data structure used by OS to track process info.
* Stored in **Process Table**.

📌 PCB contains:

* Process ID (PID)
* Process state (Ready, Running, Waiting…)
* Program Counter
* CPU registers
* Scheduling info (priority, queue info)
* Memory info

👉 Analogy: PCB = Aadhaar card of a process.

---

## 4️⃣ Process States

* **New** → Just created, not ready yet.
* **Ready** → Waiting in memory for CPU.
* **Running** → Currently executing.
* **Waiting** → Blocked for I/O or event.
* **Terminated** → Finished execution, PCB removed.

👉 Think of it like:

* **New** = Student just admitted.
* **Ready** = Student waiting for exam.
* **Running** = Student writing exam.
* **Waiting** = Student waiting for question paper.
* **Terminated** = Exam over.

---

## 5️⃣ Process Queues

* **Job Queue** → All jobs in secondary memory. (Managed by Long-Term Scheduler - LTS).
* **Ready Queue** → Jobs in main memory waiting for CPU. (Managed by Short-Term Scheduler - STS).
* **Waiting Queue** → Jobs waiting for I/O.

👉 **Dispatcher** = Person who hands over CPU to a process chosen by scheduler.

---

## 6️⃣ Swapping

* Moving process **out of memory** → Disk (swap out).
* Later brought back → Memory (swap in).
* Controlled by Medium-Term Scheduler (MTS).
  👉 Used when memory is full → makes space.

---

## 7️⃣ Context Switching

* Switching CPU from one process to another.
* Save current process state → PCB.
* Load new process state from PCB.
  ⚠️ Overhead (no useful work done while switching).

👉 Example: Teacher pausing one student’s viva → moving to another.

---

## 8️⃣ Special Processes

* **Orphan Process** → Parent dies, child still alive.
* **Zombie Process** → Child finished but parent didn’t read exit status → entry remains in process table.

---

## 9️⃣ Scheduling Basics

👉 Scheduling = Deciding **which process gets CPU** next.

* **Non-Preemptive**: Once CPU given, process keeps it until done/waits. (Ex: FCFS, SJF-non-preemptive).
* **Preemptive**: CPU can be taken away (Ex: Round Robin, Priority-preemptive).

### Goals of CPU Scheduling:

* Max CPU utilization
* Min Turnaround Time (TAT)
* Min Waiting Time (WT)
* Min Response Time
* Max Throughput

📌 Terms:

* **Arrival Time (AT)** → When process comes.
* **Burst Time (BT)** → CPU execution time required.
* **Completion Time (CT)** → When process finishes.
* **Turnaround Time (TAT)** → CT – AT.
* **Waiting Time (WT)** → TAT – BT.
* **Response Time** → Time until process gets CPU first time.
* **Throughput** → Processes completed per unit time.

---

## 🔑 Scheduling Algorithms

### 1. **FCFS (First Come, First Serve)**

* Queue based. First process to arrive → executed first.
* **Non-preemptive**.
  ⚠️ **Convoy Effect** → One long job delays others.

---

### 2. **SJF (Shortest Job First)**

* Job with shortest burst time first.
* **Non-preemptive** version → May cause starvation.
* **Preemptive SJF (SRTF)** → Runs shortest remaining time job first → reduces starvation.

---

### 3. **Priority Scheduling**

* Each process has priority.
* Highest priority runs first.
* **Non-preemptive + Preemptive** possible.
  ⚠️ Starvation possible → **Solution = Aging** (priority increases with wait time).

---

### 4. **Round Robin (RR)**

* Like FCFS but **preemptive**.
* Each process gets **time quantum (TQ)**.
* If not finished in TQ → put back in ready queue.
  ✅ Fairness, no starvation.
  ⚠️ Too small TQ = too many context switches (overhead).

---

### 5. **MLQ (Multi-Level Queue)**

* Multiple queues by process type (System, Interactive, Batch).
* Each queue → own scheduling algo.
  ⚠️ Starvation for lower priority queues.

---

### 6. **MLFQ (Multi-Level Feedback Queue)**

* Processes can move between queues.
* I/O bound & short jobs → higher priority.
* Long CPU jobs → lower priority.
  ✅ Reduces starvation.

---

## 🎯 Placement Style Questions

**Q1. What is PCB?**
👉 Data structure storing process info (PID, state, registers, memory, scheduling info).

**Q2. Difference between Process & Thread?**
👉 Process = Independent unit with its own memory. Thread = Lightweight unit inside process, shares memory.

**Q3. Explain Context Switching.**
👉 Saving state of current process in PCB and loading another process → overhead but enables multitasking.

**Q4. Convoy Effect?**
👉 When one long process delays smaller processes (in FCFS).

**Q5. Which scheduling algorithm is best for time-sharing systems?**
👉 **Round Robin (RR)**.

---

## 🧠 Memory Hacks

* **PCB = Aadhaar card** of process.
* **Context Switch = Teacher pausing one viva, calling another student**.
* **FCFS = Queue at ATM**.
* **SJF = Fast food counter, small orders first**.
* **RR = Cricket batting, everyone gets 2 overs (TQ)**.
* **MLQ = VIP vs Normal queues**.
* **MLFQ = Dynamic queues (VIP pass can be earned if you wait too long)**.

---
