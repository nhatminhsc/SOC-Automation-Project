# 🚀 SOC Automation Lab – Wazuh + Shuffle + VirusTotal + TheHive

<div align="center">
  <img src="https://img.shields.io/badge/Wazuh-Active-blue?logo=wazuh" alt="Wazuh">
  <img src="https://img.shields.io/badge/Shuffle-SOAR-orange" alt="Shuffle">
  <img src="https://img.shields.io/badge/VirusTotal-Threat%20Intel-green" alt="VirusTotal">
  <img src="https://img.shields.io/badge/TheHive-Incident%20Response-yellow" alt="TheHive">
</div>

---

## 📌 Overview
This repository contains **two SOC automation workflows** that demonstrate how to integrate **Wazuh**, **Shuffle SOAR**, **VirusTotal**, and **TheHive** to **detect, enrich, and respond** to security threats.  

The two scenarios include:
1. **Mimikatz Detection Workflow** – Detect malicious process execution via Sysmon logs, enrich with VirusTotal, create a case in TheHive, and notify analysts via email.  
2. **SSH Brute Force Active Response Workflow** – Detect repeated failed SSH logins, enrich attacker IP via VirusTotal, prompt analyst approval, and automatically block IP using Wazuh Active Response.

📄 **Full write-up / Blog**: [SOC Automation Lab Blog](https://hackmd.io/@FLFwOI7sTB6F-qAm07OXLQ/SJWVEbtDgx)

---

## 🛠 Components
- 🛡 **Wazuh** – Host-based Intrusion Detection System (HIDS) & SIEM  
- ⚡ **Shuffle SOAR** – Workflow orchestration & automation  
- 🧠 **VirusTotal** – Threat intelligence for IPs, hashes, domains  
- 🐝 **TheHive** – Incident Response & Case Management platform  
- 📧 **Email Service** – Analyst notification channel

---

## 🔄 Workflow Scenarios

### **1️⃣ Mimikatz Detection Workflow**
1. **Wazuh** detects suspicious process execution (Mimikatz) via custom Sysmon rule.
2. Alert is sent to **Shuffle** via Webhook.
3. **Shuffle** extracts file hash using Regex Capture Group.
4. **VirusTotal** performs file hash lookup for threat reputation.
5. **TheHive** creates a new case with alert details and VT enrichment.
6. **Email Notification** sent to SOC analyst.

---

### **2️⃣ SSH Brute Force Active Response Workflow**
1. **Wazuh** detects multiple failed SSH login attempts with rule ID `5710`.
2. Custom aggregation rule (`5764`) triggers when:
   - Same source IP  
   - ≥3 events within 60 seconds  
3. Alert is sent to **Shuffle** via Webhook.
4. **VirusTotal** checks the attacker’s IP reputation.
5. Analyst receives **email prompt** for action:
   - ✅ Approve → Trigger **Wazuh Active Response** to run `firewall-drop` on target agent → Block IP.
   - ❌ Deny → No action taken.
6. **TheHive** creates a case for investigation.

---

## ⚙️ Technologies & Setup
- **Wazuh Manager**: Deployed on DigitalOcean VM.  
- **Wazuh Agents**: Installed on Windows (Sysmon logs) & Ubuntu (SSH target).  
- **TheHive**: Deployed on DigitalOcean VM.  
- **Shuffle SOAR**: Cloud platform for workflow execution.  
- **VirusTotal API**: Public/Enterprise API for enrichment.  

---

## ✅ Key Features
- **Custom Wazuh Rules** for Sysmon Event ID 1 (process creation) & SSH brute force correlation.
- **Automated Enrichment** with VirusTotal for both file hashes & IPs.
- **Incident Case Creation** in TheHive for analyst tracking.
- **Email Notification** for SOC analyst review.
- **Active Response** to automatically block malicious IPs via `firewall-drop`.

---

## 📚 References
- [Wazuh Documentation](https://documentation.wazuh.com/current/index.html)  
- [TheHive Project Documentation](https://docs.strangebee.com/thehive/)  
- [Shuffle SOAR](https://shuffler.io)  
- [VirusTotal API Reference](https://developers.virustotal.com/)  

---

## 🏁 Conclusion
This lab demonstrates how to build an **end-to-end SOC automation pipeline** to:
- Detect threats from endpoint logs
- Enrich with threat intelligence
- Notify and involve analysts
- Take automated containment actions

By combining **SIEM + SOAR + Threat Intel + IR Platform**, you can drastically reduce **Mean Time to Detect (MTTD)** and **Mean Time to Respond (MTTR)** in real-world security operations.
