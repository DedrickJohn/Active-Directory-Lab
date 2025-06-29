# Active Directory Lab

## Objective

This Active Directoy Lab was created to simulate a realistic enterprise network using Windows infrastructure for hands-on cybersecurity practice. The goal was to deploy, secure, and monitor an Active Directory domain while using a SIEM (Splunk) to detect malicious behavior such as privilege escalation, unauthorized logins, and lateral movement. This lab provided valuable experience in blue-team operations, log correlation, and incident response.

### Skills Learned

- Configuration and hardening of Active Directory (GPOs, auditing, least privilege)
- Ingestion of Windows event logs into Splunk via Universal Forwarder
- Detection of common attack techniques (e.g., brute-force, Pass-the-Hash, Kerberoasting)
- Privilege escalation monitoring and analysis
- User behavior analysis through logon and group membership events
- Building dashboards and alerts in Splunk for continuous monitoring

### Tools Used

- **Splunk** – for centralized log collection, search, and visualization  
- **Windows Server / Active Directory** – core of the simulated enterprise domain  
- **Event Viewer** – for manual log inspection
  
## Steps

*Ref 1: Network Diagram*
![draw2](https://github.com/user-attachments/assets/2cefb5ec-4a18-44cf-9cb1-e64902e8ac02)
