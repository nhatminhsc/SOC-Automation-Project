# 🚀 Wazuh → Shuffle → VirusTotal → TheHive → Email Notification

<div align="center">
  <img src="https://img.shields.io/badge/Wazuh-Active-blue?logo=wazuh" alt="Wazuh">
  <img src="https://img.shields.io/badge/Shuffle-SOAR-orange" alt="Shuffle">
  <img src="https://img.shields.io/badge/VirusTotal-Threat%20Intel-green" alt="VirusTotal">
  <img src="https://img.shields.io/badge/TheHive-Incident%20Response-yellow" alt="TheHive">
</div>

---

## 📌 Overview
This project demonstrates an **automated alert enrichment and case creation** workflow using:
- 🛡 **Wazuh** – Security Information and Event Management (SIEM)  
- ⚡ **Shuffle SOAR** – Automation & Orchestration  
- 🧠 **VirusTotal** – Threat Intelligence Lookup  
- 🐝 **TheHive** – Incident Response Case Management  
- 📧 **Email Service** – Notification Delivery  

When Wazuh detects an event, it triggers a **Shuffle Webhook** → Enrichment via VirusTotal → Case creation in TheHive → Email notification.

📄 **Full write-up**: [HackMD Documentation](https://hackmd.io/CazsmsEeQFixYyIZ101iKg)

---

## 🔄 Workflow Steps
1. **Wazuh** generates an alert.  
2. The alert is sent to **Shuffle** via a Webhook Trigger.  
3. If it is a **hash**, perform a VirusTotal **File Lookup**.  
4. Create a **case** in **TheHive**.  
5. Send an **email notification**.  
