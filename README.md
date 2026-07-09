# 🛡️ SOC Home Lab

> **A hands-on Security Operations Center (SOC) portfolio demonstrating detection engineering, alert triage, incident investigation, and threat detection using Splunk Enterprise, Microsoft Sysmon, and Windows Event Logs.**

---

# 📖 Overview

Welcome to my SOC Home Lab portfolio.

This repository contains practical SOC projects built in a controlled home lab environment to simulate real-world cyber threats. Each project focuses on developing detection logic, monitoring security events, investigating alerts, correlating evidence from multiple log sources, and documenting the complete incident response process.

The primary objective of this repository is to strengthen practical SOC analyst skills through hands-on experience with SIEM technologies, Windows event analysis, and structured incident investigations.

---

# 🎯 Learning Objectives

- Build practical SOC Analyst skills through hands-on projects.
- Simulate real-world attack scenarios in a controlled lab.
- Develop custom Splunk detection rules.
- Monitor and investigate security alerts.
- Correlate logs from multiple data sources.
- Practice evidence-based incident response.
- Map adversary behavior to the MITRE ATT&CK Framework.
- Produce professional SOC investigation documentation.

---

# 🛠️ SOC Home Lab Environment

| Component | Technology |
|-----------|------------|
| SIEM | Splunk Enterprise |
| Log Forwarder | Splunk Universal Forwarder |
| Endpoint Monitoring | Microsoft Sysmon |
| Operating System | Windows 10 |
| Attacker Machine | Kali Linux |
| Virtualization | VirtualBox |
| Logs | Windows Security Logs, Sysmon, PowerShell Operational Logs |
| Version Control | Git & GitHub |

---

# 📂 SOC Projects

## 🛡️ Project 01 – RDP Brute Force Detection & Investigation

**Status:** ✅ Completed

### Overview

Simulated an RDP brute-force attack from a Kali Linux attacker machine against a Windows 10 endpoint. Developed a custom Splunk detection rule, investigated failed authentication attempts, validated the absence of successful logins, and documented the complete incident response process.

### Skills Demonstrated

- Splunk Enterprise
- Windows Security Event Logs
- Event ID 4625 Analysis
- SPL Query Development
- Alert Triage
- Incident Investigation
- MITRE ATT&CK Mapping

📁 **Project Folder:** `Project-01-RDP-BruteForce`

---

## 🛡️ Project 02 – Encoded PowerShell Detection & Investigation

**Status:** ✅ Completed

### Overview

Developed a custom Splunk detection rule to identify PowerShell execution using the **-EncodedCommand** parameter. Investigated the generated alert using Microsoft Sysmon Process Creation (Event ID 1) and PowerShell Script Block Logging (Event ID 4104), correlated evidence, and classified the incident based on the investigation findings.

### Skills Demonstrated

- Splunk Enterprise
- Microsoft Sysmon
- PowerShell Investigation
- Detection Engineering
- Alert Validation
- Log Correlation
- False Positive Analysis
- MITRE ATT&CK Mapping

📁 **Project Folder:** `Project-02-Encoded-PowerShell-Detection`

---

# 🚧 Upcoming Projects

- 🔄 Project 03 – Credential Dumping Detection & Investigation
- 🔄 Project 04 – Persistence Detection
- 🔄 Project 05 – Malware Investigation
- 🔄 Project 06 – Phishing Investigation
- 🔄 Project 07 – Lateral Movement Investigation
- 🔄 Project 08 – Command & Control Detection
- 🔄 Project 09 – Data Exfiltration Detection
- 🔄 Project 10 – Ransomware Investigation

---

# 🧠 Skills Demonstrated

| Category | Skills |
|----------|--------|
| SIEM | Splunk Enterprise |
| Detection Engineering | SPL Query Development, Alert Creation |
| Log Analysis | Windows Event Logs, Microsoft Sysmon |
| Incident Response | Alert Validation, Investigation, Incident Documentation |
| Threat Hunting | Evidence Correlation, IOC Analysis |
| MITRE ATT&CK | Threat Mapping |
| Operating Systems | Windows 10, Kali Linux |
| Version Control | Git, GitHub |
| Documentation | Investigation Reports, Technical Documentation |

---

# 💻 Technologies Used

- Splunk Enterprise
- Splunk Universal Forwarder
- Microsoft Sysmon
- Windows Event Logs
- PowerShell Operational Logs
- Windows 10
- Kali Linux
- VirtualBox
- Git
- GitHub

---

# 🚀 SOC Learning Roadmap

| Status | Project |
|--------|---------|
| ✅ | Project 01 – RDP Brute Force Detection & Investigation |
| ✅ | Project 02 – Encoded PowerShell Detection & Investigation |
| ⏳ | Project 03 – Credential Dumping Detection |
| ⏳ | Project 04 – Persistence Detection |
| ⏳ | Project 05 – Malware Investigation |
| ⏳ | Project 06 – Phishing Investigation |
| ⏳ | Project 07 – Lateral Movement Investigation |
| ⏳ | Project 08 – Command & Control Detection |
| ⏳ | Project 09 – Data Exfiltration Detection |
| ⏳ | Project 10 – Ransomware Investigation |

---

# 📈 Current Portfolio Progress

- ✅ 2 SOC Investigation Projects Completed
- 🛠️ Custom Splunk Detection Rules Developed
- 🔍 Hands-on Windows Event & Sysmon Analysis
- 📑 Professional Investigation Documentation
- 🎯 Building a complete SOC Analyst portfolio through practical home lab projects

---

# 📬 Contact

- **GitHub:** https://github.com/Hemanth814241
- **LinkedIn:** https://www.linkedin.com/in/hemanth814241/
