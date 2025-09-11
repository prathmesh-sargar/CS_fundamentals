
# 🧾 UNIT 2 – Quick Summary (Revision Sheet)

---

### 📌 Components of OS

* **Kernel (Engine of OS)** → Core, manages hardware (process, memory, file, I/O).
* **User Space** → Apps run here, no direct hardware access.
* **Shell (Command Interpreter)** → Bridge between user & kernel (CLI/GUI).

---

### 📌 Functions of Kernel

1. Process Management → Create, delete, schedule.
2. Memory Management → Allocate/deallocate.
3. File Management → Create, delete, organize.
4. I/O Management → Spooling, Buffering, Caching.

---

### 📌 Types of Kernels

| Type            | Key Idea                  | Pros     | Cons          | Examples          |
| --------------- | ------------------------- | -------- | ------------- | ----------------- |
| **Monolithic**  | All services in kernel    | Fast     | Less reliable | Linux, Unix       |
| **Microkernel** | Only essentials in kernel | Stable   | Slower        | MINIX, Symbian    |
| **Hybrid**      | Mix of both               | Balanced | Overhead      | Windows NT, macOS |
| **Exo/Nano**    | Minimal core              | Modular  | Complex       | Research OS       |

---

### 📌 User Mode vs Kernel Mode

* **User Mode** → Limited access, apps run.
* **Kernel Mode** → Full hardware access.
* **Switch** → Happens via **System Calls**.

---

### 📌 System Calls (Apps → Kernel)

1. **Process Control** → create, terminate, wait (`fork()`, `exit()`).
2. **File Management** → open, read, write (`open()`, `read()`).
3. **Device Management** → request, release (`ioctl()`).
4. **Info Maintenance** → get time, get PID (`getpid()`, `alarm()`).
5. **Communication** → pipes, shared memory (`pipe()`, `shmget()`).

---

### 📌 Booting Process (Power ON → OS Ready)

1. Power ON
2. **BIOS/UEFI** → Hardware check (POST)
3. **Bootloader** → Loads OS

   * Windows → bootmgr.exe
   * Linux → GRUB
   * macOS → boot.efi
4. Kernel loads
5. User Space starts

---

### 📌 32-bit vs 64-bit OS

* **32-bit** → 4GB RAM max, 32-bit registers.
* **64-bit** → Huge memory, faster, supports both 32/64-bit OS.
* **64-bit better** → Performance, graphics, resource usage.

---

### 🎯 Must-Remember for Placements

1. Kernel = Engine of OS.
2. System Calls = Only way User Mode ↔ Kernel Mode.
3. Monolithic vs Microkernel (most asked).
4. Booting Steps in order.
5. 32-bit vs 64-bit differences.

---

### 🧠 Easy Analogies

* Kernel = Engine 🚗
* System Call = Doorbell 🔔 (app rings, kernel responds)
* Booting = Morning routine 🌅
* Monolithic = One Big Kitchen 🍲, Microkernel = Separate Kitchens 🍱

---
