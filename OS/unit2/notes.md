
# 🖥️ UNIT 2 – OS Components & System Calls

---

## 1️⃣ Components of OS

### 🟢 1. Kernel (Heart of OS)

* **Definition**: Core part of OS, directly talks to hardware.
* **Loads first** when computer starts.
* Handles: Process, Memory, File, I/O management.

👉 Think of **Kernel = Engine of a Car**.

* Without engine, car won’t run.
* User doesn’t touch engine directly → Uses steering, pedals (like shell).

---

### 🟢 2. User Space

* Where **applications** run.
* Apps cannot access hardware directly (no privileges).
* Communicate with kernel using **system calls**.

👉 Analogy: You can’t enter the airplane cockpit (kernel), you sit in passenger cabin (user space) and give requests to pilot via crew (system calls).

---

### 🟢 3. Shell

* Command interpreter (CLI or GUI).
* Takes commands from user → sends to kernel.
  👉 Example: Terminal, PowerShell, Bash.

---

## 2️⃣ Functions of Kernel

1. **Process Management** → Create, delete, suspend, resume, schedule processes.
2. **Memory Management** → Allocate/deallocate, keep track of memory usage.
3. **File Management** → Create, delete, organize files & directories.
4. **I/O Management** → Handle devices (buffering, caching, spooling).

📌 **Spooling** → Print queue.
📌 **Buffering** → YouTube video buffering.
📌 **Caching** → Browser cache, memory cache.

---

## 3️⃣ Types of Kernels

| Kernel Type     | Features                                                                                | Pros                               | Cons                                                    | Examples            |
| --------------- | --------------------------------------------------------------------------------------- | ---------------------------------- | ------------------------------------------------------- | ------------------- |
| **Monolithic**  | All OS services inside kernel                                                           | High performance                   | Less reliable (if 1 module fails, whole kernel crashes) | Linux, Unix, MS-DOS |
| **Microkernel** | Only essential services in kernel (process + memory mgmt). Other services in user space | Stable, reliable                   | Slower (more user ↔ kernel switching)                   | MINIX, Symbian      |
| **Hybrid**      | Combines both (fast + stable)                                                           | Balance between speed & modularity | Some overhead                                           | Windows NT, macOS   |
| **Exo/Nano**    | Minimalist kernel, very small                                                           | High modularity                    | Very complex to design                                  | Research OS         |

---

## 4️⃣ User Mode vs Kernel Mode

* **User Mode** → Apps run, limited access.
* **Kernel Mode** → Full access to hardware.

👉 **Transition** happens via **System Calls**.

* Example: When you save a file → App → System Call → Kernel writes to disk.

---

## 5️⃣ System Calls (Very Important for Placements 🚨)

**Definition**: Mechanism for apps to request kernel services.

* Apps can’t access hardware directly.
* Only way to enter **kernel mode** from **user mode**.

👉 Example: `mkdir` in Linux → Behind the scenes, it calls a system call that interacts with file management module in kernel.

---

### 📌 Types of System Calls

1. **Process Control**

   * create, terminate, wait, abort.
   * Example: `fork()`, `exit()`, `wait()`.

2. **File Management**

   * create, open, read, write, delete.
   * Example: `open()`, `read()`, `write()`.

3. **Device Management**

   * request/release device, read/write device.
   * Example: `ioctl()`, `read()`, `write()`.

4. **Information Maintenance**

   * get time/date, get process info.
   * Example: `getpid()`, `alarm()`.

5. **Communication**

   * send/receive messages, create pipe, shared memory.
   * Example: `pipe()`, `shmget()`, `mmap()`.

📌 **System Calls in Windows** → `CreateProcess()`, `ReadFile()`.
📌 **System Calls in Unix** → `fork()`, `read()`, `open()`.

---

## 6️⃣ Booting Process (Interview Favorite)

What happens when you turn on your computer?

1. **Power ON** → CPU starts.
2. **BIOS/UEFI** → Firmware checks hardware (POST – Power On Self Test).
3. **Bootloader** → Finds OS and loads it.

   * Windows → `bootmgr.exe`
   * Linux → GRUB
   * macOS → `boot.efi`
4. Bootloader loads **Kernel**.
5. Kernel starts **User Space**.

👉 Analogy: Starting a car:

* Turn key → Engine check → ECU loads → Engine starts → Car ready to drive.

---

## 7️⃣ 32-bit vs 64-bit OS

* **32-bit** → Can use up to 2³² = 4GB RAM.
* **64-bit** → Can use up to 2⁶⁴ (theoretically huge, practically limited).
* **64-bit CPUs** can run both 32-bit & 64-bit OS.
* **Performance**: 64-bit faster (handles more data per cycle, better graphics).

---

## 🎯 Placement Style Questions

**Q1. What is a Kernel?**
👉 Core of OS, first loaded, manages hardware directly (process, memory, file, I/O).

**Q2. Difference between Monolithic & Microkernel.**
👉 Monolithic = Fast, but less reliable. Micro = Stable, but slower.

**Q3. How do apps interact with hardware?**
👉 Through **system calls** (user → kernel transition).

**Q4. What happens when you switch on a computer?**
👉 Power ON → BIOS/UEFI → Bootloader → Kernel → User Space.

**Q5. 32-bit vs 64-bit OS difference?**
👉 32-bit supports up to 4GB RAM, 64-bit supports much larger memory + better performance.

---

## 🧠 Memory Hacks (Unit 2)

* **Kernel = Engine**.
* **System Call = Doorbell** (app presses, kernel answers).
* **Monolithic = One Big Kitchen**, Microkernel = Separate Kitchens for each service.
* **Booting = Morning routine** (Wake up → Check health → Dress → Go to work).

---
