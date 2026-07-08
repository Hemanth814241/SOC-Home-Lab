# Project 02 - Encoded PowerShell Detection and Investigation using Splunk & Sysmon

## Overview

This project demonstrates the complete Security Operations Center (SOC) workflow for detecting and investigating PowerShell execution using the **-EncodedCommand** parameter.

A custom Splunk detection rule was developed to identify encoded PowerShell activity, generate a real-time security alert, and support incident investigation using Microsoft Sysmon Process Creation (Event ID 1) and PowerShell Script Block Logging (Event ID 4104).

The investigation followed a structured SOC methodology, including alert validation, evidence collection, log correlation, and incident analysis to determine whether the activity represented malicious behavior or legitimate administrative activity. Based on the collected evidence, the alert was classified as a **False Positive (Lab Generated Activity)**.
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

## Lab Architecture

                Kali Linux
             (Attack Simulation)
                     │
                     ▼
        Windows 10 Endpoint
        (PowerShell Execution)
                     │
             Microsoft Sysmon
                     │
      Splunk Universal Forwarder
                     │
                     ▼
          Splunk Enterprise SIEM
                     │
         Custom Detection Rule
                     │
              Real-Time Alert
                     │
                     ▼
           SOC Investigation
                     │
                     ▼
      False Positive Classification
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
## Investigation Methodology

The alert was investigated using the following workflow:

1. Validate the triggered alert.
2. Review Sysmon Process Creation (Event ID 1).
3. Analyze PowerShell Script Block Logging (Event ID 4104).
4. Investigate child process activity.
5. Review outbound network connections.
6. Correlate evidence from multiple log sources.
7. Classify the incident based on collected evidence.
## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Command and Scripting Interpreter: PowerShell | T1059.001 |

---

## Final Outcome

The custom detection successfully identified encoded PowerShell execution. Investigation confirmed that the activity was intentionally generated within a controlled home lab for testing purposes. No malicious behavior, persistence, child process execution, or network communication was observed. The incident was classified as a **False Positive (Lab Generated Activity)**.

## Key Investigation Evidence

The investigation is supported by screenshots demonstrating:

- Detection Rule Configuration
- Real-Time Alert Configuration
- Triggered Splunk Alert
- Encoded PowerShell Execution
- PowerShell Script Block Logging (Event ID 4104)
- Sysmon Process Creation (Event ID 1)
- Child Process Investigation
- Network Investigation
- Final Investigation Verdict

Refer to the **Screenshots** folder for supporting evidence.
