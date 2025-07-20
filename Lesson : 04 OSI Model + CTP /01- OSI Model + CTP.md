# 🌐 OSI Model (Open Systems Interconnection Model) - সম্পূর্ণ বাংলা গাইড

OSI মডেল হলো একটি স্ট্যান্ডার্ড নেটওয়ার্ক মডেল যা ডাটা এক ডিভাইস থেকে আরেক ডিভাইসে পাঠানোর প্রক্রিয়াকে **৭টি স্তর (Layer)**-এ ভাগ করে ব্যাখ্যা করে। এটি **ISO (International Organization for Standardization)** দ্বারা প্রস্তাবিত।

---

## 📚 OSI Model-এর ৭টি স্তর

| স্তর | নাম (বাংলায়)              | কাজ |
|------|----------------------------|------|
| 7️⃣ | Application Layer           | ইউজারের সরাসরি ইন্টারফেস |
| 6️⃣ | Presentation Layer          | Data formatting, encryption |
| 5️⃣ | Session Layer               | Session Establish, Maintain, Terminate |
| 4️⃣ | Transport Layer             | Reliable delivery, TCP/UDP |
| 3️⃣ | Network Layer               | IP Address, Routing |
| 2️⃣ | Data Link Layer             | MAC Address, Frame handling |
| 1️⃣ | Physical Layer              | Bits transmission via medium |

---

## 🔹 Layer 7: Application Layer

- ইউজারের অ্যাপলিকেশন ও নেটওয়ার্কের মাঝে ইন্টারফেস তৈরি করে।
- কাজ: Resource sharing, File access, Browsing, Email
- Common Protocols:
  - FTP, TFTP
  - HTTP, HTTPS
  - DNS, DHCP
  - SSH, Telnet
  - SMTP, POP3
  - LDAP, SMB

  নিশ্চয়ই! আপনি যে প্রোটোকলগুলোর নাম দিয়েছেন—**FTP, TFTP, HTTP, HTTPS, DNS, DHCP, SSH, Telnet, LDAP, SMB, ARP, RARP, ICMP, SMTP, POP**—এগুলোর **ফুল মিনিং, কাজ এবং OSI ৭ লেয়ারে অবস্থান** নিচে সুন্দর করে তালিকাবদ্ধ করে দেওয়া হলো।

---

# 📘 ১. প্রোটোকলগুলোর ফুল মিনিং ও কাজ

| প্রোটোকল       | ফুল মিনিং                             | কাজ                                                             |
| -------------- | ------------------------------------- | --------------------------------------------------------------- |
| **FTP**        | File Transfer Protocol                | ফাইল আপলোড ও ডাউনলোডের জন্য ব্যবহৃত হয়                          |
| **TFTP**       | Trivial File Transfer Protocol        | সিম্পল ফাইল ট্রান্সফার, কোনো authentication বা encryption ছাড়াই |
| **HTTP**       | HyperText Transfer Protocol           | ওয়েবপেজ লোড করার জন্য ব্যবহৃত হয়                                |
| **HTTPS**      | HyperText Transfer Protocol Secure    | নিরাপদভাবে ওয়েব ট্রান্সমিশনের জন্য (SSL/TLS)                    |
| **DNS**        | Domain Name System                    | নাম থেকে IP address রিজলভ করা                                   |
| **DHCP**       | Dynamic Host Configuration Protocol   | অটোমেটিক IP, Gateway, Subnet mask বরাদ্দ দেয়                    |
| **SSH**        | Secure Shell                          | সিকিউর রিমোট কনসোল অ্যাকসেস                                     |
| **Telnet**     | Teletype Network                      | রিমোট অ্যাকসেসের জন্য (non-secure)                              |
| **LDAP**       | Lightweight Directory Access Protocol | ইউজার ডিরেক্টরি সিস্টেমে এক্সেস                                 |
| **SMB**        | Server Message Block                  | ফাইল/প্রিন্টার শেয়ারিং (Windows/Unix)                           |
| **ARP**        | Address Resolution Protocol           | IP থেকে MAC address নির্ধারণ                                    |
| **RARP**       | Reverse Address Resolution Protocol   | MAC থেকে IP address নির্ধারণ                                    |
| **ICMP**       | Internet Control Message Protocol     | Ping, network error/troubleshooting                             |
| **SMTP**       | Simple Mail Transfer Protocol         | ইমেইল পাঠানোর জন্য                                              |
| **POP** / POP3 | Post Office Protocol                  | ইমেইল গ্রহণ করার জন্য (email inbox থেকে)                        |

---

# 🌐 ২. OSI Model-এ এই প্রোটোকলগুলোর স্তর (Layer)

| প্রোটোকল         | OSI লেয়ার             | ব্যাখ্যা                       |
| ---------------- | --------------------- | ------------------------------ |
| **FTP**          | Layer 7 – Application | ইউজার লেভেলে ফাইল ট্রান্সফার   |
| **TFTP**         | Layer 7 – Application | লাইটওয়েট ফাইল ট্রান্সফার       |
| **HTTP / HTTPS** | Layer 7 – Application | ওয়েব ব্রাউজিং (HTTPS → Secure) |
| **DNS**          | Layer 7 – Application | নাম থেকে IP রিজলভ              |
| **DHCP**         | Layer 7 – Application | IP address বরাদ্দ              |
| **SSH / Telnet** | Layer 7 – Application | রিমোট অ্যাকসেস                 |
| **LDAP**         | Layer 7 – Application | Directory অ্যাকসেস             |
| **SMB**          | Layer 7 – Application | ফাইল ও রিসোর্স শেয়ার           |
| **SMTP / POP3**  | Layer 7 – Application | ইমেইল পাঠানো/গ্রহণ             |
| **ICMP**         | Layer 3 – Network     | Ping, network error detect     |
| **ARP / RARP**   | Layer 2 – Data Link   | IP ↔ MAC address রিজলভ         |

---

# 📊 OSI ৭ লেয়ারে তাদের কার্যপ্রবাহ সংক্ষেপে

| Layer               | কী হয়                                     | কোন প্রোটোকল                                                         |
| ------------------- | ----------------------------------------- | -------------------------------------------------------------------- |
| **7. Application**  | ইউজারের সরাসরি interface                  | FTP, TFTP, HTTP, HTTPS, DNS, DHCP, SSH, Telnet, SMTP, POP, SMB, LDAP |
| **6. Presentation** | ডেটা Encryption/Decryption, Compression   | HTTPS, SSH (TLS/SSL)                                                 |
| **5. Session**      | Session তৈরি, পরিচালনা, বন্ধ              | SSH, Telnet, FTP                                                     |
| **4. Transport**    | TCP/UDP ব্যবহার করে Port-ভিত্তিক delivery | All except ICMP/ARP/RARP                                             |
| **3. Network**      | IP Addressing, Routing                    | ICMP, IP (used by others)                                            |
| **2. Data Link**    | MAC Address, Frame, ARP                   | ARP, RARP                                                            |
| **1. Physical**     | Bits Transmission                         | All প্রোটোকলের নিচের স্তর                                            |

---

# 📌 সহজভাবে মনে রাখার উপায়:

| কাজ           | প্রোটোকল উদাহরণ | স্তর        |
| ------------- | --------------- | ----------- |
| ফাইল পাঠানো   | FTP, TFTP       | Application |
| ওয়েব ব্রাউজিং | HTTP, HTTPS     | Application |
| IP দেওয়া      | DHCP            | Application |
| নেম রিজলভ     | DNS             | Application |
| Ping চেক      | ICMP            | Network     |
| MAC resolve   | ARP, RARP       | Data Link   |
| ইমেইল         | SMTP, POP       | Application |
| রিমোট লগিন    | SSH, Telnet     | Application |

---

## 🔚 শেষ কথা

* আপনার মনে রাখতে হবে: **প্রায় সব ইউজার-ভিত্তিক কাজ** হয় **Application Layer** এ।
* কিন্তু সেই প্রোটোকলের পেছনে **TCP/UDP (Transport Layer)**, **IP (Network Layer)**, এবং **MAC/Physical (Layer 2/1)** অটোমেটিক কাজ করে।


## 🔹 Layer 6: Presentation Layer

- Data কে ইউজার-ফ্রেন্ডলি করতে **translate** করে।

এই  লেয়ার ৩ ভাবে Data কে translate করে : 
- Encryption/Decryption
- Compression/Decompression
- Plane Text → Binary → Plane Text

---

## 🔹 Layer 5: Session Layer

- Sender ও Receiver এর মধ্যে **Session Establish বা start,Session Maintain বা Continue ও Session Terminate বা End** করে।
- Communication Modes:
  - Simplex
  - Half Duplex
  - Full Duplex

---

## 🔹 Layer 4: Transport Layer

### ⚙️ কাজ:
- **Reliable Delivery**
- **Segmentation** করে data কে ছোট ছোট অংশে ভাগ করে
- **Acknowledgment** পাঠায়
- **Flow Control** (Window Size)
- **Sequencing** করে সঠিক order-এ পাঠায়

### 🧪 Protocols:
- **TCP (Transmission Control Protocol)** → Reliable
- **UDP (User Datagram Protocol)** → Fast but Unreliable

### 🔢 Port Number:
- Total: 65536 (Range: 0–65535)
- Examples:
  | Protocol | Port | Transport Protocol |
  |----------|------|--------------------|
  | HTTP     | 80   | TCP                |
  | FTP      | 20/21| TCP                |
  | DNS      | 53   | UDP/TCP            |
  | DHCP     | 67/68| UDP                |
  | SSH      | 22   | TCP                |
  | HTTPS    | 443  | TCP                |

---

## 🔹 Layer 3: Network Layer

- Responsible for **Logical Addressing (IP)** এবং **Routing**
- Router এই Layer-এ কাজ করে
- Packet = Source IP + Destination IP + Transport Data

---

## 🔹 Layer 2: Data Link Layer

- **MAC Address** এর মাধ্যমে ডাটা পাঠানো
- Frame তৈরি করে
- **Sub Layers**:
  - LLC (Logical Link Control)
  - MAC (Media Access Control)
- Devices: **Switch, NIC, Bridge**
- Protocols: Ethernet, HDLC, PPP, STP, VTP

---

## 🔹 Layer 1: Physical Layer

- Bit level-এ ডাটা ট্রান্সমিশন করে
- **Medium**: Cables, WiFi, Bluetooth, Radio
- Devices: Hub, Repeater, Network Cable
- Electrical/Optical/RF Signal ব্যবহার করে

---

## 🔁 OSI Encapsulation Process

1. Data তৈরি হয় Application Layer-এ
2. প্রতিটি Layer Header যোগ করে নিচের Layer-এ পাঠায়
3. Physical Layer থেকে Bits হিসেবে ট্রান্সমিট হয়
4. Receiver দিক থেকে উল্টোভাবে Decapsulation হয়

---

## 🧠 OSI Model Layer-Device-Protocol Chart

| Layer | Devices           | Protocols / Services               |
|-------|-------------------|------------------------------------|
| 7     | Web Browser, Mail | HTTP, FTP, DNS, DHCP, SSH         |
| 6     |                   | SSL, TLS, JPEG, MPEG              |
| 5     |                   | NetBIOS, RPC, NFS                 |
| 4     |                   | TCP, UDP                          |
| 3     | Router            | IP, ICMP, OSPF                    |
| 2     | Switch, NIC       | Ethernet, STP, MAC Address        |
| 1     | Hub, Cables       | UTP, Coaxial, Fiber, WiFi, Radio  |

---

OSI মডেল জানলে:
- ট্রাবলশুটিং সহজ হয়
- নেটওয়ার্ক ডিজাইন স্পষ্ট হয়
- প্রোটোকল ও ডিভাইসগুলোর কার্যপ্রণালী ভালোভাবে বোঝা যায়

