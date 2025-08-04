# Static Router Configuration : 

### Router0
```bash
Press RETURN to get started!
Router>en
Router#cont t
Router#conf t
Router(config)#int gig0/0
Router(config-if)#no shut
Router(config-if)#ip add 192.168.10.1 255.255.255.0
Router(config-if)#exit
Router(config)#int se0/1/0
Router(config-if)#no shut
Router(config-if)#ip add 100.10.0.1 255.255.255.0
Router(config-if)#exit
Router(config)#

Router(config)#ip dhcp pool aaa
Router(dhcp-config)#network 192.168.10.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.10.1
Router(dhcp-config)#dns-server 8.8.8.8
Router(dhcp-config)#ip route 192.168.11.0 255.255.255.0 100.10.0.2
Router(config)#ip route 192.168.12.0 255.255.255.0 100.10.0.2

Router#copy run start
Destination filename [startup-config]? 
Building configuration...
[OK]
Router#reload
```
Diagram : 

<img width="1681" height="684" alt="Image" src="https://github.com/user-attachments/assets/548cb785-84f3-4aab-a2c8-fd59da1bb114" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/10adb923-610c-4c8e-99b7-99a8a7b5bdc6" />
<img width="712" height="844" alt="Image" src="https://github.com/user-attachments/assets/222d71c7-05ad-45ae-93f4-732e8fd4284e" />


### Router1
```bash 
Router1
Router>en
Router#conf t
Router(config)#int gig0/0
Router(config-if)#no shut
Router(config-if)#ip add 192.168.11.1 255.255.255.0
Router(config-if)#exit
Router(config)#int se0/1/0
Router(config-if)#no shut
Router(config-if)#ip add 100.10.0.2 255.255.255.0
Router(config-if)#exit
Router(config)#int se0/1/1
Router(config-if)#no shut
Router(config-if)#ip add 200.20.0.1 255.255.255.0
Router(config-if)#exit
Router(config)#ip dhcp pool bbb
Router(dhcp-config)#network 192.168.11.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.11.1
Router(dhcp-config)#dns-server 8.8.8.8
Router(dhcp-config)#exit
Router(config)#ip route 192.168.10.0 255.255.255.0 100.10.0.1
Router(config)#ip route 192.168.12.0 255.255.255.0 200.20.0.2
Router(config)#exit
Router#copy run star
Destination filename [startup-config]? 
Building configuration...
[OK]
Router#copy run start
Destination filename [startup-config]? 
Building configuration...
[OK]

```
Diagram : 

<img width="721" height="997" alt="Image" src="https://github.com/user-attachments/assets/92e32337-1801-436b-a7b5-c1ca479f7744" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/0b41b9bc-7e2c-44bd-a942-63c980394a54" />

### Router2
```bash
Press RETURN to get started!
Router>en
Router#conf t
Router(config)#int gig0/0
Router(config-if)#no shut
Router(config-if)#ip add 192.168.12.1 255.255.255.0
Router(config-if)#exit
Router(config)#int se0/1/0
Router(config-if)#no shut
Router(config-if)#ip add 200.20.0.2 255.255.255.0
Router(config-if)#exit
Router(config)#ip dhcp pool ddd
Router(dhcp-config)#network 192.168.12.0 255.255.255.0
Router(dhcp-config)#default-router 192.168.12.1
Router(dhcp-config)#dns
Router(dhcp-config)#dns-server 8.8.8.8
Router(dhcp-config)#exit
Router(config)#ip route 192.168.11.0 255.255.255.0 200.20.0.1
Router(config)#ip route 192.168.10.0 255.255.255.0 200.20.0.1
Router(config)#exit
Router#copy run start
Destination filename [startup-config]? 
Building configuration...
[OK]


```

Diagram : 

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/ff1d66fe-18f5-422a-a9a2-a7aae44a09d6" />
<img width="721" height="997" alt="Image" src="https://github.com/user-attachments/assets/2fca1262-b2b7-4c9a-801b-aae2857ecf2b" />