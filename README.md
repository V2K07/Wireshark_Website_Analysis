# **Wireshark Honeypot Traffic Analysis Project**

This project demonstrates how network traffic behaves when interacting with intentionally vulnerable honeypot websites. Using Wireshark, six critical types of packets were captured and analyzed to understand how web communication works at the protocol level.

---

## 🔍 **Project Overview**

The goal of this analysis is to observe:

1. DNS Query Resolution
2. TCP 3-Way Handshake (SYN, SYN/ACK, ACK)
3. HTTP GET Requests
4. HTTP POST Requests (Form Submission)
5. HTTP Server Responses (200 OK, 302 Redirect)
6. HTML Response Body (Unencrypted HTTP Content)

This traffic was captured while interacting with:

```
http://testphp.vulnweb.com/
```

A publicly accessible training/honeypot site used for educational purposes.

---

## 🛠️ **Tools Used**

* **Wireshark** (Packet Capture & Analysis)
* **Browser** (BRAVE)
* **Linux / Windows** host system
* HTTP-based test website (vulnweb)

---

## 📂 **Repository Contents**

* `Wireshark_Honeypot_Analysis_Project.pdf` — Full project documentation
* `screenshots/` — Folder containing all packet screenshots
* `sanitized_capture.pcapng` — *(Optional)* Redacted version of packet capture
* `README.md` — Project description

---

## 📘 **Captured Packet Types**

### **1️⃣ DNS Query**

Used to translate the domain name (`testphp.vulnweb.com`) into an IP address.

Query :
<img width="1920" height="1200" alt="Screenshot From 2025-11-28 22-16-18" src="https://github.com/user-attachments/assets/1b8b4c6b-2e85-445f-bb00-03c3acfd48ef" />

Guery Response :
<img width="1920" height="1200" alt="Screenshot From 2025-11-28 22-17-47" src="https://github.com/user-attachments/assets/7f92c220-38a6-4b5e-9acf-bf059c293db9" />


### **2️⃣ TCP Handshake**

3-way handshake packets establishing a reliable connection:

* SYN

  <img width="1920" height="1200" alt="Screenshot From 2025-11-28 21-56-44" src="https://github.com/user-attachments/assets/0dc349c8-99dd-4a7c-a1bf-e81db536d1a4" />

* SYN/ACK
* ACK
  <img width="1920" height="1200" alt="Screenshot From 2025-11-28 21-56-16" src="https://github.com/user-attachments/assets/a2f341b0-c589-4a71-9290-4435cdcc2a0c" />


### **3️⃣ HTTP GET Request**

Client requesting a webpage:

```
GET /categories.php HTTP/1.1

<img width="1920" height="1200" alt="Screenshot From 2025-11-28 21-57-12" src="https://github.com/user-attachments/assets/11e86813-e3a9-406d-81c9-8bad0058a598" />

```

### **4️⃣ HTTP POST Request**

Form submission containing login parameters:

```
uname=admin&pass=admin

<img width="1920" height="1200" alt="Screenshot From 2025-11-28 22-03-29" src="https://github.com/user-attachments/assets/6f90563a-b6fc-429f-92ec-4c98a4b05e40" />

```

*(Values should be redacted before publishing.)*

### **5️⃣ HTTP Response**

Server responding with HTML data or redirects:

```
HTTP/1.1 200 OK
HTTP/1.1 302 Found

<img width="1920" height="1200" alt="Screenshot From 2025-11-28 22-07-59" src="https://github.com/user-attachments/assets/3838b35a-062c-4f73-866f-01e8bb984f76" />

```

### **6️⃣ HTML Page Content**

Visible because this website uses **HTTP**, not HTTPS.

<img width="1920" height="1200" alt="Screenshot From 2025-11-28 22-07-59" src="https://github.com/user-attachments/assets/3a246ab8-a9aa-432a-bbc3-d4c83c714dd4" />

---

## ⚠️ Security Notes

* This analysis was performed on intentionally vulnerable test sites.

---

## 🎯 **Key Learnings**

* How unencrypted HTTP exposes user data
* How credentials travel through POST requests
* How handshake packets establish connections
* How to inspect real packet flows in Wireshark
* Importance of secure protocols like HTTPS

---

## 🚀 **How to View the Capture**

I included a sanitized `.pcapng` file:

1. Install Wireshark
2. Open the pcap file
3. Apply filters such as:

   ```
   dns
   tcp
   http.request
   http.request.method == "POST"
   ```

---
