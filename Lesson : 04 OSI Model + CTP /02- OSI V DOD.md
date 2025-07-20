
# 🆚 OSI vs DoD Model 

---

## 📘 OSI Model (Open Systems Interconnection Model)

* তৈরি করেছে: **ISO (International Organization for Standardization)**
* স্তরের সংখ্যা: **7 টি Layer**
* উদ্দেশ্য: বিভিন্ন ডিভাইস ও প্রোটোকলের মধ্যে স্ট্যান্ডার্ড কমিউনিকেশন নিশ্চিত করা।
* এটি একটি **তাত্ত্বিক (theoretical)** মডেল।

---

## 🛰️ DoD Model (TCP/IP Model বা Internet Model)

* তৈরি করেছে: **US Department of Defense**
* স্তরের সংখ্যা: **4 টি Layer**
* উদ্দেশ্য: ইন্টারনেট-ভিত্তিক কমিউনিকেশন বাস্তবায়ন করা
* এটি একটি **প্রাকটিক্যাল (practical)** ও **ইন্টারনেট-বেইসড** মডেল

---

## 📊 তুলনামূলক টেবিল (OSI vs DoD)

| বিষয়                     | OSI Model                        | DoD Model (TCP/IP)                   |
| ------------------------ | -------------------------------- | ------------------------------------ |
| 🏢 নির্মাতা              | ISO                              | US Department of Defense             |
| 🧱 স্তরের সংখ্যা         | 7 Layers                         | 4 Layers                             |
| 📌 উদ্দেশ্য              | স্ট্যান্ডার্ড Reference Model    | Practical communication framework    |
| 💬 ব্যবহার               | শিক্ষার জন্য বেশি ব্যবহৃত হয়     | বাস্তব ইন্টারনেট কমিউনিকেশনে ব্যবহৃত |
| 🌍 জনপ্রিয়তা             | তাত্ত্বিকভাবে জনপ্রিয়            | প্র্যাকটিক্যালি বেশি জনপ্রিয়         |
| 🎯 ফোকাস                 | সার্ভিস, প্রসেস ও অ্যাবস্ট্রাকশন | কমিউনিকেশন ও নেটওয়ার্কিং             |
| 📤 ডাটা ট্রান্সফার ইউনিট | Packet, Frame, Segment           | Message, Datagram                    |

---

## 🔁 OSI 7 Layers vs DoD 4 Layers Mapping

| OSI Model            | DoD Model (TCP/IP)             | ব্যাখ্যা                                |
| -------------------- | ------------------------------ | --------------------------------------- |
| **Application (7)**  | **Application Layer**          | Email, HTTP, FTP, DNS                   |
| **Presentation (6)** | ↳ Merge with Application       | Data Translation, Encoding handled here |
| **Session (5)**      | ↳ Merge with Application       | Session creation handled by App         |
| **Transport (4)**    | **Transport Layer**            | TCP, UDP                                |
| **Network (3)**      | **Internet Layer**             | IP, ICMP, Routing                       |
| **Data Link (2)**    | **Network Access Layer**       | MAC, ARP, Ethernet                      |
| **Physical (1)**     | ↳ Part of Network Access Layer | Bits transmission                       |

---

## 📌 গুরুত্বপূর্ণ মিল ও পার্থক্য

| দিক                   | OSI        | DoD                     |
| --------------------- | ---------- | ----------------------- |
| Protocol Independence | হ্যাঁ      | না (TCP/IP কেন্দ্রিক)   |
| Layered Abstraction   | স্পষ্ট ৭টি | সমন্বিত ৪টি             |
| ব্যবহার               | শিক্ষাগত   | ইন্টারনেট ও নেটওয়ার্কিং |
| Flexibility           | অনেক বেশি  | সীমিত (TCP/IP ভিত্তিক)  |

---

## 🎯 কোনটা বাস্তবে বেশি ব্যবহৃত হয়?

✅ **DoD (TCP/IP) Model** বাস্তব কমিউনিকেশনে বেশি ব্যবহৃত হয় (যেমন: ইন্টারনেট, ইমেইল, ব্রাউজিং)।
📚 **OSI Model** বেশি ব্যবহৃত হয় **শিক্ষা ও নেটওয়ার্ক থিওরি বোঝাতে।**

---

## ✅ সংক্ষেপে মনে রাখার কৌশল

**OSI Model:**

> **All People Seem To Need Data Processing**
> → Application, Presentation, Session, Transport, Network, Data Link, Physical

**TCP/IP Model (DoD):**

> **A TIN**
> → Application, Transport, Internet, Network Access

---

## 📘 ব্যবহার ক্ষেত্র

| Protocol  | OSI Layer | TCP/IP Layer   |
| --------- | --------- | -------------- |
| HTTP      | 7         | Application    |
| FTP       | 7         | Application    |
| DNS       | 7         | Application    |
| TCP / UDP | 4         | Transport      |
| IP, ICMP  | 3         | Internet       |
| Ethernet  | 2         | Network Access |
