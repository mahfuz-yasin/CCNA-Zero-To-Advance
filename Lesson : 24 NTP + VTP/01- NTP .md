# NTP + VTP

# ⏰ NTP (Network Time Protocol) Configuration Guide

This guide demonstrates how to configure **NTP** to synchronize time across network devices using a centralized server.

---

## 📘 What is NTP?

**NTP (Network Time Protocol)** is a protocol used to synchronize the clocks of computer systems over packet-switched, variable-latency data networks.

> 🔍 Time synchronization is essential because many networking services and protocols rely on accurate timestamps.

---

## 🖼️ Network Diagram

> *(Add your own network diagram here with Router and NTP Server connected.)*

---

## ⚙️ Configuration Steps

### 1️⃣ Basic Configuration

Perform initial setup on Router and Server (hostname, IP, etc.).

### 2️⃣ Assign IP Addresses

Assign IP addresses to:

* **Router**
* **Server**

Example:

* Router IP: `200.0.0.1`
* NTP Server IP: `200.0.0.2`

---

### 3️⃣ Setup Time in Server

📌 **Steps**:

1. Click on **Server**
2. Go to **Services**
3. Click on **NTP**
4. Set the correct date and time

---

### 4️⃣ Configure NTP in Router

🔧 **Command (in Router CLI)**:

```bash
Router(config)# ntp server 200.0.0.2
```

This command tells the router to synchronize its time with the NTP server at `200.0.0.2`.

---

## ✅ Verification

### 🔍 Check NTP Association

```bash
Router# show ntp associations
```

### 🔍 Check Clock Details

```bash
Router# show clock detail
```

---

## 🧠 Why Use NTP?

* Ensures **uniform time** across routers, switches, firewalls, and servers
* Critical for **log accuracy**, **troubleshooting**, and **time-sensitive applications**

---
