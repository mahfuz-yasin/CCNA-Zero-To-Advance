# 🔐 ACL (Access Control List) 

An **Access Control List (ACL)** is used to permit or deny network traffic. It enhances network security by applying rules on routers.

---

## 📁 ACL Types

### ✅ Standard ACL
- Filters based on **source IP only**
- Numbered Range: `1–99` or `1300–1999`
- Placement: **Close to destination**

### ✅ Extended ACL
- Filters based on **source & destination IP, protocols, ports**
- Numbered Range: `100–199` or `2000–2699`
- Placement: **Close to source**

---

## 🧪 Lab Scenario: 3 Routers (R1, R2, R3)

### 💡 Objective Summary
| Task | Router | Goal |
|------|--------|------|
| 1️⃣ | R2 | Block `172.16.10.0/24` but allow `172.16.10.2` |
| 2️⃣ | R1 | Allow `172.16.30.2`, block rest of `172.16.30.0/24` |
| 3️⃣ | R3 | Block `172.16.10.0/24`, allow `172.16.10.2` to `172.16.50.0/24` |

---

# 3 Router Full Lab Configuration

## ⚙️ Configuration Steps

### 🔧 Step 1: Basic Configuration
```bash
Router> enable
Router# config terminal
Router(config)# hostname R1
Router(config)# interface g0/0
Router(config-if)# ip address 172.16.x.x 255.255.255.0
Router(config-if)# no shutdown
```
Repeat for all routers.

---

### 💻 Step 2: IP Assignment to PCs

Assign appropriate IP addresses and gateways to all connected PCs:
- **PC-A:** `172.16.10.2` → Gateway: `172.16.10.1`
- **PC-B:** `172.16.30.2`
- **PC-C:** `172.16.50.10`

---

### 🌐 Step 3: Static Routing

#### R0:
```bash
ip route 172.16.40.0 255.255.255.0 172.16.20.2
ip route 172.16.30.0 255.255.255.0 172.16.20.2
ip route 172.16.50.0 255.255.255.0 172.16.20.2
```

#### R1:
```bash
ip route 172.16.10.0 255.255.255.0 172.16.20.1
ip route 172.16.50.0 255.255.255.0 172.16.40.2
```

#### R2:
```bash
ip route 172.16.20.0 255.255.255.0 172.16.40.1
ip route 172.16.30.0 255.255.255.0 172.16.40.1
ip route 172.16.10.0 255.255.255.0 172.16.40.1
```

---

## 🚧 ACL Configuration

### ✅ Task 1: Standard ACL (R2)
```bash
access-list 20 permit host 172.16.10.2
access-list 20 deny 172.16.10.0 0.0.0.255
access-list 20 permit any
interface g0/0
ip access-group 20 out
```

---

### ✅ Task 2: Named Standard ACL (R1)
```bash
ip access-list standard CCNA
permit 172.16.30.2
deny 172.16.30.0 0.0.0.255
permit any
interface g0/0
ip access-group CCNA out
```

---

### ✅ Task 3: Extended ACL (R3)
```bash
access-list 110 permit ip host 172.16.10.2 172.16.50.0 0.0.0.255
access-list 110 deny ip 172.16.10.0 0.0.0.255 172.16.50.0 0.0.0.255
access-list 110 permit ip any any
interface g0/0
ip access-group 110 out
```

---

## 🧪 Practice Lab (Bonus)

### 🎯 Scenario:
- **Host A** can access **Finance Web Server**
- **Host A** cannot access **DNS & Public Web Server**
- **Host B, C, D** can access all servers

### ✅ ACL Configuration:
```bash
access-list 100 permit ip host 10.0.0.2 host 20.0.0.2
access-list 100 deny ip host 10.0.0.2 20.0.0.0 0.255.255.255
access-list 100 permit ip any any
interface g0/1
ip access-group 100 out
```

---

## ✅ Step 5: Verification

Use the following commands:
```bash
show access-lists
show ip interface g0/0
ping <destination-ip>
```

Test access between hosts and verify filtering rules.

---

## 📌 Notes
- **Standard ACL**: Filter only source IP
- **Extended ACL**: Filter source, destination, protocol, port
- **Placement**: 
  - Standard → Near Destination
  - Extended → Near Source
