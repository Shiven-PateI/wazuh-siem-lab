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
- Verified real-time log ingestion and alert generation

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
Windows endpoint (10.0.0.4) to simulate external 
reconnaissance activity. Open port 3300 discovered 
and logged.

### 3. Windows Security Baseline Check
Wazuh automatically ran CIS Microsoft Windows benchmark 
checks against the endpoint, identifying security 
configuration gaps.

## Alerts Generated
- Authentication failures mapped to PCI DSS 10.2.5
- Windows security events mapped to PCI DSS 2.2 and 2.2.5
- Real-time alert spike captured during simulation window

## Incident Report
See IR-001-Brute-Force.txt for full incident analysis 
and disposition of the brute force simulation.

## Skills Demonstrated
- SIEM deployment and configuration (Wazuh)
- Security alert triage and analysis
- MITRE ATT&CK framework mapping
- PCI DSS compliance monitoring
- Incident documentation and reporting
- Linux server administration (Ubuntu)
- Network security monitoring
- Windows endpoint security

## Tools Used
- Wazuh SIEM
- Nmap
- VirtualBox
- Ubuntu Server 22.04 LTS
- Windows 11
