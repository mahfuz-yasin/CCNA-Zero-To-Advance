![CLI Banner](https://github.com/user-attachments/assets/1d2e8ae4-c880-4226-b121-fd342cca9cb2)

# 🧠 CyberSecurity & Ethical Hacking
## 🎯 CLI (Command Line Interface) - Step-by-Step Guide for Networking

---

### 🔸 CLI কী?

**CLI** বা **Command Line Interface** হলো একটি ইন্টারফেস যেখানে ব্যবহারকারী কী-বোর্ড দিয়ে কমান্ড টাইপ করে ডিভাইসের সাথে যোগাযোগ করে। এটি গ্রাফিকাল ইন্টারফেস (GUI)-এর বিপরীতে, যেখানে মাউস ব্যবহার করে কাজ করা হয়।

👉 CLI-এর মাধ্যমে আপনি নেটওয়ার্ক ডিভাইস যেমন: **Router**, **Switch**, **Firewall** ইত্যাদির কনফিগারেশন, ট্রাবলশুটিং এবং মনিটরিং করতে পারেন।

---

### 🔸 CLI এর ব্যবহার কোথায় হয়?

- ✅ **Cisco Router ও Switch কনফিগার করতে**
- ✅ **Linux Server পরিচালনায়**
- ✅ **Windows CMD বা PowerShell-এ কাজ করতে**
- ✅ **Python বা অন্যান্য প্রোগ্রামিং টুলস চালাতে**
- ✅ **Network ট্রাবলশুটিং-এ (ping, traceroute, netstat)**

---

### 🔸 CLI এর সুবিধা

| সুবিধা                   | ব্যাখ্যা                                               |
|--------------------------|--------------------------------------------------------|
| ✅ দ্রুত কাজ করা যায়      | GUI অপেক্ষা CLI অনেক দ্রুত এবং স্ক্রিপ্টিং সুবিধা দেয়   |
| ✅ সম্পূর্ণ নিয়ন্ত্রণ     | CLI দিয়ে ডিভাইসের প্রতিটি সেটিংস কাস্টমাইজ করা যায়    |
| ✅ কম রিসোর্স ব্যবহার করে | GUI তুলনায় কম CPU ও RAM লাগে                           |
| ✅ অটোমেশন সহজ হয়        | CLI দিয়ে স্ক্রিপ্ট লিখে অটোমেশন করা যায় (Bash, Python) |

---

### 🔸 Cisco CLI Mode গুলো

| Mode                 | CLI Prompt              | কাজ                                                   |
|----------------------|-------------------------|--------------------------------------------------------|
| **User Exec Mode**   | `Router>`               | সীমিত কমান্ড চালানো যায় (show, ping)                  |
| **Privileged Mode**  | `Router#`               | সব show ও debug কমান্ড, config mode-এ যাওয়ার সুযোগ    |
| **Global Config**    | `Router(config)#`       | ডিভাইস কনফিগারেশন করার জন্য                           |
| **Interface Config** | `Router(config-if)#`    | নির্দিষ্ট interface কনফিগার করতে                      |
| **Line Config**      | `Router(config-line)#`  | Console / VTY port কনফিগার করতে                       |

---

### 🎨 Quick Design Tip in Packet Tracer

> ⌨️ **CTRL + Click**: একাধিক ডিভাইস বা কেবল একসাথে নির্বাচন করতে  
> 🛠️ দ্রুত ডায়াগ্রাম ডিজাইন ও ম্যানেজমেন্টে কার্যকর  

---

### 🔧 Useful CLI Keyboard Shortcuts (Cisco IOS)

| শর্টকাট           | কাজ/ব্যাখ্যা                                           |
|-------------------|-------------------------------------------------------|
| `↑` (Up Arrow)    | আগের লেখা কমান্ড দেখতে                                |
| `↓` (Down Arrow)  | পরবর্তী কমান্ড দেখতে                                  |
| `Tab`             | অটো-কমপ্লিট (কমান্ড টাইপ করার সময়)                   |
| `?`               | হেল্প — বর্তমান অবস্থায় কোন কমান্ড দেয়া যায় তা দেখায় |
| `CTRL + A`        | লাইন শুরুর দিকে যেতে                                 |
| `CTRL + E`        | লাইন শেষে যেতে                                       |
| `CTRL + U`        | পুরো লাইন মুছে ফেলা                                   |
| `CTRL + W`        | শেষ শব্দটা মুছে ফেলা                                  |
| `CTRL + Z`        | Config Mode থেকে Privileged Mode-এ ফিরে যাওয়া        |
| `CTRL + C`        | চলমান কমান্ড বা প্রসেস বন্ধ করা                      |

---

### 🔸 উদাহরণ কমান্ড

```bash
Router> enable                    # Privileged Mode-এ যাও
Router# configure terminal        # Global Config Mode
Router(config)# interface g0/0
Router(config-if)# ip address 192.168.1.1 255.255.255.0
Router(config-if)# no shutdown
Router(config-if)# exit
Router(config)# exit
Router# show ip interface brief  # সব ইন্টারফেসের সারসংক্ষেপ দেখায়
```
📚 CLI শেখার জন্য সুপারিশকৃত টুলস
🖥 Cisco Packet Tracer (Simulation)

🧪 GNS3 / EVE-NG (Advanced Virtual Labs)

🧠 Cisco CCNA Course Module

📄 Cisco CLI Command Cheat Sheet (PDF/Printable)

📌 নোট: CLI শেখা শুধু নেটওয়ার্কিং নয়, Linux Administration, Cloud Security, ও Ethical Hacking এর ভিত্তি গড়তেও অপরিহার্য।