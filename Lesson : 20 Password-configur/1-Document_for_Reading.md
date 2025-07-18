**Cisco Router Password Configuration**

**steps**:
- basic configuration
- set password
 
# types of passwords :

* Admin (privileged exec) mode password
* Encrypted password
* Console password
* Auxiliary port password
* VTY (Telnet/SSH) password
* Encrypting all passwords

---

### ✅ GitHub Markdown Format:

````markdown
# 🔐 Cisco Router Password Configuration Guide

This guide shows how to configure various types of passwords on a Cisco router or switch to ensure proper access control and security.

---

## 1️⃣ Admin (Privileged EXEC Mode) Password

```bash
Router(config)# enable password admin123
````

🛑 This is a plain-text password (not secure).
✅ To encrypt it, use `enable secret` instead (next step).

---

## 2️⃣ Encrypted Admin Password (Recommended)

```bash
Router(config)# enable secret admin123
```

✅ This encrypts the password using MD5.
🛡️ Always use `enable secret` instead of `enable password`.

---

## 3️⃣ Console Port Password

```bash
Router(config)# line console 0
Router(config-line)# password c0ns0le123
Router(config-line)# login
Router(config-line)# exit
```

✅ This secures **physical console access** to the device.

---

## 4️⃣ Auxiliary Port Password (Optional - rarely used)

```bash
Router(config)# line aux 0
Router(config-line)# password aux123
Router(config-line)# login
Router(config-line)# exit
```

✅ This secures access via modem (AUX port).

---

## 5️⃣ VTY Port Password (for Telnet/SSH Access)

```bash
Router(config)# line vty 0 4
Router(config-line)# password vty123
Router(config-line)# login
Router(config-line)# exit
```

✅ This secures **remote access** through Telnet or SSH (lines 0–4 = 5 sessions).

---

## 6️⃣ Encrypt All Plain Text Passwords

```bash
Router(config)# service password-encryption
```

✅ This encrypts all plain-text passwords (like console, aux, and vty) using **Type 7 encryption**.

---

## 🔁 Summary Table

| Password Type         | Command Example                     | Encrypted?                                |
| --------------------- | ----------------------------------- | ----------------------------------------- |
| Enable (plain)        | `enable password admin123`          | ❌ (unless encrypted)                      |
| Enable (secret)       | `enable secret admin123`            | ✅ (MD5 - Type 5)                          |
| Console               | `line console 0 → password → login` | ❌/✅ (after `service password-encryption`) |
| Auxiliary             | `line aux 0 → password → login`     | ❌/✅                                       |
| VTY (Telnet/SSH)      | `line vty 0 4 → password → login`   | ❌/✅                                       |
| Encrypt All Passwords | `service password-encryption`       | ✅ (Type 7)                                |

---

## 🧪 Verification Commands

```bash
Router# show running-config
Router# show line
Router# show users
```


## 🔧 STEP-BY-STEP: পাসওয়ার্ড টেস্ট ও যাচাই

### ✅ ১. Save configuration (রাউটার রিস্টার্টে যেন পাসওয়ার্ড মুছে না যায়)

```bash
Router# write memory
```

বা

```bash
Router# copy running-config startup-config
```

---

### ✅ ২. রাউটার রিস্টার্ট (reload করো)

```bash
Router# reload
```

🔸 Confirm চাইলে, শুধু Enter চাপো।

---

### ✅ ৩. Router নতুন চালু হলে দেখবে:

#### 🔐 Step 1:

```
User Access Verification
Password:
```

এখানে তুমি `abcd` টাইপ করবে → এটা **console password**।

#### 🔐 Step 2:

```bash
Router> enable
Password:
```

এখানে তুমি দিবে `1234` অথবা `enable secret` এর পাসওয়ার্ড (যদি সেট করো)।

---

### ✅ ৪. Telnet দিয়ে Login করতে চাইলে:

#### আগে Telnet চালু করো (optional)

```bash
Router(config)# line vty 0 4
Router(config-line)# password abcd
Router(config-line)# login
Router(config-line)# exit
```

#### তারপর পিং টেস্ট করে রিমোট আইপি জানো:

```bash
Router# ping 192.168.10.X
```

#### তারপর অন্য ডিভাইস (বা পিসি) থেকে:

```bash
telnet 192.168.10.1
```

🔐 তখন `abcd` চাইবে → এটা VTY password।

---

## 🔒 ✅ সমস্ত পাসওয়ার্ড কনফিগার করার চেকলিস্ট

| পাসওয়ার্ড ধরন         | কমান্ড                                 | কখন চাইবে                                  |
| --------------------- | -------------------------------------- | ------------------------------------------ |
| **Console Password**  | `line con 0 → password abcd → login`   | Router চালু হলে CLI-তে ঢোকার সময়           |
| **Enable Password**   | `enable password 1234`                 | `enable` দিলে                              |
| **Enable Secret**     | `enable secret admin123`               | `enable` দিলে (এইটা থাকলে secret কাজ করবে) |
| **VTY Password**      | `line vty 0 4 → password abcd → login` | Telnet/SSH করলে                            |
| **AUX Password**      | `line aux 0 → password abcd → login`   | AUX পোর্টে ঢুকলে                           |
| **Encrypt Passwords** | `service password-encryption`          | সব password এনক্রিপ্ট করতে                 |

---

## 🔍 পরিক্ষা করো:

* `reload` দিয়ে console password কাজ করছে কিনা
* `enable` দিয়ে enable/secret password চাইছে কিনা
* `telnet` দিয়ে VTY password কাজ করছে কিনা
* `show running-config` দিয়ে চেক করো সব আছে কিনা

---
