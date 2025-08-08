# 🔐 Task 4: Firewall Configuration and Rule Management (Windows)

## ✅ Task Objectives

1. Open the firewall configuration tool  
2. List existing firewall rules  
3. Add a rule to block inbound traffic on port 23 (Telnet)  
4. Test the rule locally  
5. (Linux only) Allow SSH on port 22  
6. Remove the test rule  
7. Document steps  
8. Summarize how firewalls filter traffic  

---

## 🖥️ Platform: Windows 10/11

---

### 1. 🛠 Open Firewall Configuration Tool

- Press `Win + R`, type `wf.msc`, then press **Enter**  
- This opens **Windows Defender Firewall with Advanced Security**

---

### 2. 📋 List Current Firewall Rules

- In the left panel, click **Inbound Rules**
- Scroll through the middle panel to view current rules
- Sort by the **Local Port** column and check for port **23**

✅ Port 23 was already blocked in this system

---

### 3. 🚫 Add a Rule to Block Port 23 (if not already blocked)

1. Right-click **Inbound Rules** → **New Rule…**
2. Select **Port** → Next
3. Choose **TCP** and enter `23` → Next
4. Select **Block the connection** → Next
5. Apply to **all profiles** → Next
6. Name it: `Block Telnet Port 23` → Finish

---

### 4. 🧪 Test the Rule

#### Install Telnet (if not installed)

- Go to Control Panel → Programs → Turn Windows features on or off  
- Check **Telnet Client**, click **OK**

#### Test Connection

```cmd
telnet localhost 23
```

✅ Output:
```
Connecting To localhost...Could not open connection to the host, on port 23: Connect failed
```

---

### 5. 🔓 Allow SSH (Linux Only)

> ❌ Skipped – Not required for Windows

---

### 6. ♻️ Remove the Test Rule

- Go to **Inbound Rules** in `wf.msc`
- Find the rule `Block Telnet Port 23`
- Right-click → **Delete**

✅ Restored firewall to original state

---

### 7. 📝 Commands / GUI Steps Summary

#### GUI Steps:
- Open firewall: `Win + R → wf.msc`
- Check rules under **Inbound Rules**
- Create new rule: Port 23 → Block → All Profiles → Name it
- Enable Telnet client
- Test with `telnet localhost 23`
- Remove the rule after test

#### Optional Command-Line:
```cmd
netsh advfirewall firewall add rule name="Block Telnet" dir=in action=block protocol=TCP localport=23
netsh advfirewall firewall delete rule name="Block Telnet"
```

---

### 8. 🔐 Firewall Summary

> A firewall filters network traffic by allowing or blocking connections based on rules.  
> It protects systems by controlling:
> - Port access
> - Application behavior
> - IP traffic  
>  
> In this task, blocking port 23 (Telnet) helped prevent insecure remote access.

---
