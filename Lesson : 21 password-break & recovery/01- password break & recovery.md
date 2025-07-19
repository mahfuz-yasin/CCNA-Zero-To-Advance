# 🔐 Password Break and Recovery Guide (Cisco Devices)

This guide covers how to configure various passwords on Cisco routers/switches, as well as how to break and recover from lost passwords.

---

## ✅ Password Configuration Steps

### 1️⃣ Admin Mode Password (Plain Text)
```bash
Router> enable
Router# configure terminal
Router(config)# enable password 123
```

🛑 This is a plain-text password (not secure).

---

### 2️⃣ Admin Mode Password (Encrypted - Recommended)
```bash
Router> enable
Router# configure terminal
Router(config)# enable secret 1234
```

🔒 `enable secret` encrypts the password using MD5. Always use this instead of `enable password`.

---

### 3️⃣ Console Port Password
```bash
Router(config)# line console 0
Router(config-line)# password ccna
Router(config-line)# login
```

---

### 4️⃣ Auxiliary Port Password
```bash
Router(config)# line aux 0
Router(config-line)# password ccna
Router(config-line)# login
```

---

### 5️⃣ VTY (Telnet/SSH) Password
```bash
Router(config)# line vty 0 4
Router(config-line)# password ccna
Router(config-line)# login
```

---

### 🔍 Verify Password Configuration
```bash
Router# show running-config
```

---

### 💾 Save All Passwords (Configuration)
```bash
Router# copy running-config startup-config
Router# copy run start
Router# write
Router# wr
```

---

### 🔄 Reload the Device After Setup (Optional)
```bash
Router# reload
```

---

## 🛠️ Password Break and Recovery

### ⚠️ When You've Lost the Password

> This method works **only with physical access** (console cable) and **device reload**.

### 🚨 Step-by-Step Recovery Process

1. **Reboot the Router**
   - Power off and on the device.
   - Press `Ctrl + Break` during boot-up to enter **ROMMON mode**.

2. **Change Configuration Register**
   ```bash
   rommon> confreg 0x2142
   rommon> reset
   ```

3. **Bypass the Startup Config**
   - After reset, you'll be in setup mode or user EXEC.
   - Enter privileged mode:
     ```bash
     Router> enable
     ```

4. **Access and Edit Startup Configuration**
   ```bash
   Router# copy startup-config running-config
   Router# configure terminal
   ```

5. **Set a New Password**
   ```bash
   Router(config)# enable secret NEWPASS
   ```

6. **Reset Config Register to Normal**
   ```bash
   Router(config)# config-register 0x2102
   ```

7. **Save and Reload**
   ```bash
   Router# write memory
   Router# reload
   ```

✅ Your password is now reset and device is restored.

---

### 📌 Notes
- Always secure your devices using `enable secret` and avoid using plain-text passwords.
- Use strong passwords for `console`, `vty`, and `aux` lines.
- Keep configuration backups securely stored.

---
