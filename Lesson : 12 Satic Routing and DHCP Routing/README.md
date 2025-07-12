# Static and Dynamic Routing 


# 📡 DHCP (Dynamic Host Configuration Protocol)

**DHCP** (Dynamic Host Configuration Protocol) হলো একটি নেটওয়ার্ক প্রোটোকল যা ক্লায়েন্ট ডিভাইসকে স্বয়ংক্রিয়ভাবে IP ঠিকানা ও অন্যান্য নেটওয়ার্ক সেটিংস প্রদান করে।

---

## 🧠 কীভাবে DHCP কাজ করে?

DHCP কাজ করে **DORA Process** অনুসারে:

| ধাপ | নাম               | বর্ণনা                                                                 |
|-----|------------------|------------------------------------------------------------------------|
| 1️⃣ | **Discover**      | ক্লায়েন্ট একটি DHCP Discover মেসেজ পাঠায়: "আমি একটি IP চাই!"          |
| 2️⃣ | **Offer**         | DHCP সার্ভার একটি IP address সহ অফার পাঠায়: "এই IP নাও!"               |
| 3️⃣ | **Request**       | ক্লায়েন্ট নির্দিষ্ট IP এর জন্য অনুরোধ পাঠায়: "আমি এই IP ব্যবহার করতে চাই" |
| 4️⃣ | **Acknowledgement** | সার্ভার নিশ্চিত করে যে ক্লায়েন্ট IP address পেয়ে গেছে                    |

---

## 🖥️ ব্যবহারিক উদাহরণ

ধরো, একটি ল্যাপটপ WiFi-তে সংযুক্ত হচ্ছে:

1. 📤 ল্যাপটপ: DHCP Discover
2. 📥 DHCP সার্ভার: DHCP Offer (192.168.1.100)
3. 📤 ল্যাপটপ: DHCP Request
4. 📥 DHCP সার্ভার: DHCP Acknowledgement

---

## ✅ DHCP ব্যবহারের সুবিধা

- 🔄 Dynamic IP address বরাদ্দ
- ⚙️ IP conflict কমায়
- 🧑‍💻 Manual configuration প্রয়োজন নেই
- 📶 WiFi রাউটার ও ISP-তে প্রচুর ব্যবহার

---

## 🔧 DHCP সার্ভার কনফিগারেশন (Cisco Router Example)

```bash
Router> enable
Router# configure terminal
Router(config)# ip dhcp pool MY_POOL
Router(dhcp-config)# network 192.168.10.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.10.1
Router(dhcp-config)# dns-server 8.8.8.8
Router(dhcp-config)# exit
Router(config)# ip dhcp excluded-address 192.168.10.1 192.168.10.10

🎯 এটি একটি DHCP pool তৈরি করে এবং 192.168.10.1 থেকে 192.168.10.10 IP গুলো বাদ দিয়ে বাকিগুলো ক্লায়েন্টদের মাঝে বিতরণ করবে।

🌐 DHCP কোথায় ব্যবহৃত হয়?
🏠 Home Router

🏢 Corporate Network

🖥️ Windows/Linux DHCP Server

🌍 ISP-এর Dynamic IP প্রদান

