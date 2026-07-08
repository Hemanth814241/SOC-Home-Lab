# Splunk Alert Configuration

## Alert Name

Suspicious Encoded PowerShell Execution Detected

---

## Alert Description

Detects PowerShell processes executed using the **-EncodedCommand** parameter through Sysmon Process Creation (Event ID 1). The alert captures execution context to support SOC investigation and identify potentially obfuscated PowerShell activity.

---

## Alert Type

Real-time

---

## Trigger Condition

- Trigger when: Number of Results
- Condition: Greater than 0
- Time Window: 1 Minute
- Trigger: Once

---

## Alert Actions

- Add to Triggered Alerts

---

## Detection Query

```spl
index=main
source="WinEventLog:Microsoft-Windows-Sysmon/Operational"
EventCode=1
Image="*\\powershell.exe"
CommandLine="*-EncodedCommand*"
| eval Severity="Medium"
| eval MITRE_Technique="T1059.001 - PowerShell"
| table _time host User ParentImage Image CommandLine ProcessId ParentProcessId Severity MITRE_Technique
```

---

## Alert Validation

The alert was successfully triggered after executing an encoded PowerShell command in the lab environment.

The generated alert appeared in Splunk Triggered Alerts and was used for the subsequent investigation.

---

## Severity

Medium

---

## MITRE ATT&CK

| Technique | ID |
|-----------|----|
| Command and Scripting Interpreter: PowerShell | T1059.001 |