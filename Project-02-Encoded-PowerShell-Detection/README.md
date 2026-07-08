# Project 02 - Encoded PowerShell Detection and Investigation using Splunk & Sysmon

## Overview

This project demonstrates how to detect and investigate PowerShell commands executed using the **-EncodedCommand** parameter with Splunk Enterprise and Microsoft Sysmon.

A custom Splunk detection rule was created to identify encoded PowerShell execution, generate a real-time alert, and support incident investigation using Sysmon Process Creation events and PowerShell Script Block Logging.

The investigation included validating the alert, analyzing PowerShell activity, correlating multiple log sources, and determining whether the activity was malicious or benign.

---

## Objectives

- Detect PowerShell executed using the **-EncodedCommand** parameter.
- Build a custom Splunk detection rule.
- Create and configure a real-time Splunk alert.
- Generate PowerShell telemetry in a controlled lab.
- Investigate the triggered alert using Sysmon and PowerShell logs.
- Determine the final incident verdict.
- Document the investigation using SOC analyst methodology.

---

## Lab Environment

| Component | Technology |
|----------|------------|
| SIEM | Splunk Enterprise |
| Log Forwarder | Splunk Universal Forwarder |
| Endpoint Monitoring | Microsoft Sysmon |
| Operating System | Windows 10 |
| Logging | PowerShell Script Block Logging |
| Sysmon Configuration | SwiftOnSecurity Sysmon Config |

---

## Project Workflow

1. Configure Sysmon
2. Enable PowerShell Script Block Logging
3. Configure Splunk Universal Forwarder
4. Build Splunk Detection Rule
5. Create Splunk Alert
6. Execute Encoded PowerShell Command
7. Validate Alert Trigger
8. Investigate Alert
9. Perform Root Cause Analysis
10. Document Findings

---

## Repository Structure

```text
Project-02-Encoded-PowerShell-Detection
│
├── Detection
├── Investigation
├── MITRE
├── Queries
├── Screenshots
├── README.md
└── SUMMARY.md
```

---

## Skills Demonstrated

- Splunk SIEM
- Detection Engineering
- Windows Event Log Analysis
- Microsoft Sysmon
- PowerShell Script Block Logging
- Alert Triage
- Incident Investigation
- MITRE ATT&CK Mapping
- False Positive Analysis
- Security Monitoring

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Command and Scripting Interpreter: PowerShell | T1059.001 |

---

## Final Outcome

The custom detection successfully identified encoded PowerShell execution. Investigation confirmed that the activity was intentionally generated within a controlled home lab for testing purposes. No malicious behavior, persistence, child process execution, or network communication was observed. The incident was classified as a **False Positive (Lab Generated Activity)**.