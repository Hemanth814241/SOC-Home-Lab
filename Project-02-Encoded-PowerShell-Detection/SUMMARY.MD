# Project Summary

## Project Title

Encoded PowerShell Detection and Investigation using Splunk & Sysmon

---

## Objective

Build a custom Splunk detection to identify PowerShell execution using the **-EncodedCommand** parameter, validate the detection through controlled testing, investigate the generated alert, and determine whether the activity represented malicious behavior.

---

## What Was Implemented

- Configured Microsoft Sysmon for endpoint telemetry.
- Enabled PowerShell Script Block Logging (Event ID 4104).
- Forwarded Windows logs to Splunk using Splunk Universal Forwarder.
- Developed a custom Splunk detection rule for encoded PowerShell execution.
- Configured a real-time Splunk alert.
- Executed an encoded PowerShell command to validate the detection.
- Investigated the alert using multiple Windows log sources.

---

## Investigation Summary

The investigation confirmed that the alert correctly detected PowerShell execution using the **-EncodedCommand** parameter.

Evidence collected included:

- Sysmon Event ID 1 (Process Creation)
- PowerShell Event ID 4104 (Script Block Logging)
- Child Process Analysis
- Network Connection Analysis

The decoded PowerShell command was:

```powershell
Get-Process | Select-Object -First 5
```

No child processes, outbound network connections, or additional suspicious behavior were identified.

---

## Final Verdict

**Classification:** False Positive (Lab Generated Activity)

The activity was intentionally generated in a controlled home lab to validate the custom detection rule. The investigation confirmed that the decoded PowerShell command was legitimate and that no malicious behavior occurred.

---

## Skills Demonstrated

- Splunk Enterprise
- Detection Engineering
- Sysmon
- PowerShell Script Block Logging
- Windows Event Log Analysis
- Alert Triage
- Incident Investigation
- Log Correlation
- MITRE ATT&CK Mapping
- False Positive Analysis

---

## Key Learning

This project demonstrates the complete SOC workflow:

Detection → Alert Validation → Investigation → Evidence Correlation → Analyst Assessment → Final Verdict