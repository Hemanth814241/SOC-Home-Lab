# Investigation Report

## Incident Summary

A Splunk real-time alert was triggered after detecting PowerShell executed with the **-EncodedCommand** parameter. Since encoded PowerShell commands are commonly used by attackers to obfuscate scripts and evade detection, the activity required further investigation.

---

## Alert Details

| Field | Value |
|--------|-------|
| Alert Name | Suspicious Encoded PowerShell Execution Detected |
| Severity | Medium |
| Alert Type | Real-time |
| Data Source | Microsoft Sysmon Event ID 1 |
| Host | SOC-WIN10 |
| User | SOCUSER |
| MITRE ATT&CK | T1059.001 - PowerShell |

---

## Investigation Steps

### Step 1 – Alert Validation

The alert was validated by confirming the timestamp, host, user, Sysmon Event ID 1, and the presence of the **-EncodedCommand** parameter in the PowerShell command line.

**Result:** Alert validated successfully.

---

### Step 2 – Sysmon Analysis

Sysmon Event ID 1 confirmed that **powershell.exe** was executed using the **-EncodedCommand** parameter.

Observed:

- User: SOCUSER
- Host: SOC-WIN10
- Parent Process: powershell.exe
- Process ID recorded
- Encoded command identified

---

### Step 3 – PowerShell Script Block Logging

PowerShell Event ID 4104 was reviewed to identify the decoded script.

Decoded Command:

```powershell
Get-Process | Select-Object -First 5
```

The decoded command was determined to be a legitimate administrative PowerShell command.

---

### Step 4 – Child Process Investigation

The PowerShell process was reviewed for any child processes.

**Result:**

No child processes were created.

---

### Step 5 – Network Investigation

The PowerShell process was reviewed for outbound network connections.

**Result:**

No external network communication was observed.

---

## Analyst Findings

The investigation confirmed:

- Encoded PowerShell execution was successfully detected.
- The decoded PowerShell command was legitimate.
- No child processes were spawned.
- No outbound network connections were observed.
- No additional malicious behavior was identified.

---

## Final Verdict

**Classification:** False Positive (Lab Generated Activity)

### Reason

The alert correctly detected PowerShell execution using the **-EncodedCommand** parameter. However, the decoded script executed a legitimate administrative command (**Get-Process | Select-Object -First 5**). The investigation found no malicious child processes, network communication, or additional suspicious activity. The execution was intentionally performed in a controlled home lab to validate the custom Splunk detection rule.