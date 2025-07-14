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

========================== :
Project`s images Step by Step -:
<img width="1182" height="558" alt="Image" src="https://github.com/user-attachments/assets/06b13c1e-773d-4b7e-adf9-8ae990b74009" />
<img width="699" height="924" alt="Image" src="https://github.com/user-attachments/assets/98e5fcd0-4802-4b36-929e-bae391dd4d1e" />
<img width="699" height="955" alt="Image" src="https://github.com/user-attachments/assets/c402e219-ffe6-4b01-bf07-bdbe6bd87187" />
<img width="699" height="132" alt="Image" src="https://github.com/user-attachments/assets/2e3097a6-dcf2-4356-942e-c7db4f2a6311" />
<img width="683" height="937" alt="Image" src="https://github.com/user-attachments/assets/1e2391f9-3699-4fee-8c2e-8fec028cf49d" />
<img width="683" height="937" alt="Image" src="https://github.com/user-attachments/assets/54c5f88e-b5e3-4f14-963a-58926727206e" />
<img width="1245" height="875" alt="Image" src="https://github.com/user-attachments/assets/c2e11927-30c7-4724-9658-0fe2a0481df4" />
<img width="1252" height="870" alt="Image" src="https://github.com/user-attachments/assets/eae13efb-e1dd-4a5a-b7a7-4afb35a88daa" />
<img width="729" height="870" alt="Image" src="https://github.com/user-attachments/assets/d028ebf5-c2d0-4738-ad08-6c37de04bdfc" />
<img width="730" height="924" alt="Image" src="https://github.com/user-attachments/assets/bbee49e6-ae5b-46f9-b1be-aa12ec8eb49a" />