# Wazuh SIEM Home Lab

## Overview
Built a fully functional enterprise SIEM environment using 
Wazuh to simulate real-world security monitoring, alert 
triage, and incident response workflows.

## Environment
- **SIEM Server:** Wazuh v4.7.5 on Ubuntu Server 22.04 LTS
- **Monitored Endpoint:** Windows 11 Home (Wazuh Agent v4.7.5)
- **Virtualization:** Oracle VirtualBox
- **Network:** Bridged adapter — both machines on same subnet

## What I Built
- Deployed Wazuh all-in-one installation on Ubuntu Server VM
- Connected Windows 11 endpoint as a monitored agent
- Configured firewall rules to allow agent-to-server 
  communication on ports 1514, 1515, and 443
- Configured File Integrity Monitoring (FIM) to monitor 
  directories in real time
- Verified real-time log ingestion, alert generation, 
  and incident documentation

## Simulations Performed

### 1. Brute Force Authentication Attack
Simulated repeated failed login attempts to trigger 
authentication failure alerts. Wazuh detected and 
categorized the activity under:
- MITRE ATT&CK T1078 (Valid Accounts)
- MITRE ATT&CK T1531 (Account Access Removal)
- Tactics: Initial Access, Persistence, Privilege 
  Escalation, Defense Evasion

### 2. Network Reconnaissance
Ran Nmap port scan from the Ubuntu server against the 
Windows endpoint to simulate external reconnaissance 
activity. Open ports discovered and logged.

### 3. Windows Security Baseline Check
Wazuh automatically ran CIS Microsoft Windows 11 
Enterprise Benchmark checks against the endpoint, 
identifying 258 failed controls with an overall 
security score of 33%.

### 4. File Integrity Monitoring — Malware Payload Simulation
Configured Wazuh FIM to monitor a local directory in 
real time. Simulated a complete malware payload lifecycle:
- File creation detected (Rule 554, Level 5)
- File modification and integrity checksum change 
  detected (Rule 550, Level 7)
- File deletion detected (Rule 553, Level 7)
- Secondary file introduction detected (Rule 554, Level 5)

All four events captured within a 6-minute window — 
consistent with real-world malware dropper behavior.

## Alerts Generated
- Authentication failures mapped to MITRE ATT&CK 
  T1078/T1531 and PCI DSS 10.2.5
- Windows security events mapped to PCI DSS 2.2 and 2.2.5
- FIM events capturing complete file lifecycle activity
- 400+ total alerts across Persistence, Defense Evasion, 
  Privilege Escalation, and Initial Access tactic categories

## Incident Reports
- **IR-001-Brute-Force.txt** — Brute force authentication 
  attack analysis and disposition
- **IR-002-FIM-Detection.txt** — File integrity monitoring 
  malware payload simulation analysis and disposition

## Screenshots
- **agent-active-status.png** — Windows-Endpoint active 
  with 100% agent coverage
- **windows-endpoint-dashboard.png** — MITRE ATT&CK 
  tactics and PCI DSS compliance mapping
- **mitre-attack-mapping.png** — Full MITRE ATT&CK 
  dashboard showing 5 tactic categories
- **fim-events-dashboard.png** — FIM detection showing 
  complete file lifecycle events
- **security-events-report.pdf** — Exported Wazuh 
  security events report

## Skills Demonstrated
- SIEM deployment and configuration (Wazuh)
- Security alert triage and analysis
- MITRE ATT&CK framework mapping
- PCI DSS compliance monitoring
- File Integrity Monitoring configuration and analysis
- Incident documentation and reporting
- Linux server administration (Ubuntu)
- Network security monitoring
- Windows endpoint security
- Malware behavior pattern recognition

## Tools Used
- Wazuh SIEM
- Nmap
- VirtualBox
- Ubuntu Server 22.04 LTS
- Windows 11
- PowerShell
