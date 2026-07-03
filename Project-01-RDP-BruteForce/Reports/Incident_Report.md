# Incident Report

## Incident Summary

- Incident Name: RDP Brute Force Attack
- Severity: High
- Classification: True Positive
- Status: Closed

## Incident Details

- Date: 03 July 2026
- Source Host: Kali Linux
- Source IP: 192.168.1.7
- Target Host: SOC-WIN10
- Target IP: 192.168.1.9
- Target User: socuser

## Impact Assessment

- Five failed RDP authentication attempts were detected.
- No successful RDP authentication was observed.
- No evidence of unauthorized access was identified.
- The activity is consistent with an attempted RDP brute-force attack.

## Recommendations

1. Monitor the source IP (192.168.1.7) for additional suspicious activity.
2. Verify whether the activity was authorized or part of an approved security assessment.
3. Escalate the incident to the L2 SOC Analyst for further investigation if the activity is determined to be unauthorized.