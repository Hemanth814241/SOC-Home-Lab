# RDP Brute Force Investigation

## Alert Summary

- Alert Name: RDP Brute Force Detection
- Severity: High
- Status: True Positive

## Attack Details

- Source IP: 192.168.1.7
- Source Host: Kali Linux
- Target IP: 192.168.1.9
- Target Host: SOC-WIN10
- Target User: socuser
- Attack Type: RDP Brute Force

## Evidence

- Windows Security Event ID 4625 (Failed Logon)
- Logon Type: 3
- Total Failed Attempts: 5
- No successful RDP logon (Event ID 4624, Logon Type 10) observed after the failed attempts.

## Analysis

The alert was triggered after five failed RDP authentication attempts were detected from the internal source IP address **192.168.1.7** targeting the user account **socuser** on **SOC-WIN10**. Investigation confirmed that no successful RDP authentication (Event ID 4624 with Logon Type 10) occurred after the failed attempts. Based on the collected evidence, the activity is classified as a **True Positive** because the detection correctly identified a brute-force attack attempt.

## Conclusion

The investigation confirmed a **True Positive** RDP brute-force attempt against the Windows host **SOC-WIN10**. Five failed RDP authentication attempts were observed from the internal host **Kali Linux (192.168.1.7)** targeting the user account **socuser**. No successful RDP logon was identified during the investigation.