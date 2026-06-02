# Volt Typhoon Forensic Investigation

Threat Hunting • Incident Response • Splunk Analysis • MITRE ATT&CK Mapping

## Overview

This project documents a forensic investigation of a simulated Volt Typhoon intrusion using Splunk.

The objective was to reconstruct the attacker's activities across multiple stages of the cyber kill chain, identify attacker techniques, and map observed behavior to the MITRE ATT&CK framework.

The investigation covered the complete attack lifecycle, including:

* Initial Access
* Persistence
* Execution
* Credential Access
* Discovery
* Lateral Movement
* Collection
* Command and Control (C2)
* Defense Evasion
* Cleanup

This project was completed as part of a cybersecurity threat hunting and incident response exercise.

---

## Tools Used

* Splunk
* Windows Event Logs
* PowerShell
* WMIC
* certutil
* netsh
* wevtutil
* CyberChef

---

## Skills Demonstrated

* Splunk Log Analysis
* Threat Hunting
* Incident Response
* Digital Forensics
* MITRE ATT&CK Mapping
* Windows Event Log Analysis
* PowerShell Investigation
* Credential Theft Detection
* IOC Identification
* Attack Timeline Reconstruction
* Adversary Behavior Analysis

---

## Investigation Summary

The investigation revealed a complete attack chain consistent with techniques publicly associated with Volt Typhoon operations.

The attacker first compromised an administrator account and established persistence through the creation of a new privileged account.

Reconnaissance activities were conducted using WMIC before the attacker extracted Active Directory data using ntdsutil.

Persistence was expanded through deployment of a web shell, while credential access was achieved using Mimikatz against an LSASS memory dump.

The attacker later moved laterally, collected financial records, established command-and-control communications, and attempted to cover their tracks by clearing Windows event logs.

---

## MITRE ATT&CK Techniques Observed

| Technique                          | MITRE ATT&CK ID |
| ---------------------------------- | --------------- |
| Valid Accounts                     | T1078           |
| Create Account                     | T1136           |
| Windows Management Instrumentation | T1047           |
| Credential Dumping                 | T1003           |
| Web Shell                          | T1505.003       |
| Indicator Removal on Host          | T1070           |
| Data Staged                        | T1074           |
| Proxy                              | T1090           |

---

## ATT&CK Coverage

| Tactic | Technique |
|----------|----------|
| Persistence | Create Account |
| Discovery | WMIC Enumeration |
| Credential Access | Credential Dumping |
| Collection | Data Staging |
| Command and Control | Proxy |
| Defense Evasion | Indicator Removal |

## Attack Timeline

1. Initial Access
2. Account Takeover
3. Persistence Established
4. Reconnaissance
5. Credential Access
6. Web Shell Deployment
7. Lateral Movement
8. Data Collection
9. Command & Control
10. Defense Evasion
11. Cleanup
    
## Key Findings

### Initial Access

* Evidence of account compromise through unauthorized password change activity involving Dean's account.

### Persistence

* Creation of a rogue administrator account (**voltyp-admin**).
* Deployment of an ASPX web shell to maintain long-term access.

### Discovery

* WMIC-based environmental reconnaissance across multiple servers.

### Credential Access

* Extraction of the Active Directory database using **ntdsutil**.
* Credential harvesting through Mimikatz execution against LSASS memory dumps.

### Defense Evasion

* Removal of Windows event logs using **wevtutil**.
* Registry cleanup to remove traces of attacker activity.

### Lateral Movement

* Web shell transferred to a secondary server and renamed **AuditReport.jspx**.

### Collection

* Financial records staged for potential exfiltration:

  * 2022.csv
  * 2023.csv
  * 2024.csv

---

## Screenshots

### Initial Access
![Initial Access](screenshots/01-initial-access.png)

### Persistence – Rogue Admin Account
![Persistence](screenshots/02-rogue-admin-account.png)

### Discovery – WMIC Reconnaissance
![WMIC](screenshots/03-wmic-reconnaissance.png)

### Credential Access – NTDS Extraction
![NTDS](screenshots/04-ntds-dump.png)

### Credential Theft – Mimikatz
![Mimikatz](screenshots/05-mimikatz-download.png)

### Web Shell Deployment
![Webshell](screenshots/06-webshell-deployment.png)

### Defense Evasion – Log Clearing
![Logs](screenshots/07-log-clearing.png)

### Lateral Movement
![Lateral Movement](screenshots/08-lateral-movement.png)

### Data Collection
![Collection](screenshots/09-data-collection.png)

## Lessons Learned

This investigation demonstrated how advanced threat actors can operate using legitimate administrative tools rather than traditional malware.

Key takeaways include:

* Behavioral analysis is critical for detecting advanced threats.
* Legitimate Windows utilities can be abused for malicious purposes.
* Credential theft remains one of the most effective attacker objectives.
* Log analysis and timeline reconstruction are essential incident response skills.
* MITRE ATT&CK mapping provides valuable context for detection engineering.

---

## Repository Structure

```text
volt-typhoon-forensic-investigation/
├── screenshots/
├── report/
├── presentation/
└── README.md
```

## Project Outcome

Successfully reconstructed the complete attack lifecycle of a simulated Volt Typhoon intrusion using Splunk log analysis and forensic investigation techniques.

The investigation identified attacker persistence mechanisms, credential theft activities, lateral movement, data collection, command-and-control communications, and defense evasion techniques while mapping findings to the MITRE ATT&CK framework.

## Deliverables

- Investigation Report (PDF)
- Presentation Slides (PPTX)
- Splunk Investigation Screenshots
- MITRE ATT&CK Mapping
- Attack Timeline Reconstruction
  
## Author

**Suganthi THAMILVANAN**

Cybersecurity Student passionate about Threat Hunting, Digital Forensics, Incident Response, and SOC Operations.

GitHub: https://github.com/Suga-thamil

## Conclusion

This investigation provided hands-on experience in threat hunting, incident response, and forensic analysis using Splunk. By reconstructing the attacker timeline and mapping activities to MITRE ATT&CK, the project demonstrated how advanced threat actors can leverage legitimate administrative tools to evade detection and maintain persistence.
Cybersecurity Student | Threat Hunting | Digital Forensics | SOC Analysis

---

This project was created for educational and portfolio purposes as part of a cybersecurity threat hunting and incident response exercise.
