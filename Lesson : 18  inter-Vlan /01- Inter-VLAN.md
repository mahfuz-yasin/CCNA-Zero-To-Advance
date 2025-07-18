# 🔁 Inter-VLAN Routing Configuration Guide

## 🧠 What is Inter-VLAN Routing?

**Inter-VLAN Routing** is the process of forwarding network traffic between VLANs using a **Layer 3 device (Router)**. While VLAN trunks allow communication between the same VLAN across multiple switches, Inter-VLAN allows different VLANs (e.g., VLAN 2 and VLAN 3) to communicate with each other through a router.

---
## Steps :
-   Basic Configuration
-   VLAN Configure in Switches
-   Inter-Vlan Configure in Router
-   Verify 


## 🗺️ Network Topology Diagram

## 🛠️ Step-by-Step Configuration

### 1️⃣ Basic VLAN Configuration on Switches

> Configure **VLAN 2 (Sales)** and **VLAN 3 (IT)** on both switches.

#### 🔧 Switch 1:

```bash
Switch(config)# vlan 2
Switch(config-vlan)# name Sales
Switch(config)# int range fa0/2-3
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 2

Switch(config)# vlan 3
Switch(config-vlan)# name IT
Switch(config)# int range fa0/4-5
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 3
```

#### 🔧 Switch 2:

```bash
Switch(config)# vlan 2
Switch(config-vlan)# name Sales
Switch(config)# int range fa0/2-3
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 2

Switch(config)# vlan 3
Switch(config-vlan)# name IT
Switch(config)# int range fa0/4-5
Switch(config-if-range)# switchport mode access
Switch(config-if-range)# switchport access vlan 3
```

---

### 2️⃣ Configure Trunk Ports

> Enable trunking on the uplink port (connecting switch to router or another switch).

```bash
Switch(config)# interface fa0/6
Switch(config-if)# switchport mode trunk
```

> If trunking between Switch 1 and Switch 2:
```bash
Switch(config)# interface <uplink-port>
Switch(config-if)# switchport mode trunk
```

---
### 3️⃣ 
then : Assign IP addresses to PCs to enable communication.
     🔹 Manually: Open the PC's network settings and assign static IP addresses.
     🔹 Dynamically: Use a DHCP server to assign IPs automatically (requires DHCP pool configuration).

### 4️⃣ Configure Router-on-a-Stick (Router Subinterfaces)

> Configure subinterfaces for each VLAN with encapsulation and IP addressing.

```bash
Router(config)# interface gig0/0
Router(config-if)# no shutdown
Router(config-if)# exit

Router(config)# interface gig0/0.1
Router(config-subif)# encapsulation dot1q 2
Router(config-subif)# ip address 192.168.10.1 255.255.255.0
Router(config-subif)# no shutdown
Router(config-subif)# exit

Router(config)# interface gig0/0.2
Router(config-subif)# encapsulation dot1q 3
Router(config-subif)# ip address 192.168.11.1 255.255.255.0
Router(config-subif)# no shutdown
Router(config-subif)# exit
```

---

### 5️⃣ ✅ Verification

> Ping between devices on different VLANs:
- From PC in VLAN 2 → PC in VLAN 3
- Check default gateways are set:
  - VLAN 2: `192.168.10.1`
  - VLAN 3: `192.168.11.1`

Use the following commands:

```bash
Switch# show vlan brief
Switch# show interfaces trunk

Router# show ip interface brief
Router# ping 192.168.11.X
Router# show running-config
Router# show interfaces g0/0.1
Router# show interfaces g0/0.2

```

---

## 🎯 Summary

| VLAN | Name  | IP Gateway        |
|------|-------|-------------------|
| 2    | Sales | 192.168.10.1/24   |
| 3    | IT    | 192.168.11.1/24   |

✅ Devices in different VLANs can now communicate via the router using subinterfaces.

---

🛡️ **Tip**: Always make sure that:
- Trunk ports are properly set.
- Correct VLAN IDs are used in encapsulation.
- IP addresses are correctly assigned and not overlapping.

---
