# SOC Investigation Report — Windows Failed Logon Event (Event ID 4625)

## 1. Incident Overview

| Field | Details |
|---|---|
| Investigation ID | SOC-INV-001 |
| Incident Type | Failed Authentication |
| Event ID | 4625 |
| Severity | Investigative / Low (single observed event) |
| Platform | Windows 11 |
| SIEM | Wazuh |
| Endpoint Agent | Windows-11-SOC-Lab |
| Status | Investigated |
| Investigation Date | 19 November 2026 |

## 2. Objective

The objective of this investigation was to identify, collect, and analyze a Windows failed logon security event using Wazuh SIEM.

The investigation was performed to validate Windows endpoint log collection and demonstrate a basic SOC monitoring and investigation workflow.

## 3. Detection

A Windows Security Event ID 4625 was identified in the Wazuh Dashboard.

**Event ID 4625 indicates a failed logon attempt.**

The event was successfully collected from the monitored Windows endpoint and displayed in Wazuh Document Details.

## 4. Observed Event Details

| Field | Observed Value |
|---|---|
| Agent ID | 001 |
| Agent Name | Windows-11-SOC-Lab |
| Agent IP | 192.168.56.1 |
| Event ID | 4625 |
| Authentication Package | Negotiate |
| Logon Process | User32 |
| Logon Type | 2 |
| IP Address | 127.0.0.1 |
| IP Port | 0 |
| Process ID | 0x20 |
| Process Name | `C:\Windows\System32\svchost.exe` |
| Status | 0xc000006d |
| SubStatus | 0xc000006a |

## 5. Event Analysis

### Event ID 4625 — Failed Logon

This event records a failed authentication attempt on a Windows system.

Failed authentication events may occur because of:

- Incorrect passwords
- Mistyped credentials
- Authentication configuration issues
- Automated authentication attempts
- Password spraying or brute-force activity

### Logon Type 2

The observed logon type was **2**, which corresponds to an interactive logon.

### IP Address

The event contained the IP address:

`127.0.0.1`

This is the localhost address, indicating that the event involved local system context rather than identifying a remote external IP address.

### Status and SubStatus

The event included:

- Status: `0xc000006d`
- SubStatus: `0xc000006a`

These codes are associated with a failed logon, with the substatus commonly indicating an incorrect password.

### Process Information

The observed process was:

`C:\Windows\System32\svchost.exe`

This is a Windows system process used to host services. The process name alone does not establish malicious activity.

## 6. Investigation Findings

The investigation confirmed that:

1. The Windows 11 endpoint was successfully enrolled in Wazuh.
2. The Wazuh Agent was communicating with the SIEM environment.
3. Windows security events were being collected.
4. Event ID 4625 was successfully detected.
5. Detailed event information was available for investigation through Wazuh Dashboard.

The observed event was consistent with a failed authentication attempt.

However, a single failed logon event is insufficient to determine whether malicious activity occurred.

## 7. SOC Analyst Assessment

**Assessment: Failed authentication event observed; no confirmed malicious activity established from this event alone.**

Further investigation would be required to determine whether the event was caused by normal user activity, a misconfigured application, or suspicious authentication behavior.

Additional analysis could include:

- Reviewing multiple Event ID 4625 events
- Identifying repeated failed attempts
- Correlating failed logons with successful logons
- Reviewing associated accounts
- Examining event timestamps and frequency
- Investigating related security events

## 8. Investigation Workflow

```text
Windows Endpoint
       |
       v
Windows Security Event Generated
       |
       v
Wazuh Agent Collects Event
       |
       v
Wazuh SIEM Receives and Analyzes Event
       |
       v
Event ID 4625 Identified
       |
       v
Analyst Reviews Event Details
       |
       v
Assessment and Documentation
```

## 9. Evidence

Screenshots documenting this investigation:

- `screenshots/event-4625.png`
- `screenshots/event-details.png`

These screenshots demonstrate event detection and investigation through the Wazuh Dashboard.

## 10. Conclusion

This investigation successfully demonstrated the collection and analysis of Windows failed logon events using Wazuh SIEM.

The exercise provided practical experience with Windows security logs, SIEM event analysis, endpoint monitoring, and basic SOC investigation procedures.

The lab will be expanded with additional security detection scenarios to improve practical threat detection and investigation skills.

---

**Environment:** Personal SOC Home Lab  
**SIEM:** Wazuh  
**Endpoint:** Windows 11  
**Investigation:** Event ID 4625 — Failed Logon
