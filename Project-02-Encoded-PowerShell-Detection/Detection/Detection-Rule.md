# Detection Rule

## Detection Name

Suspicious Encoded PowerShell Execution Detected

---

## Objective

Detect PowerShell processes executed using the **-EncodedCommand** parameter.

Attackers commonly use encoded PowerShell commands to hide malicious scripts, bypass basic security monitoring, and evade detection. This rule identifies PowerShell processes launched with encoded commands for further investigation.

---

## Data Source

- Microsoft Sysmon
- Event ID: 1 (Process Creation)

---

## Detection Logic

The rule searches for Sysmon Process Creation events where:

- The process image is **powershell.exe**
- The command line contains **-EncodedCommand**

---

## Splunk Detection Query

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

## Detection Output

The detection provides the following investigation fields:

- Event Time
- Host
- User
- Parent Process
- PowerShell Process
- Command Line
- Process ID
- Parent Process ID
- Severity
- MITRE ATT&CK Technique

---

## MITRE ATT&CK Mapping

| Technique | ID |
|-----------|----|
| Command and Scripting Interpreter: PowerShell | T1059.001 |

---

## Detection Validation

The detection was validated by executing an encoded PowerShell command in the lab environment.

The alert successfully triggered and captured the expected Sysmon Process Creation event.