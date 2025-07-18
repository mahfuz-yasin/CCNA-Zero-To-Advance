# project 01

- Steps : 
-       basic configuration
-       set all types of password 
-       verify
-       save password in CLI
-       reload
-       check 

## **Router 0**

### basic configuration :
```bash 
    Router(config)# en
    Router(config)# conf t
    Router(config)# int gig0/0
    Router(config-if)# ip add 192.168.10.1 255.255.255.0
    Router(config-if)# no shut
    Router(config)#exit
```

### set all types of password
```bash
    Router(config)# enable password 1234
    Router(config)# enable secret admin123

    Router(config)# line console 0
    Router(config-line)# password c0ns0le123
    Router(config-line)# login
    Router(config-line)# exit

    Router(config)# line aux 0
    Router(config-line)# password aux123
    Router(config-line)# login
    Router(config-line)# exit

    Router(config)# line vty 0 4
    Router(config-line)# password vty123
    Router(config-line)# login
    Router(config-line)# exit

    Router(config)# service password-encryption

    Router# show running-config

```

### verify 
``` bash 
    Router# show running-config
```

### save password in CLI
```bash
    Router# write memory
or  Router# wr
or  Router# copy running-config startup-config
or  Router# copy run start
```

### reload
```bash
    Router# reload
```
### check 
```bash
    🔐 Step 1:
    User Access Verification
    Password: put here console password

    🔐 Step 2:
    Router> enable
    Password: put here plain text password or secret password

    🔐 Step 3: 
     Password: aux / console/ vty password

```