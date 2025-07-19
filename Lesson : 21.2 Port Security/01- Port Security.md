# 🔒 Port Security Configuration & Testing (Cisco Switch)

This guide helps you configure and verify **Port Security** on Cisco switches to restrict access and protect your network.

---

## ✅ What is Port Security?

Port Security is a feature that allows a switch to **restrict input** to an interface by **limiting and identifying MAC addresses**. It helps prevent unauthorized devices from connecting.

> 🔐 **বাংলায়**: Port Security মানে সুইচে নিরাপত্তা ব্যবস্থা চালু করা, যাতে কোনো **অননুমোদিত ডিভাইস** সুইচে সংযুক্ত হতে না পারে।

---

## 🚦 Port Security Modes

| Mode        | Behavior                                                                 |
|-------------|--------------------------------------------------------------------------|
| `protect`   | Silently drops packets from unknown MAC addresses.                       |
| `restrict`  | Drops packets and logs the violation.                                    |
| `shutdown`  | Disables the port completely upon a violation (default mode).            |

---

## ⚙️ Configuration Steps

### 1️⃣ Basic Switch Setup

```bash
Switch> enable
Switch# configure terminal
Switch(config)# hostname S1
S1(config)# interface FastEthernet0/1
S1(config-if)# switchport mode access
S1(config-if)# switchport port-security
```

---

### 2️⃣ Configure Port Security Parameters

```bash
S1(config-if)# switchport port-security maximum 1
S1(config-if)# switchport port-security violation restrict
S1(config-if)# switchport port-security mac-address sticky
S1(config-if)# exit
```

🔎 Explanation:
- `maximum 1`: Only 1 MAC address allowed.
- `violation restrict`: Logs and drops packets from unknown MACs.
- `mac-address sticky`: Learns and stores the first MAC address dynamically.

---

### 3️⃣ Assign IP to PC (e.g., PC1)

🖥️ Example:
- IP: `192.168.1.10`
- Subnet Mask: `255.255.255.0`
- Gateway: `192.168.1.1`

---

## 🔍 Verify Configuration

```bash
S1# show port-security
S1# show port-security interface FastEthernet0/1
S1# show mac address-table
S1# show port-security address
```

---

## 🧪 Test Port Security

### Scenario:
1. Connect **PC1** to `FastEthernet0/1` – connection should work.
2. Replace PC1 with **PC2** (different MAC) – port reacts based on violation mode.

### Results Based on Mode:

| Mode        | Behavior When PC2 Connects                        |
|-------------|---------------------------------------------------|
| `protect`   | Drops traffic silently (no log shown).            |
| `restrict`  | Drops traffic + logs violation messages.          |
| `shutdown`  | Port is disabled and goes to `err-disabled`.      |

---

## 📋 Check Violation Logs

```bash
S1# show log
```

🔍 Look for messages like:
```
%PORT_SECURITY-2-PSECURE_VIOLATION: Security violation occurred...
```

---

## ⚠️ If Port Goes Down (Shutdown Mode)

### Check Port Status

```bash
S1# show interface status
```

You will see the interface in `err-disabled` state.

### Recover from Violation

```bash
S1(config)# interface FastEthernet0/1
S1(config-if)# shutdown
S1(config-if)# no shutdown
```

---

## 💡 Summary of Useful Commands

| Command                                  | Description                                 |
|------------------------------------------|---------------------------------------------|
| `show port-security`                     | Displays summary of all secured ports       |
| `show port-security interface fa0/1`     | Detailed info for a specific port           |
| `show mac address-table`                 | Shows MAC address table                     |
| `show port-security address`             | Lists learned MAC addresses per port        |
| `show log`                               | View system logs (includes violations)      |
| `show interface status`                  | Checks interface states                     |

---

## 📌 Tips

- Use `restrict` or `protect` in real environments to avoid auto shutdowns.
- Save the config using:
```bash
S1# copy running-config startup-config
```
- Regularly monitor port activity with:
```bash
S1# show port-security
``‌‌‌`