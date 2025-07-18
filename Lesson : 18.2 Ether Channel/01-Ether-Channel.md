# 🌐 EtherChannel (লিংক অ্যাগ্রিগেশন)

EtherChannel হলো এমন একটি প্রযুক্তি, যার মাধ্যমে একাধিক ফিজিক্যাল লিংককে একত্র করে একটি লজিক্যাল লিংক হিসেবে ব্যবহার করা হয়। এটি মূলত সুইচ থেকে সুইচ বা সুইচ থেকে রাউটারের মধ্যে **ব্যান্ডউইথ বৃদ্ধি**, **লোড ব্যালেন্সিং** এবং **রিডানডেন্সি** নিশ্চিত করতে ব্যবহৃত হয়।

---

## 🔧 কাজের প্রক্রিয়া:

- সাধারণভাবে, দুটি সুইচের মধ্যে একটি ক্যাবল সংযোগ দিলে একটি ফিজিক্যাল লিংক তৈরি হয়।
- কিন্তু যখন একাধিক ক্যাবল (যেমন 2, 4, 6 বা সর্বোচ্চ 8টি) ব্যবহার করে ফিজিক্যাল লিংক তৈরি করে, এবং তাদের একত্র করে একটি লজিক্যাল লিংকে রূপান্তর করা হয়—তখন একে **EtherChannel** বলা হয়।
- এই পদ্ধতিতে ফিজিক্যাল লিংকগুলোকে একটি **বান্ডল** হিসেবে গঠন করা হয়।

---

## 📌 শর্তসমূহ:

### 1️⃣ **স্পিড ও ক্যাবল মিল থাকা:**
- সব পোর্টের স্পিড একই হতে হবে।
  - যেমন: যদি একটি পাশে Gigabit Ethernet ব্যবহার করা হয়, তবে অন্য পাশেও সেটাই হতে হবে।
- একই ধরনের ক্যাবল (Ethernet, Fast Ethernet, Gigabit Ethernet) ব্যবহার করতে হবে।

### 2️⃣ **সব পোর্ট অ্যাক্টিভ থাকতে হবে:**
- EtherChannel-এ যুক্ত প্রতিটি পোর্টকে **active** বা **no shutdown** অবস্থায় রাখতে হবে।

---

## 📈 সুবিধাসমূহ:

- ✅ ব্যান্ডউইথ বৃদ্ধি
- ✅ লোড ব্যালেন্সিং
- ✅ ফেইলওভার সাপোর্ট (একটি লিংক ব্যর্থ হলেও অন্যগুলো কাজ চালিয়ে যাবে)
- ✅ spanning-tree port blocking এড়ানো যায়

---

## 🧰 EtherChannel এর অন্য নাম:

> **Link Aggregation** নামেও এটি পরিচিত।

---

## 🔄 EtherChannel Protocols:

EtherChannel গঠনের জন্য দুটি প্রধান প্রোটোকল ব্যবহৃত হয়:

| প্রোটোকল | পূর্ণরূপ | ব্যাখ্যা | ব্যবহার ক্ষেত্র |
|----------|----------|----------|----------------|
| **PAgP** | Port Aggregation Protocol | শুধুমাত্র Cisco ডিভাইসে ব্যবহৃত হয় | Cisco-specific |
| **LACP** | Link Aggregation Control Protocol | IEEE স্ট্যান্ডার্ড (802.3ad); Cisco ও অন্যান্য ডিভাইসে ব্যবহৃত হয় | Multi-vendor support |

---

