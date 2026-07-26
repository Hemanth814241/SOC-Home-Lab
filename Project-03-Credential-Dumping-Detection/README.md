# Project 03 - Credential Dumping Detection & Investigation

## Overview

This project demonstrates the detection and investigation of a Windows Credential Dumping attack using Splunk Enterprise and Sysmon. The investigation focuses on identifying malicious access to the LSASS process through ProcDump and analyzing the generated telemetry.

## Technologies Used

- Splunk Enterprise
- Sysmon
- Splunk Universal Forwarder
- Windows 10 Virtual Machine
- ProcDump

## Project Objective

The objective of this project is to detect and investigate a Credential Dumping attack by analyzing Sysmon logs in Splunk and documenting the complete incident investigation process.

## Lab Environment

- **Host Machine:** Windows 11
- **SIEM:** Splunk Enterprise
- **Victim Machine:** Windows 10 VM
- **Endpoint Monitoring:** Sysmon
- **Log Forwarding:** Splunk Universal Forwarder
- **Attack Tool:** ProcDump

## Architecture

```text
+-------------------------+
| Windows 10 Virtual Lab  |
| Sysmon                  |
| Splunk UF               |
+------------+------------+
             |
      Windows Event Logs
             |
             ▼
+-------------------------+
| Splunk Enterprise       |
| Detection               |
| Investigation           |
+-------------------------+
```
## Attack Scenario

A credential dumping attack was simulated using ProcDump to access the LSASS process. Sysmon captured the activity, and the logs were forwarded to Splunk Enterprise for detection and investigation.

## Detection Logic

The attack was detected using a custom Splunk search that monitored Sysmon Event IDs related to process creation, process access, and file creation.

### Splunk Detection Query

```spl
index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational"
(EventCode=1 OR EventCode=10 OR EventCode=11)
| search Image="*procdump64.exe" OR SourceImage="*procdump64.exe"
| table _time EventCode Image SourceImage TargetImage TargetFilename ProcessGuid
```

## Investigation Summary

- Event ID 1 – Process Creation (ProcDump execution)
- Event ID 10 – Process Access (LSASS access)
- Event ID 11 – File Creation (LSASS dump file)
- Incident Status – True Positive

## Skills Demonstrated

- Splunk SIEM
- Sysmon Log Analysis
- Windows Event Log Analysis
- Threat Detection
- Incident Investigation
- Threat Hunting

## Conclusion

This project demonstrates the complete detection and investigation of a Credential Dumping attack using Splunk and Sysmon. It highlights the process of identifying malicious activity, correlating security events, and documenting findings using SOC investigation methodologies.

## Screenshots

### 1. Detection Rule Development

![Detection Rule Development](Screenshots/01-Detection-Rule-Development.png)

### 2. Triggered Alerts

![Triggered Alerts](Screenshots/02-Splunk-Triggered-Alerts.png)

### 3. Alert Overview

![Alert Overview](Screenshots/03-Splunk-Alert-Overview.png)

### 4. Detection Results

![Detection Results](Screenshots/04-LSASS-Access-Detection-Results.png)

### 5. Event Correlation

![Event Correlation](Screenshots/05-Credential-Dumping-Event-Correlation.png)

### 6. Event ID 1 - ProcDump Process Creation

![Event ID 1](Screenshots/06-EventID10-LSASS-Process-Access.png)

### 7. Event ID 10 - LSASS Process Access

![Event ID 10](Screenshots/07-EventID1-ProcDump-Process-Creation.png)

### 8. Event ID 11 - Dump File Creation

![Event ID 11](Screenshots/08-EventID11-LSASS-Dump-File-Creation.png)