# 🌐 VLAN (Virtual LAN) Configuration Guide


## 🧠 What is VLAN?

**VLAN (Virtual LAN)** is a logical grouping of devices within the same broadcast domain, regardless of their physical location. It enables better **network segmentation**, **security**, and **flexibility**.

---

## ✅ Benefits of VLANs

- 🔁 Increase number of broadcast domains while decreasing size.
- 🔒 Improve security by isolating sensitive devices.
- 🧩 Group users by department, not by location.
- 🔧 Simplify network changes via switch port reconfiguration.

---

## 🗺️ Network Diagram



## ⚙️ Configuration Steps Overview

1. Assign VLAN ID
2. Assign VLAN Name
3. Implement VLAN on Interfaces
4. Verify VLAN
5. IP Assign in PC 

```bash
    Switch(config)# vlan unique_ID_Number
    Switch(config-vlan)# name meaningful_name
    Switch(config-vlan)# exit
then  : **Implement VLAN on Interfaces**
    Switch(config)# int range fa0/1-2
    Switch(config-if-range)# switchport mode access
    Switch(config-if-range)# switchport access vlan Vlan_Id_number
    Switch(config-if-range)# exit
then  : **Trunk command in Switch 1 or any switch (if two or more switches)**
    Switch(config)# interface fa0/1
    Switch(config-if)# switchport mode trunk
then  : Verify 
    Switch(config)# show vlan brief
then : Assign IP addresses to PCs to enable communication.
     🔹 Manually: Open the PC's network settings and assign static IP addresses.
     🔹 Dynamically: Use a DHCP server to assign IPs automatically (requires DHCP pool configuration).
```
```bash
🔔  Important Note : 

1.  VLANs work within the same VLAN group, but do not communicate with other VLAN groups unless Inter-VLAN Routing is configured.
       -----------------------------
2.   If two or more switches are used, trunk ports must be configured between them to allow VLANs from the same group to communicate. Without trunking, VLAN traffic will not pass between switches.
```

## 🔧 Switch Configuration (Step-by-Step)

### 🛠️ Switch 1 Configuration

#### ➤ VLAN 2 - Sales

```bash
Switch(config)# vlan 2
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit
Switch(config)# int range fa0/2-3
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 2
Switch(config-if-range)# exit
```

#### ➤ VLAN 3 - IT

```bash
Switch(config)# vlan 3
Switch(config-vlan)# name IT
Switch(config-vlan)# exit
Switch(config)# int range fa0/4-5
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 3
```

---

### 🛠️ Switch 2 Configuration

#### ➤ VLAN 2 - Sales

```bash
Switch(config)# vlan 2
Switch(config-vlan)# name Sales
Switch(config-vlan)# exit
Switch(config)# int range fa0/2-3
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 2
Switch(config-if-range)# exit
```

#### ➤ VLAN 3 - IT

```bash
Switch(config)# vlan 3
Switch(config-vlan)# name IT
Switch(config-vlan)# exit
Switch(config)# int range fa0/4-5
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 3
```

---

## 🔁 Trunk Configuration (Switch 1 or 2)

> Trunk port is needed for inter-switch VLAN traffic.

```bash
Switch(config)# interface fa0/1
Switch(config-if)# switchport mode trunk
```

---

## 🔍 Verification Command

```bash
Switch# show vlan brief
```

This command shows VLAN ID, names, and port assignments.

---

## 📌 Summary

| VLAN ID | Name  | Ports      |
|---------|--------|------------|
| 2       | Sales | fa0/2–3    |
| 3       | IT    | fa0/4–5    |

> Use this setup to logically separate departments in a network for better control and scalability.

---

