# Azure Sentinel Honeypot: Global RDP Attack Detection

![Screenshot 2023-10-20 160615](https://github.com/user-attachments/assets/cf8623f6-ef0c-46af-b775-c6cdc38a6eec)

## Objective

The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks using Azure Sentinel. The primary focus was to ingest and analyze logs within the SIEM system, specifically observing live RDP brute force attacks from around the world. Additionally, a custom PowerShell script was utilized to look up attackers' geolocation information and plot it on the Azure Sentinel Map. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned

- Advanced understanding of SIEM concepts and practical application with Azure Sentinel.
- Proficiency in analyzing and interpreting network logs within a cloud environment.
- Ability to generate and recognize attack signatures and patterns, specifically RDP brute force attempts.
- Enhanced knowledge of network protocols, security vulnerabilities, and geographic attack analysis.
- Development of critical thinking and problem-solving skills in cybersecurity.
- Practical experience in automating incident responses with Azure Playbooks.

### Tools Used

- **Azure Sentinel**: For log ingestion, analysis, and visualizing attack patterns on a map.
- **Azure Log Analytics Workspace (LAW)**: For collecting and analyzing logs from the VM.
- **Virtual Machine (VM)**: Used as a honeypot to attract and log brute force attack attempts.
- **PowerShell Script**: Custom script to retrieve geolocation data for attack visualization.
- **Geolocation.io API**: Service to convert IP addresses into geographical locations.
- **Azure Playbooks**: Automated incident response to alert on repeated failed login attempts.


## Steps

1. **Setup Azure Subscription and Virtual Machine**
    - Created an Azure account and set up a VM to act as a honeypot, logging access attempts.
  
2. **Configure Security and Log Gathering**
    - Allowed all traffic through the VM's firewall and set up Log Analytics Workspace to collect logs.
    - Enabled Azure Security Center for monitoring.

3. **Install and Configure Azure Sentinel**
    - Set up Azure Sentinel for monitoring and analyzing the collected logs.
  
4. **Simulate Attacks and Log Analysis**
    - Simulated failed login attempts and observed the logs in the VM's Event Viewer.
  
5. **Implement Geolocation Mapping**
    - Ran a custom PowerShell script to retrieve geolocation data for the attacks, using the Geolocation.io API.
    - Plotted this data on Azure Sentinel's map for visualization.

6. **Automated Incident Response**
    - Configured an Azure Playbook to automatically send an email alert upon detecting 10 failed login attempts from a single IP address.

## Screenshots

![Screenshot 2023-10-20 160615](https://github.com/user-attachments/assets/cf8623f6-ef0c-46af-b775-c6cdc38a6eec)

*Ref 1: Network Diagram*
- Description: (Insert description explaining the network setup and its purpose.)

![heat map](https://github.com/user-attachments/assets/9f1c1dcc-aea3-49e7-aec3-9cc894548b4e)

*Ref 2: Azure Sentinel Map*
- Description: (Insert description of the map visualization, highlighting key observations from the attacks.)

![powershell failed log](https://github.com/user-attachments/assets/7aae2869-2547-40a9-8a85-002297160f8c)

*Ref 3: PowerShell Script Output*
- Description: (Insert description of the script's output, focusing on the geolocation data obtained.)

![image](https://github.com/user-attachments/assets/1a831ef8-b00b-4ecf-b706-aaab3beb307e)

*Ref 4: Email Alerts*
- Description: (}

