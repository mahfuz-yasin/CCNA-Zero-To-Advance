
## 🔧 Network Automation with Python (on **Linux**) — Step by Step Guide:

---

### 🧰 প্রয়োজনীয় টুলস:

1. Python (≥ 3.x)
2. GNS3 (Linux version)
3. net-tools / iproute2
4. `telnetlib` module (Python built-in)
5. Notepad++ এর পরিবর্তে: `gedit`, `nano`, `vim` বা `VS Code`
6. Optional: Loopback interface (for simulating connection)

---

### 🪜 Step-by-Step (Linux Version):

#### ✅ 1. **Python Install আছে কিনা চেক করুন**:

```bash
python3 --version
```

যদি না থাকে:

```bash
sudo apt update
sudo apt install python3 python3-pip
```

---

#### ✅ 2. **GNS3 ইনস্টলেশন (যদি আগে না থাকে)**:

[Official Docs](https://docs.gns3.com/docs/getting-started/installation/linux/)

```bash
sudo add-apt-repository ppa:gns3/ppa
sudo apt update
sudo apt install gns3-gui gns3-server
```

---

#### ✅ 3. **GNS3-তে Loopback Interface তৈরি (Linux Equivalent):**

Linux-এ Loopback Interface তৈরি করতে:

```bash
sudo ip tuntap add dev lo1 mode tap
sudo ip addr add 10.10.10.5/24 dev lo1
sudo ip link set lo1 up
```

> আপনি চাইলে `tunctl` বা `ip tuntap` দিয়ে simulate করতে পারেন।

---

#### ✅ 4. **GNS3 Topology তৈরি করুন**:

* Cloud ↔ Router
* Cloud এ loopback interface `lo1` সিলেক্ট করুন

---

#### ✅ 5. **Router Configuration (GNS3 এর Console থেকে)**:

```bash
Router> enable
Router# config t
Router(config)# interface fastEthernet 0/0
Router(config-if)# ip address 10.10.10.6 255.255.255.0
Router(config-if)# no shutdown
Router(config)# enable password 1234
Router(config)# username admin password 1234
Router(config)# line vty 0 4
Router(config-line)# login local
```

---

#### ✅ 6. **Python Script তৈরি করুন**:

একটি ফাইল খুলুন: `nano net.py`

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

#### ✅ 7. **Script রান করুন (Linux Terminal):**

```bash
python3 net.py
```

---

### 📋 ফলাফল যাচাই:

Router Console এ গিয়ে:

```bash
CCNA#sh ip protocols
CCNA#sh ip int brief
```

---

## 🧠 Tips:

* আপনি চাইলে SSH দিয়েও অটোমেশন করতে পারেন (telnet এর বদলে `paramiko`)
* Ansible, NETCONF, RESTCONF ব্যবহার করতে চাইলে pip দিয়ে module ইনস্টল করতে হবে
* Linux-এ `NetworkManager` বা `systemd`-based interface configuration হতে পারে – সতর্ক থাকতে হবে

---

