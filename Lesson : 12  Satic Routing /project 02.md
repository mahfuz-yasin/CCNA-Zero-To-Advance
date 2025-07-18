
## 🔁 Static Routing Between Three Routers

To configure static routing in a three-router network, follow these step-by-step instructions:

### ✅ Steps:

1. ### **Basic Configuration**

   * Enable all necessary router interfaces.
   * Assign IP addresses to each interface.
     ```bash
     Router(config)# interface interface_name  
     Router(config-if)# ip address Default_Gateway Subnet_Mask 
     Router(config-if)# no shutdown
     ```
     * Example:
     ```
     Router(config)# interface Gig0/0  
     Router(config-if)# ip address 10.0.0.1 255.255.255.0  
     Router(config-if)# no shutdown

2. ### **IP Address Assign to PCs**

   * Manually or dynamically (using DHCP) assign:

     * **IP Address**
     * **Subnet Mask**
     * **Default Gateway**
   * Example (manual setup on PC):

     ```
     IP Address: 192.168.1.10  
     Subnet Mask: 255.255.255.0  
     Default Gateway: 192.168.1.1
     ```
    * Example (dynamically (using DHCP) setup on PC):
    ``` 
    * step-1
    - Go to Router and create pool
        Router(config)# ip dhcp pool IT
        Router(dhcp-config)# network 192.168.10.0 255.255.255.0
        Router(dhcp-config)# default-router 192.168.10.1
        Router(dhcp-config)# dns-server 8.8.8.8
        Router(dhcp-config)# exit
    * step- 2
        - Go to each pc and active DHCP

3. ### **Static Routing Configuration**

   * Add static routes to each router manually using the following syntax:

     ```bash
     ip route [destination_network] [subnet_mask] [next_hop_IP or exit_interface]
     ```
   * Example:

     ```bash
     Router(config)# ip route 192.168.3.0 255.255.255.0 10.0.0.2
     ```
   * Repeat for all routers to ensure full network reachability.

4. ### **Verify Static Route**

   * Use the following commands to verify routing functionality:

     ```bash
     Router# ping [destination_IP]  
     Router# traceroute [destination_IP]  
     Router# show ip route
     ```
   * Confirm successful communication between all network devices.

---

### 📝 Note:

> Without static routes, routers will not know how to reach networks they are not directly connected to. Proper configuration ensures end-to-end connectivity in the network.



## 🔧 Important Steps **Before** Routing Configuration

To ensure proper network topology and device connectivity, follow these essential steps **before** configuring routing:

1. **Device Setup:**

   * Prepare **three routers**.
   * Connect **three PCs to each router** (total 9 PCs).

2. **Router-to-Router Connection:**

   * Use a **serial cable** or **crossover cable** to connect one router to another.

3. **Router-to-Switch and Switch-to-PC Connection:**

   * Use a **straight-through cable** to connect:

     * Each **router to a switch**
     * Each **switch to its corresponding PCs**

---

### 📝 Note:

> These hardware connections must be completed before starting routing configuration. A correct physical setup ensures successful network communication and routing. 

# Diagram of Project : 
<img width="1427" height="626" alt="Image" src="https://github.com/user-attachments/assets/3aae7a9b-9cd9-48d6-835e-3e37af6d8b42" />


## ⚙️ Static Routing Configuration – Three Routers (with DHCP)

---

### 🛠️ **Router 0 Configuration**

```bash
Router>en
Router#conf t
Router(config)#int gig0/0	
Router(config-if)#ip address 192.168.10.1 255.255.255.0
Router(config-if)#no shut

Router(config-if)#int se0/3/0
Router(config-if)#ip address 100.50.10.1 255.255.255.0
Router(config-if)#no shut
Router(config-if)#exit

# DHCP Configuration
Router(config)#ip dhcp pool aaa
Router(dhcp-config)#network 192.168.10.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.10.1
Router(dhcp-config)#dns-server 8.8.8.8
Router(dhcp-config)#exit

# Static Routes
Router(config)#ip route 192.168.20.0 255.255.255.0 100.50.10.2
Router(config)#ip route 192.168.30.0 255.255.255.0 100.50.10.2
```

---

### 🛠️ **Router 1 Configuration**

```bash
Router>en
Router#conf t
Router(config)#int gig0/0
Router(config-if)#ip address 192.168.20.1 255.255.255.0
Router(config-if)#no shut

Router(config-if)#int se0/2/0
Router(config-if)#ip address 100.50.10.2 255.255.255.0
Router(config-if)#no shut
Router(config-if)#exit

# DHCP Configuration
Router(config)#ip dhcp pool bbb
Router(dhcp-config)#network 192.168.20.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.20.1
Router(dhcp-config)#dns-server 8.8.8.8
Router(dhcp-config)#exit

# Connect to Router 2
Router(config)#int se0/2/1
Router(config-if)#ip address 200.40.50.1 255.255.255.0
Router(config-if)#no shut
Router(config-if)#exit

# Static Routes
Router(config)#ip route 192.168.10.0 255.255.255.0 100.50.10.1
Router(config)#ip route 192.168.30.0 255.255.255.0 200.40.50.2
```

---

### 🛠️ **Router 2 Configuration**

```bash
Router>en
Router#conf t
Router(config)#int gig0/0
Router(config-if)#ip address 192.168.30.1 255.255.255.0
Router(config-if)#no shut

Router(config-if)#int se0/1/0
Router(config-if)#ip address 200.40.50.2 255.255.255.0
Router(config-if)#no shut
Router(config-if)#exit

# DHCP Configuration
Router(config)#ip dhcp pool ccc
Router(dhcp-config)#network 192.168.30.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.30.1
Router(dhcp-config)#dns-server 8.8.8.8
Router(dhcp-config)#exit

# Static Routes
Router(config)#ip route 192.168.20.0 255.255.255.0 200.40.50.1
Router(config)#ip route 192.168.10.0 255.255.255.0 200.40.50.1
```