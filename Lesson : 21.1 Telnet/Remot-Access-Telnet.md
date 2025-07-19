# 🌐 Remote Access - Telnet (Cisco Devices)

This guide walks you through enabling remote access to a Cisco router or switch using **Telnet**.

---

## ✅ Steps Overview

- Basic Configuration
- IP Assignment in PC
- Password Setup
- Remote Access via Telnet

---

## 1️⃣ Basic Configuration on Router

```bash
Router> enable
Router# configure terminal
Router(config)# hostname R1
R1(config)# interface FastEthernet0/0
R1(config-if)# ip address 192.168.1.1 255.255.255.0
R1(config-if)# no shutdown
R1(config-if)# exit
```

---

## 2️⃣ Set Console and VTY Passwords

```bash
R1(config)# line console 0
R1(config-line)# password cisco
R1(config-line)# login
R1(config-line)# exit

R1(config)# line vty 0 4
R1(config-line)# password telnet123
R1(config-line)# login
R1(config-line)# exit
```

---

## 3️⃣ Set Enable Password

```bash
R1(config)# enable secret admin123
```

---

## 4️⃣ Assign IP in PC (Manually)

🖥️ On the connected PC:

- IP Address: `192.168.1.2`
- Subnet Mask: `255.255.255.0`
- Default Gateway: `192.168.1.1` (Router IP)

---

## 5️⃣ Telnet Remote Access from PC

🔗 On the PC’s terminal or Command Prompt:
```bash
telnet 192.168.1.1
```

✅ After successful connection:
- Enter VTY password → `telnet123`
- Enter `enable` command
- Enter enable password → `admin123`

---

## 🔍 Verification Commands

```bash
R1# show running-config
R1# show line
R1# show users
```

---

## 📌 Notes

- Telnet sends data in **plain text**. For secure access, consider using **SSH** instead.
- Make sure Telnet is **enabled by default** on older devices. On newer IOS versions, you may need to manually enable it.

---
