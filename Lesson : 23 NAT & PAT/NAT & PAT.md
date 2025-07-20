# 🌐 NAT & PAT 

## 📖 Overview

**NAT (Network Address Translation)** allows private IP addresses to be translated into public IP addresses, enabling internal devices to communicate over the internet.

### 🔄 Types of NAT:

1. **Static NAT** – Maps one private IP to one public IP.
2. **Dynamic NAT** – Maps private IPs to a pool of public IPs.
3. **PAT (Port Address Translation)** – Maps multiple private IPs to a single public IP using different ports (aka NAT Overload).

---

## 🧪 Lab 1: Static NAT

### 🖼️ Network Diagram

*(Add your network diagram here)*

### ⚙️ Steps

1. Basic router configuration
2. Assign IP addresses
3. Verify PC gateway
4. Configure NAT inside & outside interfaces
5. Configure static NAT
6. Verify NAT


### 🖧 Topology

```
[PC1] ---- [G0/0] R1 [G0/1] ---- [Internet/PC2]
  |           Inside      Outside
  |          
192.168.1.10          203.0.113.1
```
### Diagram : 

<img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/6eace237-926c-49df-bb24-d85bb26c11b7" />
---

### ⚙️ Step-by-Step Configuration

### ✅ 1. Basic Router Configuration

```bash
Router> enable
Router# configure terminal
Router(config)# hostname R1
Router(config)# no ip domain-lookup
```

---

### ✅ 2. Assign IP Addresses

```bash
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface g0/1
Router(config-if)# ip address 203.0.113.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
```

---

### ✅ 3. Verify PC Gateway

**PC1:**

* IP: `192.168.1.10`
* Subnet Mask: `255.255.255.0`
* Gateway: `192.168.1.1`

---

### ✅ 4. Configure Inside & Outside Interfaces

```bash
Router(config)# interface g0/0
Router(config-if)# ip nat inside
Router(config-if)# exit

Router(config)# interface g0/1
Router(config-if)# ip nat outside
Router(config-if)# exit
```

---

### ✅ 5. Configure Static NAT

```bash
Router(config)# ip nat inside source static 192.168.1.10 203.0.113.10
```

> 🔁 This means:
> Inside local IP `192.168.1.10` will be seen publicly as `203.0.113.10`

---

### ✅ 6. Verify NAT

```bash
Router# show ip nat translations
Router# show ip nat statistics
```

➡️ To test, **ping from PC1 to an external IP** (e.g., simulated server).


## 🧪 Lab 2: Dynamic NAT

### ⚙️ Steps

1. Basic configuration
2. Assign IP addresses to PCs
3. Check gateway
4. Configure inside/outside interfaces
5. Create ACL for inside source IPs
6. Configure NAT pool
7. Enable dynamic NAT
8. Verify NAT



## 🔧 1. Basic Configuration (Router Name & Interfaces)

```bash
Router> enable
Router# configure terminal
Router(config)# hostname R1
Router(config)# no ip domain-lookup
```

---

## 🖥️ 2. Assign IP Addresses to PCs

**PC1:**

* IP: `10.0.0.2`
* Subnet Mask: `255.255.255.0`
* Default Gateway: `10.0.0.1`

**PC2:**

* IP: `10.0.0.3`
* Subnet Mask: `255.255.255.0`
* Default Gateway: `10.0.0.1`

---

## 🌐 3. Check & Set Gateway on Router

```bash
Router(config)# interface gig0/0
Router(config-if)# ip address 10.0.0.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface gig0/1
Router(config-if)# ip address 192.0.2.1 255.255.255.0
Router(config-if)# no shutdown
```

---

## 🔄 4. Configure NAT Inside/Outside Interfaces

```bash
Router(config)# interface gig0/0
Router(config-if)# ip nat inside
Router(config-if)# exit

Router(config)# interface gig0/1
Router(config-if)# ip nat outside
Router(config-if)# exit
```

---

## 🔐 5. Create ACL for Inside Source IPs

```bash
Router(config)# access-list 1 permit 10.0.0.0 0.0.0.255
```

---

## 🛜 6. Configure NAT Pool (Public IP Range)

```bash
Router(config)# ip nat pool NAT_POOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0
```

---

## ✅ 7. Enable Dynamic NAT Using ACL + Pool

```bash
Router(config)# ip nat inside source list 1 pool NAT_POOL
```

---

## 🔍 8. Verify NAT Configuration

➡️ First, generate some traffic from PC to the Internet or a simulated server:

```bash
PC> ping 8.8.8.8
```

➡️ Then, quickly run:

Use `ping` from PC to server and quickly run:

```bash
Router# show ip nat translations
Router# show ip nat statistics
```



## 🧪 Lab 3: PAT (NAT Overload)

### ⚙️ Steps

1. Basic configuration
2. Assign IP addresses to PCs
3. Verify gateway
4. Configure NAT interfaces
5. Create ACL for inside source IPs
6. Enable NAT with Overload (PAT)
7. Verify PAT



### 🖧 Topology Overview:

```
[PC1]    [PC2]  
  |         |
  |         |---- [g0/0] R1 [g0/1] ---- Internet (8.8.8.8)
192.168.1.10     192.168.1.20     Inside    Outside
```

---

### ⚙️ Step-by-Step Configuration:

---

### ✅ 1. Basic Router Configuration

```bash
Router> enable
Router# configure terminal
Router(config)# hostname R1
Router(config)# no ip domain-lookup
```

---

### ✅ 2. Assign IP Addresses to PCs

**PC1:**

* IP: `192.168.1.10`
* Subnet Mask: `255.255.255.0`
* Gateway: `192.168.1.1`

**PC2:**

* IP: `192.168.1.20`
* Subnet Mask: `255.255.255.0`
* Gateway: `192.168.1.1`

---

### ✅ 3. Verify Gateway on Router

```bash
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface g0/1
Router(config-if)# ip address 203.0.113.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
```

---

### ✅ 4. Configure NAT Interfaces

```bash
Router(config)# interface g0/0
Router(config-if)# ip nat inside
Router(config-if)# exit

Router(config)# interface g0/1
Router(config-if)# ip nat outside
Router(config-if)# exit
```

---

### ✅ 5. Create ACL for Inside Source IPs

```bash
Router(config)# access-list 1 permit 192.168.1.0 0.0.0.255
```

---

### ✅ 6. Enable NAT with Overload (PAT)

```bash
Router(config)# ip nat inside source list 1 interface g0/1 overload
```

📌 This means:

* All IPs from 192.168.1.0/24 will be translated using the **interface IP 203.0.113.1** with different **port numbers**.

---

### ✅ 7. Verify PAT

```bash
# Generate traffic from PCs (e.g., ping 8.8.8.8)

Router# show ip nat translations
Router# show ip nat statistics
```

---

📘 **Explanation:**

| Component       | Description                           |
| --------------- | ------------------------------------- |
| `access-list 1` | Allows traffic from inside LAN        |
| `overload`      | Enables PAT (many-to-one using ports) |
| `g0/1`          | Public interface for NAT              |
---

* NAT helps conserve IPv4 addresses.
* PAT is the most common form of NAT in home and small office networks.
* Use `show ip nat statistics` for deeper diagnostics