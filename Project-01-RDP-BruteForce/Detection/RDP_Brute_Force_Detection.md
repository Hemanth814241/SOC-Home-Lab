# RDP Brute Force Detection

## Objective

Detect multiple failed RDP authentication attempts using Windows Security Event ID 4625 and generate a Splunk alert when the defined threshold is exceeded.

## Detection Query

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4625 Logon_Type=3
| stats count by Account_Name, Source_Network_Address, ComputerName
| where count >= 5
```

## Detection Criteria

- Log Source: Windows Security Logs
- Event ID: 4625 (Failed Logon)
- Logon Type: 3
- Threshold: 5 failed authentication attempts
- Time Window: 5 minutes
- Alert Type: Scheduled Splunk Alert