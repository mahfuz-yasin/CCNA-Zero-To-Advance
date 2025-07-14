# Static Routing between two Routers
- steps :
    - Basic Configuration
    - IP Address Assign to PC
    - Static Routing Configure
    - Verify Static Route
==============: 

# **Router 0**
    - Network Address : 192.168.10.0/24
    - Default Gateway : 192.168.10.1
    - Subnet Mask : 255.255.255.0
    - second Interface Network address : 100.0.0.0/24
    - Remote Network: 192.168.20.0/24
    - Next hop Address : 100.0.0.2
## Basic Configuration :
    Router> en
    Router# conf t
    Router(config)# int gig0/0
    Router(config-if)# ip address 192.168.10.1 255.255.255.0
    Router(config-if)# no shutdown
   
    Router(config)# int se0/1/0
    Router(config-if)# no shutdown
    Router(config-if)# ip address 100.0.0.1 255.255.255.0

## IP Address Assign to pc (Dynamically)
    Router(config)# ip dhcp pool IT
    Router(dhcp-config)# network 192.168.10.0 255.255.255.0
    Router(dhcp-config)# default-router 192.168.10.1
    Router(dhcp-config)# dns-server 8.8.8.8
    Router(dhcp-config)# exit

## Static Routing Configuration :
    Router(config)# ip route 192.168.20.0 255.255.255.0 100.0.0.2



# **Router 1**
- Network Address : 192.168.20.0/24
- Default Gateway : 192.168.20.1
- Subnet Mask : 255.255.255.0
- second Interface Network address : 100.0.0.0/24
- Remote Network: 192.168.10.0/24
- next hop Address : 100.0.0.1
## Basic Configuration :
    Router> en
    Router# conf t
    Router(config)# int gig0/0
    Router(config-if)# no shutdown
    Router(config-if)# ip address 192.168.20.1 255.255.255.0

    Router(config)# int se0/0/0
    Router(config-if)# no shutdown
    Router(config-if)# ip address 100.0.0.2 255.255.255.0

## IP Address Assign to pc (Dynamically)
    Router(config)# ip dhcp pool Sales
    Router(dhcp-config)# network 192.168.20.0 255.255.255.0
    Router(dhcp-config)# default-router 192.168.20.1
    Router(dhcp-config)# dns-server 8.8.8.8
    Router(dhcp-config)# exit

## Static Routing Configuration :
    Router(config)# ip route 192.168.10.0 255.255.255.0 100.0.0.1

## Verification :
    Router# show ip route
    Router# show ip protocols
    Router# ping 192.168.20.x (or 192.168.10.x)

