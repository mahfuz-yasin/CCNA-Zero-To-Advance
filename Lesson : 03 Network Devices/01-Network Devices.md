
## 🌀 Repeater

**Repeater** হল এমন একটি ডিভাইস যা সিগন্যালকে এম্প্লিফাই করার জন্য ব্যবহার করা হয়।
১৮৫ মিটার দূরত্ব অতিক্রম করার আগে আপনি একটি রিপিটার ব্যবহার করলে সেই সিগন্যালকে এম্প্লিফাই করে দিলে সরাসরি ১৮৫ মিটার অতিক্রম করতে পারবে।

* এটি কাজ করে **OSI মডেল** এর **ফিজিক্যাল লেয়ারে**।

📷 ![Repeater](https://i2.wp.com/www.shikkhok.com/wp-content/uploads/2014/09/Repeater.jpg)

---

## 🔗 HUB

**Hub** হল একটি সরল রিপিটার যেটি একাধিক পোর্টের মাধ্যমে ডেটা ব্রডকাস্ট করে।

* এটি কাজ করে **OSI মডেল** এর **ফিজিক্যাল লেয়ারে**।
* সাধারণত **4 থেকে 24 পোর্ট** পর্যন্ত হয়।
* কাজ করে **Half Duplex Mode** এ।
* শুধুমাত্র **সিগন্যাল রিলে** করে।
* যেকোনো পোর্টে **Collision** হলে তা **Broadcast** করে দেয়।

📷 ![Hub](https://i1.wp.com/www.shikkhok.com/wp-content/uploads/2014/09/HUB.png)

---

## 🌉 Bridge

**Bridge** একটি স্মার্ট ডিভাইস যা MAC Address দেখে একাধিক সেগমেন্ট যুক্ত করে।

* OSI মডেল এর **Data Link Layer** এ কাজ করে।
* Port সংখ্যা: **2 থেকে 4**
* কাজ করে **Full Duplex Mode** এ।
* **MAC Table/CAM Table** ব্যবহার করে।

**Bridge এর বৈশিষ্ট্য:**

* সিগন্যালকে Frame এ রূপান্তর করে।
* Source MAC Address পড়ে CAM Table এ Entry করে।
* প্রথমে Broadcast করে, পরে Unicast করে।
* প্রতিটি Entry সাধারণত ৩০ সেকেন্ড পর্যন্ত থাকে।
* Collision হলে নির্দিষ্ট Port ব্লক করে দেয়।

---

## 🧠 Switch

**Switch** একটি Multiport Bridge এর উন্নত সংস্করণ।

* OSI মডেল এর **Data Link Layer** এ কাজ করে।
* Port সংখ্যা: **4 থেকে 24**
* কাজ করে **Full Duplex Mode** এ।
* MAC Address দেখে Decision নেয়।

📷 ![Switch](https://i2.wp.com/www.shikkhok.com/wp-content/uploads/2014/09/switch.jpg)

### Switch এর ধরন:

1. **Unmanageable Switch**: কোনো OS বা প্রটোকল রান করে না।
2. **Manageable Switch**: OS থাকে, প্রটোকল ও সার্ভিস চালু থাকে।
3. **Layer 3 Switch**: Routing ও Switching উভয়ই করে (Brouter = Bridge + Router)

---

## 📡 Router

**Router** একটি নেটওয়ার্ক ডিভাইস যা আলাদা আলাদা নেটওয়ার্ককে সংযুক্ত করে।

* OSI মডেল এর **Network Layer** এ কাজ করে।
* Port সংখ্যা: **2 থেকে 8**
* কাজ করে **Full Duplex Mode** এ।
* **IP Address** দেখে Routing করে।

### Router এর কাজ:

1. **Inter-Network Communication** – বিভিন্ন নেটওয়ার্কের মধ্যে যোগাযোগ
2. **Path Selection**

   * **Manual**: Admin নিজে পথ নির্ধারণ করে।
   * **Dynamic**: RIP (Hop Count), OSPF (Bandwidth) ইত্যাদি প্রোটোকল দ্বারা।
3. **Packet Switching**
4. **Packet Filtering** – ACL দ্বারা নিয়ন্ত্রণ

---

## 📃 Routing Table

* প্রতিটি Router এ একটি Table থাকে যেটা **Routing Table** নামে পরিচিত।
* এতে বিভিন্ন Network সম্পর্কিত তথ্য থাকে।
* Broadcast ডেটা Router গ্রহণ করে না।

---

## 🔌 Router Interfaces

### Networking Port

#### Physical Interface:

1. **Ethernet** = 10 Mbps
2. **Fast Ethernet** = 100 Mbps
3. **Gigabit Ethernet** = 1000 Mbps
4. **Serial Interface** = 1.544 Mbps

#### Logical Interface:

* **Loopback Interface**: 0 থেকে 2147483647 পর্যন্ত লজিকাল ইন্টারফেস
* টেস্টিং বা নেটওয়ার্ক সিমুলেশনের কাজে ব্যবহৃত হয়

---

### Regular Port:

1. **Console Port**: লোকালি কনফিগার করার জন্য
2. **Auxiliary Port**: মডেম দিয়ে রিমোট কনফিগারেশন
3. **VTY Port**: Telnet/SSH এর মাধ্যমে রিমোট কনফিগারেশন (Password না থাকলে কনফিগার করা যাবে না)

---

## ⚙️ Protocol

**Protocol** হল নিয়মের একটি সেট যা ম্যানুয়ালি বা ডাইনামিকভাবে কমিউনিকেশন নিয়ন্ত্রণ করে।

### প্রকারভেদ:

1. **Open Source Protocol**: সকল ডিভাইসে চলে (e.g. RIP, OSPF)
2. **Proprietary Protocol**: নির্দিষ্ট কোম্পানির ডিভাইসে চলে (e.g. EIGRP)

**Sub-Protocol**: বড় Protocol এর অংশ, যেমন EIGRP এর Sub-Protocol হলো STP

---

## 🛠️ Service

প্রতিটি Protocol এক বা একাধিক Service প্রদান করে।
উদাহরণ:

* **PING** → ICMP Protocol এর একটি সার্ভিস → Connectivity Test / Troubleshoot

---

## 🌐 Default Gateway

**Default Gateway** হল এমন একটি Router IP Interface যেটি LAN থেকে বাহিরে যাবার পথ।

* এটি Router এর IP Interface দ্বারা নির্ধারিত হয়।
* প্রতিটি Host এ এটি কনফিগার করতে হয়।
* না থাকলে External Communication সম্ভব নয়।

--- 