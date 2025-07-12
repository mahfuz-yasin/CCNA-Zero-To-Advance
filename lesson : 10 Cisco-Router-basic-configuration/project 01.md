# Project 01  
## Topic: Basic Configuration in Cisco Packet Tracer

---

### Step 01: Diagram  
- নেটওয়ার্কের ডায়াগ্রাম তৈরি করো।

---

### Step 02: Plan  
- Network IP Address  
- Default Gateway  
- Subnet Mask  
- Router এবং অন্যান্য ডিভাইসে এসব সেটআপ করো।

---

### Step 03: Basic Configuration  

1. CLI তে **User EXEC Mode** এ যাও এবং **enable** বা **en** কমান্ড ব্যবহার করো।  
2. **Privileged EXEC Mode** এ যাও এবং **config terminal** বা **conf t** কমান্ড চালাও।  
3. **Global Configuration Mode** থেকে ইন্টারফেস সিলেক্ট করো, যেমন:  
   ```bashjj
   int gig0/0
4. ইন্টারফেস চালু করো:
    **no shutdown**
5. IP অ্যাড্রেস ও সাবনেট মাস্ক সেট করো:
    - **ip address [IP_Address] [Subnet_Mask]**
    - উদাহরণ:
    ```bash 
     **ip address 192.168.0.1 255.255.255.0**
