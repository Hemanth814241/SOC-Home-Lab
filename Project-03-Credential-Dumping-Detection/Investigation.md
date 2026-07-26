# Investigation Report

## Incident Details

| Field | Value |
|-------|-------|
| Incident | Credential Dumping Detection |
| Severity | Critical |
| Status | True Positive |
| Detection Source | Splunk Alert (Sysmon Logs) |

## Incident Summary

A credential dumping attack was detected after `procdump64.exe` accessed the `lsass.exe` process and created an LSASS memory dump file. The activity was identified using Sysmon Event IDs 1, 10, and 11 collected in Splunk. Based on the investigation, the incident was confirmed as a **True Positive**.

## Investigation Timeline

| Event ID | Activity | Status |
|----------|----------|--------|
| 1 | Process Creation (`procdump64.exe`) | Detected |
| 10 | Process Access (`lsass.exe`) | Confirmed |
| 11 | Dump File Creation (`lsass_dump-2.dmp`) | Confirmed |

## Investigation Findings

- `procdump64.exe` was executed successfully.
- The process accessed `lsass.exe`.
- An LSASS memory dump file (`lsass_dump-2.dmp`) was created.
- The activity matched a Credential Dumping attack.

## Evidence Collected

| Evidence | Description |
|----------|-------------|
| Sysmon Event ID 1 | Process Creation of `procdump64.exe` |
| Sysmon Event ID 10 | Access to `lsass.exe` |
| Sysmon Event ID 11 | Creation of `lsass_dump-2.dmp` |

## Root Cause Analysis

The incident occurred because `procdump64.exe` was able to access the `lsass.exe` process and create a memory dump. This indicates that a legitimate administrative tool was misused to perform credential dumping.

## Response Actions

- Isolated the affected endpoint from the network.
- Preserved evidence for forensic investigation.
- Recommended removing unauthorized tools after evidence collection.
- Recommended resetting potentially compromised credentials.

## Lessons Learned

- Monitor access to the LSASS process.
- Restrict the use of administrative tools such as ProcDump.
- Continuously monitor PowerShell activity.
- Implement application control to prevent unauthorized tool execution.