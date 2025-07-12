# Project 01  
## Topic: Basic Configuration in Cisco Packet Tracer

---

### Step 01: Diagram  
- নেটওয়ার্কের ডায়াগ্রাম তৈরি করো।

---

### Step 02: Plan  
- Network IP Address  : 192.168.0.0/24
- Default Gateway  : 192.168.0.1
- Subnet Mask  : 255.255.255.0
- Router এবং switch, pc  এসব ডিভাইসেস সেটআপ করো।

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

Project All Images : 
<img width="635" height="557" alt="Image" src="https://github.com/user-attachments/assets/b9f8e084-705e-460c-bb8a-b6a89250f496" />
<img width="695" height="794" alt="Image" src="https://github.com/user-attachments/assets/78b70445-75f2-46ec-8816-445a061cf4cf" />
<img width="695" height="794" alt="Image" src="https://github.com/user-attachments/assets/1559657d-b563-496c-87a3-df18d0419053" />
<img width="695" height="794" alt="Image" src="https://github.com/user-attachments/assets/752ed531-5e86-4d44-ad50-5aa8683be44f" />
<img width="695" height="794" alt="Image" src="https://github.com/user-attachments/assets/a7010ac7-4d34-40e1-8e0f-f3b44670cd92" />
<img width="636" height="835" alt="Image" src="https://github.com/user-attachments/assets/57d6a52a-0549-4359-803e-3a4aadcf4273" />