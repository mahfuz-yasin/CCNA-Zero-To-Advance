# Password Break and Recovery
**Steps**: 
-   password setup
-   password break and Recovery

## password setup 
1.  Admin mode password (plain text)
    ```
    enable
    conf t
    enable password 123
    save or save after all types of setup password
    reload or reload after all types of password setup

2.   Admin mode password (encrypted password)
    ``` 
    enable
    conf t
    enable password secret 1234
    save or save after all types of setup 
    password
    reload or reload after all types of 
    password setup

3. console password 
    ```
    line con 0
    password ccna
    login
4. auxiliary port password
    ```
    line aux 0
    password ccna
    login
5. vty port password
    ``` 
    line vty 0 4 
    password 
    login
### Verify 
    ```
    show running-config

**Save All Passwords**
    ```
-     copy running-config startup-config
-     copy run start
-     write 
-     wr


**Reload after all password setupe**

## password break and Recovery
