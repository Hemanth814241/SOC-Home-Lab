# Technical Documentation

This document contains the technical details of the detection logic, MITRE ATT&CK mapping, Indicators of Compromise (IOCs), response recommendations, and lessons learned for Project 03.

## Detection Rule

### Splunk Detection Query

```spl
index=main source="WinEventLog:Microsoft-Windows-Sysmon/Operational"
(EventCode=1 OR EventCode=10 OR EventCode=11)
| search Image="*procdump64.exe" OR SourceImage="*procdump64.exe"
| table _time EventCode Image SourceImage TargetImage TargetFilename ProcessGuid
```

## Query Explanation

| Query | Purpose |
|-------|---------|
| `index=main` | Searches the `main` index where Sysmon logs are stored. |
| `source="WinEventLog:Microsoft-Windows-Sysmon/Operational"` | Filters only Sysmon Operational logs. |
| `(EventCode=1 OR EventCode=10 OR EventCode=11)` | Searches for Process Creation, Process Access, and File Creation events. |
| `search Image="*procdump64.exe" OR SourceImage="*procdump64.exe"` | Filters events related to ProcDump. |
| `table ...` | Displays only the relevant fields for investigation. |

## MITRE ATT&CK Mapping

| Tactic | Technique | Technique ID |
|--------|-----------|--------------|
| Credential Access | OS Credential Dumping: LSASS Memory | T1003.001 |

## Indicators of Compromise (IOCs)

| IOC Type | Value |
|----------|-------|
| Process | `procdump64.exe` |
| Target Process | `lsass.exe` |
| Dump File | `lsass_dump-2.dmp` |
| File Path | `C:\Temp\lsass_dump-2.dmp` |
## Response Recommendations

- Isolate the affected endpoint from the network.
- Preserve forensic evidence before remediation.
- Remove unauthorized tools after evidence collection.
- Reset potentially compromised credentials.
- Monitor for additional credential dumping activity.

## Lessons Learned

- Monitor access to the LSASS process.
- Restrict the use of administrative tools such as ProcDump.
- Continuously monitor PowerShell activity.
- Implement application control policies to prevent unauthorized tool execution.