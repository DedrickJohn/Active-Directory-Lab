# Active Directory Lab

Disclaimer: all tools/passwords were used in a virtual environment for education purposes only
## Objective

This Active Directoy Lab was created to simulate a realistic enterprise network using Windows infrastructure for hands-on cybersecurity practice. The goal was to deploy, secure, and monitor an Active Directory domain while using a SIEM (Splunk) to detect malicious behavior such as privilege escalation, unauthorized logins, and lateral movement. This lab provided valuable experience in blue-team operations, log correlation, and incident response.

### Skills Learned

- Configuration of Active Directory (adding users, enabling RDP, making groups)
- Ingestion of Windows event logs into Splunk via Universal Forwarder
- Detection of common attack techniques (brute-force)
- Privilege escalation monitoring and analysis
- Building dashboards and alerts in Splunk for continuous monitoring

### Tools Used

- **Splunk** – for centralized log collection, search, and visualization
- **Splunk Universal Forwarder** - Used to collect data and send to splunk for analysis
- **Sysmon** - Used to help send data
- **Windows Server / Active Directory** – core of the simulated environment 

  
## Steps

1: Network Diagram*
Brief overview of how the network is setup between the splunk server, windows server, attacker machine, and target machine. Includes Ip addresses that were used as well as the connections between the machines and tools used.
![draw2](https://github.com/user-attachments/assets/2cefb5ec-4a18-44cf-9cb1-e64902e8ac02)

1A: Virtual Machine Setup (VirtualBox) 
![vm](https://github.com/user-attachments/assets/aa0d578c-59ac-4383-a59d-71b351dd3a98)

Pre setup: TBA

![addedtoDomain](https://github.com/user-attachments/assets/072377f4-c063-4c89-94f0-89dffa3c455b)
![networkconfigkali](https://github.com/user-attachments/assets/19707c62-6355-447c-8c7e-b0b233b5f369)
![passwords](https://github.com/user-attachments/assets/bbdb4d5f-b3e6-4419-ac9b-4b0673bc5184)
![rdp](https://github.com/user-attachments/assets/26e06b14-1121-4e85-8976-35a8d0a74a3e)
![hyrdasuccess](https://github.com/user-attachments/assets/43614fba-3bc6-4a45-984a-633a84eae2cc)
![splunklog1](https://github.com/user-attachments/assets/f140490d-0bb1-4d48-b407-e4cc0a3ef1e0)
![telemetry](https://github.com/user-attachments/assets/4ce7c453-f34d-441b-a4ef-b7814b1ff0cb)
![4625](https://github.com/user-attachments/assets/f5547508-bb80-4d4b-a931-46c14dee6320)
![success](https://github.com/user-attachments/assets/74734f6e-80f4-41a1-81f4-99e606ade05d)
![workstation](https://github.com/user-attachments/assets/afff6180-73e4-4ae1-b001-a9e8cf3d04e0)

Problems encountered and how they were solved:
  - Performance
      - Running 4 VM's at once was incredibly taxing on my PC. In order to reduce strain I had to research ways to optimize windows and the VM's so that I could run them simultaneously. Proper management of the VM system settings to turn off any unnessecary functions as well as accurately deciding what VM's needed a certain amount of RAM were used. In addition, setting windows to performance mode using sysdm.cpl > Performance > Settings > Adjust for best performance helped with running 2 windows based VM's at the same time.
  - Network
      - It is incredibly important to double check the network settings and make sure each VM is setup with the proper network adapter through both VirtualBox settings as well as inside the VM. This also links back to performance as I was encountering network issues the less resources I dedicated to my VM's. Ways that I fixed the network issues included: double checking network settings, using ipconfig and ping commands to ensure that there was an open connection, allocating the neccessary amount of resources. 

Final Thoughts on this lab: 
  - This was a good introductory lab as it was my first time setting up a home lab environment and documenting my steps. It taught me about the basics of splunk, the importance of being able to analyze logs, how to set up a VM and run multiple at the same time, and expanded upon my knowledge of networks.
  - For future labs I want to improve on my documentation as well as delve into more complex lab environments as I explore more ways to improve my threat detection.






