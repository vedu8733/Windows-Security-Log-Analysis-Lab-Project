# 🔐 Windows Security Log Analysis – Lab Project

## 📘 Overview

This is a hands-on cybersecurity project I completed  to understand how to analyze **Windows Security Logs** using the built-in Event Viewer.  
The lab simulates real-world scenarios like failed login attempts and account lockouts to help me practice detecting suspicious activity using specific **Event IDs** (e.g., `4624`, `4625`).  
This project is part of my learning path toward becoming a **SOC Analyst**

---

## 🎯 Objective

- Explore and understand how **Windows Security Logs** work  
- Learn to identify important **Event IDs** (e.g., 4624, 4625, 4740)  
- Simulate failed login events and analyze logs step-by-step  
- Gain practical skills required for cybersecurity job roles  

---

## 🧰 Lab Setup

### ✅ Requirements:
- **Operating System**: Windows 10/11 or Windows Server 2019/2022  
- **Tools Used**:
  - 🛠️ Windows Event Viewer (pre-installed)
  - 🖥️ PowerShell
  - 🔑 Administrator Privileges

---

## 📂 What Are Windows Security Logs?

Windows Security Logs keep a detailed record of security-related events on the system. These logs are useful for detecting unauthorized access, policy changes, or unusual user activity. In this project, I focused on the following log types:

| 🔍 Activity                  | 📖 Description                                                           |
|-----------------------------|---------------------------------------------------------------------------|
| 🔑 Successful/Failed Logins  | Tracks both valid and invalid login attempts                             |
| 🔐 Account Lockouts          | Logs when accounts are locked due to repeated wrong password attempts     |
| 📝 Audit Policy Changes      | Captures modifications to security policies                              |
| 👥 Group Membership Changes  | Tracks when users are added/removed from groups                          |
| ⚙️ Privilege Escalation     | Shows when users gain admin or elevated privileges                        |

---

## 🔢 Common Event IDs in Windows Logs

| Event ID | Description                                     |
|----------|-------------------------------------------------|
| `4624`   | ✅ Successful Login                              |
| `4625`   | ❌ Failed Login                                  |
| `4740`   | 🔐 Account Lockout                               |
| `4732`   | 👥 User added to a security-enabled local group  |
| `4672`   | ⚙️ Privileges assigned to new logon (Admin)      |

---

## 🧪 Lab Task – Simulate and Analyze Logs

### 🔹 Step 1: Simulate a Failed Login Attempt

#### ✅ Create a Test User

Open **PowerShell as Administrator**, and run:

```powershell
net user user1 Password123 /add
```


###  Simulate a Failed Login

In the same **PowerShell** window, run the following command to simulate a failed login attempt:

```cmd
net use \\127.0.0.1\IPC$ /user:user1 WrongPassword
```
### 🔹 Step 2: Analyze Logs in Event Viewer

#### 🪟 Open Event Viewer

> 📌 Press `Win + R`, type `eventvwr.msc`, and hit `Enter`  
> This will launch the Windows Event Viewer.

---

#### 📂 Navigate to Logs

Go to the Windows Logs → Security 


---

#### 🔍 Filter by Event ID

Use the **"Filter Current Log..."** option (on the right sidebar) and filter for:

| Event ID | Description            |
|----------|------------------------|
| `4625`   | ❌ Failed Logon         |
| `4624`   | ✅ Successful Logon     |

---

#### 📋 Review Log Details

When you click an event, check the following fields in the **Event Details** pane:

- 👤 **Username** – the user who attempted to log in  
- 🔑 **Logon Type** – how the login attempt was made (e.g., local, network, RDP)  
- 🌐 **Source IP / Network Address** – origin of the login attempt (usually empty for local)  
- 🕒 **Timestamp** – when the event occurred  

---

✅ This step helps simulate how a **SOC Analyst** investigates login activity using logs.  




