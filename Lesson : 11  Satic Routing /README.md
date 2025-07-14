# 🛰️ Static Routing

## 📌 Static Routing Between Two Routers

### 🔹 Steps:
- Basic Configuration
- Assign IP Address to PC (via DHCP)
- Configure Static Routing
- Verify Static Routes

---

## 🚦 Router 0

### 🔧 Basic Configuration:
```bash
Router> enable                 // User EXEC mode
Router# configure terminal     // Privileged EXEC mode
Router(config)# interface gig0/0    // LAN interface
Router(config-if)# ip address 192.168.10.1 255.255.255.0
Router(config-if)# no shutdown

Router(config)# interface se0/1/0    // Serial interface to Router 1
Router(config-if)# ip address 100.10.10.1 255.255.255.0
Router(config-if)# no shutdown
````

### 🖥️ Assign IP to PC Dynamically (DHCP):

```bash
Router(config)# ip dhcp pool IT
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
```

### 📍 Static Routing:

```bash
Router(config)# ip route 192.168.20.0 255.255.255.0 100.10.10.2
```

---

## 🚦 Router 1

### 🔧 Basic Configuration:

```bash
Router> enable
Router# configure terminal
Router(config)# interface gig0/0
Router(config-if)# ip address 192.168.20.1 255.255.255.0
Router(config-if)# no shutdown

Router(config)# interface se0/0/0
Router(config-if)# ip address 100.10.10.2 255.255.255.0
Router(config-if)# no shutdown
```

### 🖥️ Assign IP to PC Dynamically (DHCP):

```bash
Router(config)# ip dhcp pool Sales
Router(dhcp-config)# network 192.168.20.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.20.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
```

### 📍 Static Routing:

```bash
Router(config)# ip route 192.168.10.0 255.255.255.0 100.10.10.1
```

---

### ✅ Verification Commands:

```bash
Router# show ip route
Router# show ip protocols
Router# ping 192.168.10.x
Router# ping 192.168.20.x
```

---

## 🚦 Static Routing Between Three Routers

### 🔹 Steps:

* Basic Configuration
* Assign IP Address to PC (via DHCP)
* Configure Static Routing
* Verify Static Routes

> নিচের উদাহরণে Router 0 ↔ Router 1 ↔ Router 2 সংযুক্ত।

---

## 🛠️ Router 0

### 🔧 Basic Configuration:

```bash
Router(config)# interface gig0/0
Router(config-if)# ip address 192.168.10.1 255.255.255.0
Router(config-if)# no shutdown

Router(config)# interface se0/1/0
Router(config-if)# ip address 100.10.10.1 255.255.255.0
Router(config-if)# no shutdown
```

### 🖥️ DHCP:

```bash
Router(config)# ip dhcp pool IT
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
```

### 📍 Static Routing:

```bash
Router(config)# ip route 192.168.30.0 255.255.255.0 100.10.10.2
```

---

## 🛠️ Router 1

### 🔧 Basic Configuration:

```bash
Router(config)# interface se0/0/0
Router(config-if)# ip address 100.10.10.2 255.255.255.0
Router(config-if)# no shutdown

Router(config)# interface se0/1/0
Router(config-if)# ip address 100.20.20.1 255.255.255.0
Router(config-if)# no shutdown
```

### 📍 Static Routing:

```bash
Router(config)# ip route 192.168.10.0 255.255.255.0 100.10.10.1
Router(config)# ip route 192.168.30.0 255.255.255.0 100.20.20.2
```

---

## 🛠️ Router 2

### 🔧 Basic Configuration:

```bash
Router(config)# interface gig0/0
Router(config-if)# ip address 192.168.30.1 255.255.255.0
Router(config-if)# no shutdown

Router(config)# interface se0/0/0
Router(config-if)# ip address 100.20.20.2 255.255.255.0
Router(config-if)# no shutdown
```

### 🖥️ DHCP:

```bash
Router(config)# ip dhcp pool HR
Router(dhcp-config)# network 192.168.30.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.30.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
```

### 📍 Static Routing:

```bash
Router(config)# ip route 192.168.10.0 255.255.255.0 100.20.20.1
```

---

### ✅ Verification Commands (For All Routers):

```bash
Router# show ip route
Router# show ip protocols
Router# ping [remote-network-IP]
```

---

> 🔁 Make sure clock rate is set on DCE end of serial interface:

```bash
Router(config-if)# clock rate 64000
```
