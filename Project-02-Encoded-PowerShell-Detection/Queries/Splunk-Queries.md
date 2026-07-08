# Splunk Queries

This document contains the Splunk Search Processing Language (SPL) queries used during the detection and investigation of Encoded PowerShell execution.

---

# 1. Detection Query

Purpose:

Detect PowerShell processes executed using the **-EncodedCommand** parameter.

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

# 2. PowerShell Script Block Logging

Purpose:

Review the decoded PowerShell script executed.

```spl
index=main
source="WinEventLog:Microsoft-Windows-PowerShell/Operational"
EventCode=4104
```

---

# 3. Child Process Investigation

Purpose:

Identify whether PowerShell spawned additional processes.

```spl
index=main
source="WinEventLog:Microsoft-Windows-Sysmon/Operational"
EventCode=1
ParentProcessId=<PowerShell Process ID>
| table _time Image CommandLine ParentImage ProcessId ParentProcessId User
```

---

# 4. Network Investigation

Purpose:

Identify outbound network connections initiated by the PowerShell process.

```spl
index=main
source="WinEventLog:Microsoft-Windows-Sysmon/Operational"
EventCode=3
ProcessId=<PowerShell Process ID>
| table _time Image DestinationIp DestinationHostname DestinationPort Protocol User
```

---

# Investigation Outcome

- Detection triggered successfully.
- Script Block Logging revealed the decoded PowerShell command.
- No child processes were identified.
- No outbound network connections were observed.