# <span style="color:gold; font-size:1.8rem ;">VLAN configuration between multiple switches : </span>

# Switch : 01
## Group: Admin
### **step: 01**
- open CLI after click on switch
- enable
- configur termianl
- vlan uniqeIdNumber (example: vlan 2)
- name VlanName (example : name Admin)
- exit

### **step: 02**
- selec interface and implement VLAN on interface
- int fa0/1 (single network device)
- int range fa0/1-2 (multiple network devices by written "range")
- switchport mode access
- switchport access vlan IdNumber
- exit
- **step: 03**
- Got to privileged mode and verify
- show vlan brief

# Group: Sales
### **step: 01**
- open CLI after click on switch
- enable
- configur termianl
- vlan uniqeIdNumber (example: vlan 2)
- name VlanName (example : name Admin)
- exit

### **step: 02**
- selec interface and implement 
- int fa0/1 (single network device)
- int fa0/3-4 (multiple network devices)
- switchport mode access
- switchport access vlan IdNumber
- exit
- **step: 03**
- Got to privileged mode and verify
- show vlan brief




# Switch : 02
## Group: Admin
### **step: 01**
- open CLI after click on switch
- enable
- configur termianl
- vlan uniqeIdNumber (example: vlan 2)
- name VlanName (example : name Admin)
- exit

### **step: 02**
- selec interface and implement VLAN on interface
- int fa0/1 (single network device)
- int range fa0/1-2 (multiple network devices by written "range")
- switchport mode access
- switchport access vlan IdNumber
- exit
- **step: 03**
- Got to privileged mode and verify
- show vlan brief

# Group: Sales
### **step: 01**
- open CLI after click on switch
- enable
- configur termianl
- vlan uniqeIdNumber (example: vlan 2)
- name VlanName (example : name Admin)
- exit

### **step: 02**
- selec interface and implement 
- int fa0/1 (single network device)
- int fa0/3-4 (multiple network devices)
- switchport mode access
- switchport access vlan IdNumber
- exit
- **step: 03**
- Got to privileged mode and verify
- show vlan brief

# Trunk command in switch 1 or switch 2
- int fa0/5
- switchport mode trunk

# **Project 01 All images step by step**

<img width="1560" height="630" alt="Image" src="https://github.com/user-attachments/assets/dcdd88e1-d088-442c-92f1-2651e34d4c72" />
<img width="703" height="940" alt="Image" src="https://github.com/user-attachments/assets/01912fcc-95ab-4a36-b5c5-6ff47d227a3b" />
<img width="703" height="790" alt="Image" src="https://github.com/user-attachments/assets/83519422-c691-4f3a-a64a-2a3d6bbcd982" />
<img width="688" height="685" alt="Image" src="https://github.com/user-attachments/assets/3e7be797-0227-4718-875d-46bd196625f8" />
<img width="688" height="685" alt="Image" src="https://github.com/user-attachments/assets/1ca6faac-0931-4355-bf4e-4215806f4867" />
<img width="688" height="685" alt="Image" src="https://github.com/user-attachments/assets/557c479e-1929-4717-a41f-db6f7a31dd17" />
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/fccfb83f-737e-4699-adc8-b2b679712679" />

# <h1>project 02 Ended Here <h1>