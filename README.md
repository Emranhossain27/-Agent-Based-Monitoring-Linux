# 🛡️ Agent-Based Monitoring: Linux

## **Objective**
The purpose of this lab is to configure an **agent-based Nessus scanner** to identify vulnerabilities on a **Virtual Linux System**.  
By deploying a **Tenable Nessus Agent**, we can monitor system vulnerabilities directly from the **Tenable Cloud portal**, ensuring continuous assessment and visibility.

---

## **Lab Steps**

### **1. Log in to Tenable Cloud**
Access the Tenable Cloud Portal:  
🔗 [https://cloud.tenable.com/](https://cloud.tenable.com/)

Navigate to:  
**Settings → Sensors → Nessus Agents → Agent Groups → +Add Agent Group**  
- Create an agent group (avoid using spaces in the group name).

---

### **2. Create a Triggered Agent Scan**
Go to:  
**Scans → +New Scan → Triggered: Basic Agent Scan**  
- Note down the name of your scan for later reference.

---

### **3. Provision the Nessus Agent**
From the Tenable Cloud Portal:  
**Settings → Sensors → Nessus Agents → +Add Nessus Agent**  

Follow the on-screen instructions to generate your **installation command**.

---

### **4. Connect to the Virtual Linux Machine**
Log into your Linux virtual machine and switch to root privileges:
```bash
sudo -i
```

Then, execute the Nessus Agent installation command (example below):
```bash
curl -H 'X-Key: 58aab372289ac80911e4c5ad40a07b23b5524319f9ff5c010aa50ec625ccf389' 'https://sensor.cloud.tenable.com/install/agent?groups=Emran_Linix_agent' | bash
```

✅ The installation should complete automatically.

---

### **5. Trigger the Scan**
To manually trigger a scan, create a trigger file in the Nessus Agent directory:
```bash
sudo touch /opt/nessus_agent/var/nessus/triggers/hello.lol
```

---

### **6. Verify Agent Status (Optional)**
To confirm that the Nessus Agent service is active and running:
```bash
sudo systemctl status nessusagent.service
```

---

### **7. Confirm Agent Registration**
Return to the Tenable Cloud Portal and navigate to:  
**Settings → Sensors → Nessus Agents**

You should now see your **Linux Agent** listed under your selected group.  
⚙️ *Note: It may take several minutes for vulnerabilities to appear after the agent check-in.*

---

### **8. View Vulnerability Scan Results**
Once the scan completes:
1. Go to **Scans → [Your Triggered Scan Name]**
2. Click **See All Details**
3. Review the list of detected vulnerabilities and related remediation steps.

---

## **Conclusion**
This lab demonstrated how to:
- Deploy and register a **Nessus Agent** on a Linux system  
- Configure **Agent Groups** and **Triggered Scans** in Tenable Cloud  
- Initiate scans and monitor **Agent health status**  
- View and analyze vulnerability findings in the Tenable dashboard  

Agent-based monitoring ensures secure, continuous, and scalable vulnerability detection for modern Linux environments.

---

## **Author**
**Emran Hossain**  
📍 Youngstown, OH  
🔗 [GitHub](https://github.com/EmranHossain27) | [LinkedIn](https://www.linkedin.com/in/emran-hossain-934349257/)
