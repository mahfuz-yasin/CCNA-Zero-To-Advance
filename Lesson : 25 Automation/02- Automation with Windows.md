**Windows ব্যবহার করে Network Automation (Telnet + Python Script + GNS3 Router)** 

## ✅ **Network Automation on Windows — Step-by-Step Full Guide**

---

### 🛠️ প্রয়োজনীয় সফটওয়্যার ও টুলস:

1. **GNS3** – টপোলজি তৈরির জন্য
2. **Loopback Interface Manager** – PC ↔ Router কানেকশন
3. **Python (v3.x)** – অটোমেশন স্ক্রিপ্টের জন্য
4. **Notepad++** – কোড লেখার জন্য
5. **PowerShell / CMD** – স্ক্রিপ্ট রান করার জন্য

---

### 🪜 **Step-by-Step Configuration**

---

### 🔁 1. **Loopback Interface Setup (GNS3 ↔ PC connectivity)**

#### ✅ Step 1: Run CMD as Administrator

```bash
cd "C:\Program Files\GNS3"
```

#### ✅ Step 2: Run this command

```bash
sc config npf start= auto
```

#### ✅ Step 3: Launch Loopback Manager

```bash
Loopback-manager.cmd
```

👉 তারপর নিচের অপশনগুলো নির্বাচন করুন:

* 4 → Remove all existing loopback interfaces
* 2 → Install new loopback interface
* 6 → Quit

#### ✅ Step 4: PC Reboot দিন

---

### 🌐 2. **Loopback Interface IP Configuration**

#### Control Panel → Network and Sharing Center → Change Adapter Settings

Loopback Interface-এ রাইট ক্লিক → Rename (e.g., Loop1) → Properties → IPv4:

```plaintext
IP: 10.10.10.5
Subnet: 255.255.255.0
```

---

### 🖥️ 3. **GNS3 Configuration**

#### ✅ Create simple topology:

* 1 Router (R1)
* 1 Cloud (connect to Loopback)

#### ✅ Configure Cloud in GNS3:

1. Drag Cloud
2. Right click → Configure → Check "Show special interfaces"
3. Add the **Loopback interface**

---

### 🔧 4. **Router Configuration in GNS3 Console**

```bash
R1> enable
R1# configure terminal
R1(config)# interface fastEthernet 0/0
R1(config-if)# ip address 10.10.10.6 255.255.255.0
R1(config-if)# no shutdown

R1(config)# enable password 1234
R1(config)# username admin password 1234

R1(config)# line vty 0 4
R1(config-line)# login local
```

✅ এখন পিং করুন:

```bash
R1# ping 10.10.10.5
```

---

### 🐍 5. **Python Script তৈরি করুন (telnet দিয়ে অটোমেশন)**

#### ✅ Script লিখুন: `notepad++` বা `Visual Studio Code` ব্যবহার করুন

**net.py**:

```python
import getpass
import telnetlib

HOST = "10.10.10.6"
user = input("Enter your telnet username: ")
password = getpass.getpass()

tn = telnetlib.Telnet(HOST)

tn.read_until(b"Username: ")
tn.write(user.encode('ascii') + b"\n")
if password:
    tn.read_until(b"Password: ")
    tn.write(password.encode('ascii') + b"\n")

tn.write(b"enable\n")
tn.write(b"1234\n")
tn.write(b"conf t\n")
tn.write(b"hostname CCNA\n")
tn.write(b"int loop 0\n")
tn.write(b"ip address 1.1.1.1 255.255.255.255\n")
tn.write(b"int loop 1\n")
tn.write(b"ip address 2.2.2.2 255.255.255.255\n")
tn.write(b"router ospf 10\n")
tn.write(b"network 0.0.0.0 255.255.255.255 area 0\n")
tn.write(b"end\n")
tn.write(b"exit\n")

print(tn.read_all().decode('ascii'))
```

---

### 📁 6. **Script ও Document ফাইল একসাথে রাখুন**

উদাহরণ:

```plaintext
D:\Network Automation\net.py
D:\Network Automation\document.txt
```

---

### 💻 7. **PowerShell দিয়ে Script চালানো**

```powershell
PS C:\Users\Administrator> d:
PS D:\> cd '.\Network Automation\'
PS D:\Network Automation> python net.py
```

#### Output:

```plaintext
Enter your telnet username: admin
Password:
...
CCNA(config)#hostname CCNA
...
```

---

### 🔍 8. **রাউটারে যাচাই করুন:**

```bash
CCNA#sh ip protocols
CCNA#sh ip int brief
```

---

## 🏁 ফলাফল (Result):

✅ Router hostname পরিবর্তন হয়েছে
✅ Loopback interface সেট হয়েছে
✅ OSPF configured
✅ Telnet দিয়ে অটোমেশন সফল

---

## 📦 Bonus: Python Installation (যদি না থাকে)

ডাউনলোড লিংক: [https://www.python.org/downloads/windows/](https://www.python.org/downloads/windows/)
ইনস্টল করার সময় **Add Python to PATH** সিলেক্ট করে ইনস্টল দিন।

---

## 🧠 Note:

* Telnet ইউজ করতে গেলে Firewall allow করে নিতে হতে পারে
* Always use CMD or PowerShell as Administrator
* GNS3 এবং PC এর IP subnet একই হলে Ping হবে
