# 📘 Computer Networks – Switch, Router & Repeater 

Now we move from basic idea → to actual intelligent devices.

This is where networking actually becomes interesting.

---

# 1️⃣ Switch (Layer 2 Device – Data Link Layer)

![Image](https://m.media-amazon.com/images/I/61fIasArsQL._AC_UF1000%2C1000_QL80_.jpg)

![Image](https://images.monoprice.com/cms_images/pexels-brett-sayles_250617.jpg)

![Image](https://online.visual-paradigm.com/repository/images/061db788-c53c-42d6-ade4-da52ea017608.png)

![Image](https://cf-assets.www.cloudflare.com/slt3lc6tev37/6ENfwtM3iUH99JpYoEC9FY/04abc1654ceff2645f50713394ebcb73/network-switch.svg)

## 📌 What is a Switch?

A **Switch** is a network device that connects multiple computers in a LAN and sends data **only to the intended device**, not to everyone.

Unlike a hub:

* Hub → Broadcast to all
* Switch → Send to specific device

---

## 🧠 Core Concept: MAC Address Based Communication

Every network device has a unique **MAC address** (Media Access Control address).

Example:

```
PC1 → MAC: AA:11
PC2 → MAC: BB:22
PC3 → MAC: CC:33
```

When PC1 sends data to PC3:

```
PC1 → Switch → PC3 (ONLY)
```

Switch checks:

* Destination MAC
* Looks into MAC table
* Forwards packet only to that port

---

## 📊 How Switch Works (Step-by-Step)

1. Receives data frame
2. Reads source MAC address
3. Stores it in MAC table
4. Reads destination MAC
5. Forwards frame to correct port

If destination unknown → Temporary broadcast
Once learned → Unicast

---

## 🔥 Important: Full-Duplex

Switch supports **Full-Duplex Mode**

Meaning:

* Send + Receive simultaneously

Hub = Half duplex
Switch = Full duplex

This reduces collisions.

---

## ✅ Advantages of Switch

* Private communication (Unicast)
* Higher speed
* More secure than hub
* Better bandwidth usage
* Stable network
* MAC based filtering

---

## ❌ Disadvantages

* Expensive compared to hub
* If switch fails → Entire LAN down (Single point failure)
* Configuration required (especially managed switches)

---

## 🧠 Real World Example

Your college computer lab:

If 60 students are working:

* Hub → Everyone’s data goes everywhere → slow
* Switch → Each system communicates independently → fast

That’s why hubs are obsolete today.

---

# 2️⃣ Router (Layer 3 Device – Network Layer)

![Image](https://i.rtings.com/assets/pages/zqvV4jR6/best-routers-for-large-houses-20240416-2-medium.jpg?format=auto)

![Image](https://images.wondershare.com/edrawmax/templates/wireless-network-diagram.png)

![Image](https://www.smallnetbuilder.com/images_old/myimages/howto/two_private_lans.gif)

![Image](https://www.researchgate.net/publication/326060523/figure/fig1/AS%3A642817676304388%401530271085420/Example-of-a-Network-to-Network-In-Figure-3-there-is-two-network-connected-to-a-router.png)

## 📌 What is a Router?

A **Router** connects different networks together and finds the best path for data to travel.

If Switch is local traffic manager,
Router is highway traffic controller.

---

## 🌍 Example

Your home:

```
Laptop → Switch → Router → ISP → Internet
```

Router connects:

* Your LAN
* ISP’s WAN

---

## 🧠 Core Function: Routing

Router:

* Reads IP address
* Checks routing table
* Finds best path
* Forwards packet

It uses algorithms like:

* Shortest Path First
* Distance Vector
* Link State

---

## 📊 How Router Works (Step-by-Step)

1. Receives packet
2. Checks destination IP
3. Searches routing table
4. Chooses best route
5. Forwards to next hop

---

## 🔥 Important Difference

Switch works using:

* MAC Address (Layer 2)

Router works using:

* IP Address (Layer 3)

---

## ✅ Advantages of Router

* Connects different networks
* Supports wired + wireless
* Intelligent routing
* Traffic control
* Network segmentation
* Reduces broadcast domain

---

## ❌ Disadvantages

* Expensive
* Complex configuration
* Needs firmware/software
* Can become bottleneck
* Requires security configuration (Firewall, NAT)

---

## 🧠 Real World Understanding

When you open:

```
google.com
```

Your request travels:

```
Laptop → Router → ISP → Multiple Routers → Google Server
```

Without router → Internet impossible.

---

# 3️⃣ Repeater (Layer 1 Device – Physical Layer)

![Image](https://nailyourinterview.org/_next/static/media/repeater.f6aa93f5.webp)

![Image](https://www.lintratek.com/uploads/Basic-Principles-of-Mobile-Signal-Repeater.jpg)

![Image](https://cfrouting.zoeysite.com/cdn-cgi/image/format%3Dauto%2Cquality%3D85%2Cfit%3Dscale-down/https%3A//s3.amazonaws.com/zcom-media/sites/a0i0L00000TLpceQAD/media/catalog/product/p/r/productimages-er-s1110-xlg.jpg)

![Image](https://westwardsales.com/image/cache/data/blackbox/resources/LPR1111_main_25681-1000x1000.jpg)

## 📌 What is a Repeater?

A **Repeater** is a device that:

* Receives weak signal
* Regenerates it
* Sends it forward

It does NOT filter
It does NOT analyze
It just boosts signal

---

## 🧠 Why Needed?

Signals weaken over long distance.

Example:

* Ethernet cable limit ≈ 100 meters
* Beyond that → signal weakens

Repeater allows:

* Extended distance

---

## 📊 Working

```
Sender → Weak Signal → Repeater → Strong Signal → Receiver
```

It regenerates to original strength.

---

## 📺 Real Life Example

Old cable TV systems:

Black boxes on electric poles → Repeaters

Without repeater:

* Picture blur
* Noise

With repeater:

* Clear signal

---

## ✅ Advantages

* Extends network distance
* Cheap device
* Simple installation
* Maintains signal quality

---

## ❌ Disadvantages

* Does not reduce traffic
* Cannot filter data
* Cannot connect different networks
* Too many repeaters = delay
* Works only at physical level

---

# 🔥 Complete Comparison (Hub vs Switch vs Router vs Repeater)

| Feature           | Hub  | Switch      | Router | Repeater |
| ----------------- | ---- | ----------- | ------ | -------- |
| OSI Layer         | 1    | 2           | 3      | 1        |
| Address Used      | None | MAC         | IP     | None     |
| Intelligent       | No   | Yes         | Highly | No       |
| Broadcast         | Yes  | No (mostly) | No     | Yes      |
| Connects Networks | No   | No          | Yes    | No       |
| Signal Boost      | No   | No          | No     | Yes      |
| Duplex Mode       | Half | Full        | Full   | Half     |

---

# 🧠 Mental Architecture Understanding

Think like this:

```
Repeater → Boost
Hub → Distribute blindly
Switch → Deliver intelligently (inside LAN)
Router → Deliver globally (between networks)
```

---

# 🚀 Engineering-Level Understanding You Must Develop

You should now clearly understand:

* Switch = Layer 2 = MAC-based
* Router = Layer 3 = IP-based
* Repeater = Layer 1 = Signal-based

If someone asks:

"How does data go from your laptop to US server?"

You must answer step-by-step using:

* MAC
* IP
* Switch
* Router
* Routing

If you cannot explain full data journey → You don’t understand networking yet.

---
