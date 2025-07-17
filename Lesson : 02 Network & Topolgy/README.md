# Networking and Topology

# 📘 CCNA - নেটওয়ার্কিং পরিচিত

## নেটওয়ার্ক কী?

আমরা সবাই কমবেশি নেটওয়ার্ক বা নেটওয়ার্কিং এর সাথে পরিচিত। একাধিক কম্পিউটার একে অপরের সাথে তথ্য আদান-প্রদান করলে তাকে নেটওয়ার্ক বলা হয়। এর জন্য অন্তত দুটি কম্পিউটার প্রয়োজন।

---

## নেটওয়ার্কের প্রকারভেদ
নেটওয়ার্ক প্রধানত তিন ভাগে বিভক্ত:

- LAN
- MAN
- WAN

### 🟢 Local Area Network (LAN)
একই ভবনের ভিতরে অবস্থিত একাধিক কম্পিউটারকে সংযুক্ত করে LAN গঠিত হয়।   
**ডেটা ট্রান্সফার গতি:** ১০ Mbps  
**ডিভাইস:** কম্পিউটার, হাব, নেটওয়ার্ক ইন্টারফেস ইত্যাদি

Diaram of LAN : 
   <img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/4bc4986a-2b82-4bc9-844a-03dc62d232bd" />
---
### 🟡 Metropolitan Area Network (MAN)
একটি শহরের ভিতরে বিভিন্ন স্থানে অবস্থিত লোকেশনগুলোর মধ্যে সংযোগ স্থাপন করে MAN তৈরি হয়।  
**পরিসর:** ৫০–৭৫ মাইল  
**ডেটা ট্রান্সফার:** গতি স্থির নয়  
**ডিভাইস:** রাউটার, সুইচ, মাইক্রোওয়েভ এন্টেনা

MAN`s Diagram : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/7a2d9876-562e-45a0-8596-a6610e8a4a2d" />
---

### 🔹 WAN (Wide Area Network)
বিভিন্ন শহর বা দেশের মধ্যে সংযোগ স্থাপন করে।  
**গতি:** ৫৬ Kbps থেকে ১.৫৪৪ Mbps  
**ডিভাইস:** রাউটার, মডেম, WAN সুইচ

Diagram of WAN
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/632f34f4-140a-4147-9083-b11eb1ba49fd" />
---

## End Device এবং Intermediary Device
নেটওয়ার্ক ডিভাইসসমূহকে আবার দুইভাগে ভাগ করা হয়:
1. End Device  
2. Intermediary Device

### 🖥 End Device:
কম্পিউটার, ল্যাপটপ, সার্ভার, প্রিন্টার, আইপি ফোন, আইপি রাউটার, পিসি ইত্যাদি।  End Device কে Host ও বলা হয়।
Host হচ্ছে sender বা Reciever, যাদের আলাদা আলাদা আইডেন্টিটি থাকে। এক Host যখন অন্য Host-কে ডেটা পাঠায় তখন ঠিকানা বা Address ব্যবহৃত করে।

### End Devices :
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/78de8cb6-e7d6-4d7c-8e33-e313ac9fbe9c" />

###  Intermediary Device
End Device গুলোর মাঝে সংযোগ স্থাপনকারী ডিভাইস।  
যেমন: Switch, Hub, Router, Wireless Access Point 

### Intermediary Device : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/950d781b-07a0-4fe9-b23d-96f07044cf7c" />
---

## PC এর অন্যান্য নামসমূহ
- Work Station  
- Host  
- Node  
- End Device  
- End Point  
- Client PC  
- Server PC  
- Desktop

---

## ## LAN Card এর বিভিন্ন নাম
1. Network Interface Card (NIC)  
2. Communication Card  
3. Ethernet Card

# Diagram of LAN Card : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/ce943c79-62aa-4791-8688-970887d18810" />
---

## নেটওয়ার্ক মিডিয়া (তথ্য আদান-প্রদানের মাধ্যম)/Network Media
তথ্য আদান-প্রদানের জন্য ব্যবহৃত মাধ্যমসমূহ:
1. Metallic Wire  
2. Glass or Fiber  
3. Wireless Transmission

** Network Media নির্বাচনের সময় বিবেচ্য বিষয়সমূহ:**
- দূরত্ব
- পরিবেশ
- ডেটা পরিমাণ এবং গতি
- ইনস্টলেশন খরচ

---

### Wireless Transmission

বেতার তরঙ্গ ব্যবহার করে তথ্য প্রেরণের পদ্ধতি, যেখানে কোনো কেবল ব্যবহারের প্রয়োজন হয় না।

Wireless Transmission : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/821f54f7-854a-41a6-a1ec-adbf6cb250e3" />

## Common Data Network Symbols

---

## Network Topologies (টপোলজির ধরন)
নেটওয়ার্কের কম্পিউটার গুলো কিভাবে যুক্ত আছে তা নির্ধারণ করে টপোলজি।

---
**প্রকারভেদ:**
- Point to Point
- Bus
- Core
- Mesh
- Ring
- Star
- Hub & Spoke
---
### 1. Point-to-Point Topology
দুইটি পিসির মধ্যে সরাসরি সংযোগ স্থাপিত হয়।

Point-to-Point Topology Diagram: 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/0cfe75d8-5020-4a56-ad41-3a51a500d9d7" />
---

### 2. Bus Topology

একটি কেবলে একাধিক কম্পিউটার যুক্ত থাকে।  
**ব্যবহারযোগ্য উপকরণ:**  
1. Coaxial Cable  
2. LAN Card  
3. T Connector  
4. Terminator

**সুবিধা:** খরচ কম, সহজ স্থাপন  
**অসুবিধা:** তারে সমস্যা হলে পুরো নেটওয়ার্ক বিঘ্নিত হয়

Bus Topology Diagram : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/a1d67870-33d1-4dc9-a1cd-6e9193555856" />


### 3. Core Topology

সর্বনিম্ন ৩টি কম্পিউটার প্রয়োজন। প্রথম কম্পিউটার থেকে শেষ কম্পিউটার পর্যন্ত যুক্ত থাকে এবং প্রথম ও শেষ পিসি অতিরিক্তভাবে সংযুক্ত থাকে।  
**দুইটি LAN Card** প্রতিটি পিসিতে থাকতে হয়।

**অসুবিধা:** কোনো একটি পিসি বন্ধ হয়ে গেলে পুরো নেটওয়ার্ক বন্ধ হয়ে যেতে পারে।

Core Topology Diagram : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/f8c33c24-c82f-4b65-9182-01eafbb2c070" />

### 4. Mesh Topology

প্রতিটি পিসি অন্যসব পিসির সাথে যুক্ত থাকে।  
- Full Mesh  
- Partial Mesh / Hub Mesh

Full Mesh Diagram : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/0b3520a6-4e02-478b-a5fe-46efa03096e9" />

Partial Mesh Diagram : 
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/7496320c-0cc4-4e29-bebf-f8f56618cac1" />

---

### 5. Hub & Spoke Topology

একটি কেন্দ্রীয় ডিভাইস (HUB) এর সাথে অন্যান্য ডিভাইস (Spoke) সরাসরি সংযুক্ত থাকে।
Hub কেন্দ্রীয় ডিভাইস হিসেবে কাজ করে, অন্যান্য ডিভাইসগুলো Spoke হিসেবে যুক্ত থাকে।

Hub & Spoke Topology Diagram :

<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/3d47268e-c231-4a3a-891d-51a4518ddb34" />


- মাঝখানে যে কম্পিউটারটি রয়েছে — যেখান থেকে সব লাইন (সংযোগ) বের হয়েছে — ওটাই Hub।
- এটি কেন্দ্রীয় নিয়ন্ত্রণ ডিভাইস, যেমন Switch, Router বা Central Server হতে পারে।

- Spoke : Hub থেকে সংযুক্ত চারপাশের ৮টি কম্পিউটারই Spoke।
- প্রতিটি spoke সরাসরি শুধুমাত্র hub-এর সাথে সংযুক্ত থাকে, একে অপরের সাথে নয়।
```
          [Spoke]
              |
[Spoke] — [Hub] — [Spoke]
              |
          [Spoke]

```

### 🔸 Ring Topology

সব কম্পিউটার একটি রিং আকারে সংযুক্ত থাকে।

**সুবিধা:** দ্রুত যোগাযোগ  
**অসুবিধা:** ব্যয়বহুল ও সমস্যার সমাধান কঠিন

Ring Topology Diagram
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/70369482-3730-4c75-bbe8-6da526d33197" />

---

### 7. Star Topology
সব ডিভাইস একটি HUB বা SWITCH এর সাথে সংযুক্ত  
**সুবিধা:** সহজ স্থাপন ও ট্রাবলশুটিং  
**অসুবিধা:** কেন্দ্রীয় ডিভাইসে সমস্যা হলে পুরো নেটওয়ার্ক অচল

Star Topology Diagram
<img width="1024" height="1024" alt="Image" src="https://github.com/user-attachments/assets/792bf51a-4270-4a6d-a608-9619c6356c47" />
---