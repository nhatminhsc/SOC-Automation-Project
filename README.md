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
2. Alert is sent to **Shuffle** via Webhook Trigger.  
3. **hash** → VirusTotal **File Lookup**    
4. Create a **case** in **TheHive**.  
5. Send an **email notification**.

---

## 📊 Architecture Diagram

```mermaid
flowchart LR
    A[Wazuh Alert] --> B[Shuffle Webhook Trigger]
    B --> C{Is it a hash?}
    C -->|Yes| D[VirusTotal File Lookup]
    D --> E[Create Case in TheHive]
    E --> F[Send Email Notification]

    style A fill:#ffcccc,stroke:#b30000,stroke-width:2px;
    style B fill:#e6f7ff,stroke:#006699,stroke-width:2px;
    style C fill:#fff3cd,stroke:#996600,stroke-width:2px;
    style D fill:#e8ffe8,stroke:#339933,stroke-width:2px;
    style E fill:#fff0f5,stroke:#b30047,stroke-width:2px;
    style F fill:#f0f0f0,stroke:#666666,stroke-width:2px;
