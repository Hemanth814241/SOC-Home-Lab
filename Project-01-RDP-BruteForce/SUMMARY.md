# Project Summary

## Attack

A simulated RDP brute-force attack was launched from a Kali Linux machine against a Windows 10 virtual machine.

## Detection

A custom Splunk detection rule monitored Windows Security Event ID 4625 and generated an alert after five failed RDP authentication attempts within five minutes.

## Investigation

The investigation identified:

- Source IP: 192.168.1.7
- Source Host: Kali Linux
- Target IP: 192.168.1.9
- Target Host: SOC-WIN10
- Target User: socuser

The investigation also confirmed that no successful RDP authentication (Event ID 4624) occurred after the failed attempts.

## Classification

**True Positive**

## MITRE ATT&CK

- TA0001 – Initial Access
- T1110 – Brute Force

## Outcome

The detection rule successfully identified the brute-force attack, and the investigation confirmed that the attack did not result in unauthorized access.