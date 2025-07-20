# 🛰️ OSPF (Open Shortest Path First) Complete Configuration & Theory Guide

## 📖 What is OSPF?

**OSPF (Open Shortest Path First)** is a **Link-State Routing Protocol** used within an Autonomous System (AS) to automatically exchange routing information. It uses the **Dijkstra Shortest Path First (SPF)** algorithm to determine the most efficient path.

---

## 🧠 Why Use OSPF?

| Reason                     | Description                                                        |
|----------------------------|--------------------------------------------------------------------|
| 🔄 Dynamic Routing         | Automatically shares routing updates with neighbors               |
| ⚡ Fast Convergence        | Quickly adapts to changes in the network                          |
| 📶 Bandwidth-Based Metric | Uses bandwidth (cost) instead of hop count                        |
| 🔐 Security Options        | Supports authentication (MD5, etc.)                              |
| 🌍 Scalable Network Design | Supports hierarchical areas for large networks                    |

---

## 🔧 Key OSPF Concepts

| Term           | Description                                                        |
|----------------|--------------------------------------------------------------------|
| **Router ID**  | Unique ID of the router (can be manual or highest IP/loopback)     |
| **Neighbor**   | Routers that directly exchange OSPF hello packets                   |
| **LSA**        | Link State Advertisement – updates sent between routers            |
| **LSDB**       | Link State Database – map of network topology                      |
| **SPF Tree**   | Built by router to determine best paths                            |
| **DR/BDR**     | Designated Router / Backup DR on broadcast networks                |

---

## 🗂️ OSPF Areas

- **Backbone Area:** `Area 0` – all other areas must connect through it
- **Other Areas:** `Area 1, 2, ...` – used for scalability and segmentation

---

## 📦 OSPF Packet Types

| Packet Type | Description                           |
|-------------|---------------------------------------|
| Hello       | Discover and maintain neighbors       |
| DBD         | Database Description                  |
| LSR         | Link State Request                    |
| LSU         | Link State Update                     |
| LSAck       | Link State Acknowledgment             |

---

## 🧪 Lab Topology

```

\[PC1]---\[R1]---\[R2]---\[PC2]
192.168.1.0 192.168.12.0 192.168.2.0

````

---

## ⚙️ Step-by-Step OSPF Configuration

### 🔹 R1 Configuration

```bash
Router> enable
Router# configure terminal
Router(config)# hostname R1
R1(config)# interface g0/0
R1(config-if)# ip address 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown

R1(config)# interface g0/1
R1(config-if)# ip address 192.168.12.1 255.255.255.0
R1(config-if)# no shutdown

R1(config)# router ospf 1
R1(config-router)# router-id 1.1.1.1
R1(config-router)# network 192.168.1.0 0.0.0.255 area 0
R1(config-router)# network 192.168.12.0 0.0.0.255 area 0
````

---

### 🔹 R2 Configuration

```bash
Router> enable
Router# configure terminal
Router(config)# hostname R2
R2(config)# interface g0/0
R2(config-if)# ip address 192.168.12.2 255.255.255.0
R2(config-if)# no shutdown

R2(config)# interface g0/1
R2(config-if)# ip address 192.168.2.1 255.255.255.0
R2(config-if)# no shutdown

R2(config)# router ospf 1
R2(config-router)# router-id 2.2.2.2
R2(config-router)# network 192.168.12.0 0.0.0.255 area 0
R2(config-router)# network 192.168.2.0 0.0.0.255 area 0
```

---

## 🔍 Verification Commands

```bash
show ip ospf neighbor         # View neighbor relationships
show ip route ospf            # Check learned OSPF routes
show ip ospf interface        # View OSPF-enabled interfaces
show ip protocols             # General routing protocol info
show running-config | section ospf
```

---

## 🔐 Authentication in OSPF

```bash
interface g0/0
 ip ospf authentication message-digest
 ip ospf message-digest-key 1 md5 YOUR_PASSWORD

router ospf 1
 area 0 authentication message-digest
```

---

## 🛡️ OSPF Default Route Advertisement

```bash
ip route 0.0.0.0 0.0.0.0 [next-hop-ip]
router ospf 1
 default-information originate
```

---

## 🧮 OSPF Cost Calculation

```
Cost = 100,000,000 / Bandwidth (in bps)

Example:
100 Mbps → 100,000,000 / 100,000,000 = Cost 1
10 Mbps  → 100,000,000 / 10,000,000  = Cost 10
```

Use this to influence route preference.

---

## 🧠 Timer Defaults

| Timer Type | Value      |
| ---------- | ---------- |
| Hello      | 10 seconds |
| Dead       | 40 seconds |

Must match on both routers for neighbor relationship.

---

## 💡 Best Practices

* Use **loopback interface** for stable Router ID
* Set **manual router-id** for clarity
* **Area 0 is mandatory** for multi-area setup
* Always verify with `show` commands
* Avoid duplicate router IDs

---

✅ **Conclusion**: OSPF is a scalable, secure, and fast-converging routing protocol perfect for large or dynamic enterprise networks.

``‌‌`