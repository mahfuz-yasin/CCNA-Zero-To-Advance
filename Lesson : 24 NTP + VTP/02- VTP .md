
# 🔄 VTP (VLAN Trunking Protocol) Configuration Guide

This guide explains how to configure **VTP**, a Cisco protocol that allows automatic distribution of VLAN information across switches.

---

## 📘 What is VTP?

**VTP (VLAN Trunking Protocol)** is a Cisco proprietary protocol used to synchronize VLAN information (IDs and names) between switches within the same VTP domain.

---

## 🧠 Why Use VTP?

* Reduces VLAN configuration workload
* Ensures VLAN consistency across large switch networks
* Prevents manual VLAN mismatches

---

## 🧪 VTP Modes

Each switch can operate in one of the following modes:

| Mode              | Description                                                                   |
| ----------------- | ----------------------------------------------------------------------------- |
| **Server**        | Default mode. Can create, delete, and propagate VLANs.                        |
| **Client**        | Cannot create/delete VLANs. Receives and processes VLAN updates.              |
| **Transparent**   | Doesn’t share VLAN info but forwards VTP updates. Local VLANs can be created. |
| **Off** *(VTPv3)* | Similar to Transparent but does **not** forward VTP messages.                 |

---

## 🖼️ Example Network

3 switches connected:

* **SW1** – VTP Server
* **SW2** – VTP Transparent
* **SW3** – VTP Client

If VLAN 5 is created on SW1:

* SW2 (Transparent): does **not** create VLAN but **forwards** VTP update.
* SW3 (Client): **creates** VLAN 5 from VTP update.

---

## ⚙️ Requirements for VTP Communication

1. At least one switch must be **Server** or **Client** mode.
2. All switches must have the **same VTP domain name**.
3. If set, the **same VTP password** must be used.
4. All switches must use the **same VTP version**.
5. Links between switches must be **trunk ports**.

---

## 🛠️ Configuration Example

### 🔧 SW1 (Server)

```bash
SW1(config)# vtp domain ccna
SW1(config)# vtp password cisco
```

### 🔧 SW2 (Client)

```bash
SW2(config)# vtp mode client
SW2(config)# vtp domain ccna
SW2(config)# vtp password cisco
```

### 🔧 SW3 (Client)

```bash
SW3(config)# vtp mode client
SW3(config)# vtp domain ccna
SW3(config)# vtp password cisco
```

---

## ✅ Testing

When VLAN 5 is created on **SW1**:

```bash
SW1(config)# vlan 5
```

* **SW2** (transparent): does **not** create VLAN 5, but forwards the update.
* **SW3** (client): automatically creates VLAN 5.


## ⚙️ How to Configure a Trunk Port
🔧 Example on Switch interface FastEthernet 0/1:
```bash
Switch(config)# interface fastEthernet 0/1
Switch(config-if)# switchport mode trunk
Switch(config-if)# switchport trunk encapsulation dot1q
```
