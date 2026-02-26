# 📘 Computer Networks – TCP vs UDP, Transmission Modes & Data Transmission (Strong Fundamentals Section)

Now we’re entering **Transport layer depth + Physical transmission understanding**.

If you don’t understand this clearly → you cannot understand how internet actually works.

---

# 🧩 SECTION 1: TCP vs UDP (Transport Layer – Layer 4)

These are transport layer protocols under TCP/IP model.

---

## 🔹 TCP (Transmission Control Protocol)

### 📌 Core Nature

* Connection-oriented
* Reliable
* Ordered
* Error-checked

---

### 🧠 How TCP Works (Very Important)

Before sending data:

### 1️⃣ Three-Way Handshake

```id="tcp1"
Client → SYN →
Server → SYN-ACK →
Client → ACK →
```

Connection established.

---

### 2️⃣ Data Transfer

* Data divided into segments
* Sequence numbers assigned
* Receiver sends acknowledgment (ACK)
* Lost packet → retransmitted

---

### 3️⃣ Connection Termination

Gracefully closed.

---

### 📦 Header Size

20 bytes (minimum)

Because it includes:

* Sequence number
* ACK number
* Flags
* Window size
* Checksum

---

### ✅ Advantages

* Guaranteed delivery
* Correct order
* Congestion control
* Flow control

---

### ❌ Disadvantages

* Slower (due to checks & handshake)
* More overhead

---

### 🚀 Used In

* HTTP / HTTPS
* FTP
* SMTP
* Banking systems
* File downloads

---

## 🔹 UDP (User Datagram Protocol)

### 📌 Core Nature

* Connectionless
* Unreliable
* No acknowledgment
* No ordering guarantee

---

### 🧠 How UDP Works

```id="udp1"
Sender → Sends data
Receiver → May or may not receive
```

No handshake. No confirmation.

---

### 📦 Header Size

8 bytes

Very small → Faster.

---

### ✅ Advantages

* Fast
* Low overhead
* Real-time communication friendly

---

### ❌ Disadvantages

* Packet loss possible
* No retransmission
* No ordering guarantee

---

### 🚀 Used In

* Video conferencing
* Online gaming
* Live streaming
* DNS queries

---

## 🔥 TCP vs UDP Comparison

| Feature        | TCP        | UDP            |
| -------------- | ---------- | -------------- |
| Connection     | Required   | Not required   |
| Reliability    | Guaranteed | Not guaranteed |
| Ordering       | Yes        | No             |
| Speed          | Slower     | Faster         |
| Retransmission | Yes        | No             |
| Header Size    | 20 bytes   | 8 bytes        |

---

## 🧠 Real Engineering Understanding

Video call uses UDP because:

If one packet drops:

* You don’t want delay
* You prefer speed over perfection

Bank transfer uses TCP because:

If ₹10,000 packet lost:

* Not acceptable.

---

# 🧩 SECTION 2: Data Transmission Modes (Communication Direction)

This defines **how two devices communicate**.

---

## 1️⃣ Simplex Mode

```id="simplex"
Sender → Receiver
```

Only one direction.

### Examples:

* Keyboard → CPU
* Monitor ← CPU
* Loudspeaker

---

### 🚨 Key Point

No feedback possible.

---

## 2️⃣ Half-Duplex Mode

```id="half"
Device A ⇄ Device B
(One at a time)
```

Both can send/receive
But NOT simultaneously.

### Example:

* Walkie-talkie

Press → Speak
Release → Listen

---

### 🚨 Used In:

* Old hub networks
* Some wireless systems

---

## 3️⃣ Full-Duplex Mode

```id="full"
Device A ⇄ Device B
(Simultaneously)
```

Send and receive at same time.

### Examples:

* Phone calls
* Modern switch networks

---

### 🚀 Why Important?

Switch supports full-duplex → No collision
Hub supports half-duplex → Collisions possible

---

## 🔥 Comparison

| Mode        | Direction              | Efficiency |
| ----------- | ---------------------- | ---------- |
| Simplex     | One-way                | Low        |
| Half-Duplex | Two-way (alternate)    | Medium     |
| Full-Duplex | Two-way (simultaneous) | High       |

---

# 🧩 SECTION 3: Data Transmission (Bit-Level Understanding)

Data travels as bits:

```
0 and 1
```

Transmission happens in two main ways:

---

# 🔹 Parallel Transmission

```id="parallel"
8 wires → 8 bits sent simultaneously
```

### 🧠 Characteristics

* Fast
* Multiple channels
* Expensive
* Short distance only

---

### Example:

* Old printer cables
* Internal motherboard communication

---

### 🚨 Problem

Long distance → Signal skew
Bits may not arrive together.

---

# 🔹 Serial Transmission

```id="serial"
1 wire → 1 bit at a time
```

### 🧠 Characteristics

* Cheaper
* Long distance friendly
* Slightly slower (bit by bit)

---

### Used In:

* USB
* Ethernet
* Internet communication

---

## 🔥 Why Serial Wins Today?

Because:

* Long-distance stable
* Less wiring complexity
* Modern high-speed serial is extremely fast

---

# 🧩 Types of Serial Transmission

---

## 1️⃣ Synchronous Transmission

Data sent in blocks.

```id="sync"
[Block1][Block2][Block3]
```

* Continuous stream
* No start/stop bits per character
* Faster

Used in:

* Ethernet
* High-speed networks

---

## 2️⃣ Asynchronous Transmission

Each character sent separately.

```id="async"
Start Bit (0) + Data + Stop Bit (1)
```

Example:

```
0 10101010 1
```

* Start bit alerts receiver
* Stop bit signals completion

Used in:

* Keyboard communication
* Serial ports (UART)

---

## 🔥 Comparison

| Feature    | Synchronous | Asynchronous    |
| ---------- | ----------- | --------------- |
| Speed      | Faster      | Slower          |
| Structure  | Block-based | Character-based |
| Overhead   | Low         | Higher          |
| Complexity | Higher      | Simple          |

---

# 🚀 Complete Big Picture Now

When you open a website:

1️⃣ Data created
2️⃣ Divided into bits
3️⃣ Serial transmission used
4️⃣ Full-duplex communication
5️⃣ TCP ensures reliability
6️⃣ IP ensures addressing

All these concepts work together.

---

# 🎯 What You Must Now Clearly Understand

If asked in interview:

* Why UDP used in gaming?
* Explain TCP handshake.
* Difference between synchronous and asynchronous?
* Why serial transmission preferred?
* What is full duplex?

If you can explain confidently without memorizing → your fundamentals are solid.

---
