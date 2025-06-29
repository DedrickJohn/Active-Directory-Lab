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

Pre setup: TBA (includes the installation of windows, Splunk, kali, the setup of Sysmon and the Splunk Universal Forwarder) 

2: This shows the completed configuration of my own local domain through the use of Windows Server manager. Through Windows Server manager I was able to add a new group for the purposes of this lab in which I added 2 new users to, one of which Jenny Smith which is the user that the brute force attack will be performed on with the kali linux machine. 
![addedtoDomain](https://github.com/user-attachments/assets/072377f4-c063-4c89-94f0-89dffa3c455b)




3: This shows the IP address of the Kali linux machine ensuring that everything matches the network diagram
![networkconfigkali](https://github.com/user-attachments/assets/19707c62-6355-447c-8c7e-b0b233b5f369)




4: After installing and updating of kali and various features I created a new path where the passwords file would be located. The picture shows the passwords inside the file with the target's Password inside. This txt file will be used with brute forcing tools and RDP to attempt to logon using the targets (Jenny Smith's) credentials. 
![passwords](https://github.com/user-attachments/assets/bbdb4d5f-b3e6-4419-ac9b-4b0673bc5184)




4A: Added users that can connect using RDP, neccessary for the attack to work. 
![rdp](https://github.com/user-attachments/assets/26e06b14-1121-4e85-8976-35a8d0a74a3e)




5: This shows a completed attempt to logon using the targets credentials using the tool hydra in kali linux. You can see it go through the passwords in the lists until it gets to the correct password in which a success is made. This is important as this will show up on the splunk page. 
![hyrdasuccess](https://github.com/user-attachments/assets/43614fba-3bc6-4a45-984a-633a84eae2cc)




6A: Search for telemetry on the jsmith user using the endpoint setup from The Splunk Universal Forwarder and sysmon
![splunklog1](https://github.com/user-attachments/assets/f140490d-0bb1-4d48-b407-e4cc0a3ef1e0)
6B: After narrowing down the results on the telemetry on the jenny smith user (jsmith) we can see in the event codes the codes 4625 and 4624. This includes the attempts to logon from multiple runs of hydra 
![telemetry](https://github.com/user-attachments/assets/4ce7c453-f34d-441b-a4ef-b7814b1ff0cb)
6C: Using the Windows Log Event codes we can figure out what the codes 4625 and 4624 mean. 4625 means an account failed to logon while 4624 means an account successfully logged on. (Note: see problems and solutions for more information as to why code 4624 is greater than 1)
![docue](https://github.com/user-attachments/assets/61d4a3cc-a4c9-4b56-8b84-12ddc940db97)





7A: By expanding the Splunk logs we can see more details on this event code.
![success](https://github.com/user-attachments/assets/74734f6e-80f4-41a1-81f4-99e606ade05d)
7B: From the details we can see where this attack happened from, I can see the workstation (kali) and its IP address. Both of which match the attacker machine used to attack the target. 
![workstation](https://github.com/user-attachments/assets/afff6180-73e4-4ae1-b001-a9e8cf3d04e0)





Problems encountered and how they were solved:
  - Performance
      - Running 4 VM's at once was incredibly taxing on my PC. In order to reduce strain I had to research ways to optimize windows and the VM's so that I could run them simultaneously. Proper management of the VM system settings to turn off any unnessecary functions as well as accurately deciding what VM's needed a certain amount of RAM were used. In addition, setting windows to performance mode using sysdm.cpl > Performance > Settings > Adjust for best performance helped with running 2 windows based VM's at the same time.
  - Network
      - It is incredibly important to double check the network settings and make sure each VM is setup with the proper network adapter through both VirtualBox settings as well as inside the VM. This also links back to performance as I was encountering network issues the less resources I dedicated to my VM's. Ways that I fixed the network issues included: double checking network settings, using ipconfig and ping commands to ensure that there was an open connection, allocating the neccessary amount of resources. 
  - Crowbar
      - The intial plan was to utilize crowbar to perform the attack but after double checking network and RDP settings I could not figure out how to get Crowbar to find a success on the target. As a backup, I used the tool hydra to conduct the attack which worked smoothly.
  - Splunk Search
      - Had a issue searching for telemetry within a certain time frame (such as last 15 minutes), which I theorize could be because of a time inaccuracy on one of the VM's. For now I limited the search to All time and will use the tag and code to narrow the search down.
        
Final Thoughts on this lab: 
  - This was a good introductory lab as it was my first time setting up a home lab environment and documenting my steps. It taught me about the basics of splunk, the importance of being able to analyze logs, how to set up a VM and run multiple at the same time, and expanded upon my knowledge of networks.
  - For future labs I want to improve on my documentation as well as delve into more complex lab environments as I explore more ways to improve my threat detection.

Potential Additional Improvements to Add at a later date: 
 - Switch to a cloud based VM for reduced loads
 - Implement Atomic Red Team to generate more telemetry 





