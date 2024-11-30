# Azure Sentinel Honeypot: Global RDP Attack Detection

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/a2d9748f-6833-400d-90b0-d9742f71c30d" alt="SIEM Project Overview" style="border: 2px solid #000; border-radius: 5px;">
</div>


## Overview

This Detection project is aimed to establish a controlled environment for simulating and detecting cyber attacks using Azure Sentinel. The primary focus was to ingest and analyze logs within the Microsoft's Azure SIEM, specifically monitoring live RDP brute force attacks from around the world. Additionally, a custom PowerShell script was utilized to look up attackers' geolocation information and plot it on the Azure Sentinel Map. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Utilized 

- Applied advanced SIEM concepts and practical expertise with Azure Sentinel.
- Analyzed and interpreted network logs within a cloud environment.
- Identified and generated attack signatures and patterns, focusing on RDP brute force attempts.
- Utilized knowledge of network protocols, security vulnerabilities, and geographic attack analysis.
- Demonstrated critical thinking and problem-solving in cybersecurity scenarios.
- Automated incident responses using Azure Playbooks.

### Tools Used

- **Azure Sentinel**: For log ingestion, analysis, and visualizing attack patterns on a map.
- **Azure Log Analytics Workspace (LAW)**: For collecting and analyzing logs from the VM.
- **Virtual Machine (VM)**: Used as a honeypot to attract and log brute force attack attempts.
- **PowerShell Script**: Custom script to retrieve geolocation data for attack visualization.
- **Geolocation.io API**: Service to convert IP addresses into geographical locations.
- **Azure Playbooks**: Automated incident response to alert on repeated failed login attempts.


## Steps

1. **Setup Azure Subscription and Virtual Machine (VM)**
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

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/a2d9748f-6833-400d-90b0-d9742f71c30d" alt="SIEM Project Overview" style="border: 2px solid #000; border-radius: 5px;">
</div>

*Ref 1: Network Diagram*
- Description: This network diagram illustrates the flow of data and actions in the SIEM project. It begins with **cyber attackers** targeting a **vulnerable virtual machine (VM)**. The VM, acting as a honeypot, logs all access attempts and forwards these logs to **Azure Log Analytics Workspace (LAW)**. The data from LAW is then ingested into **Azure Sentinel** for real-time analysis.

Azure Sentinel processes the incoming data, and two key actions are highlighted in the diagram:
1. **Email Alerts**: When Azure Sentinel detects ten failed login attempts from a single IP address, it triggers an alert that is sent to an email server, notifying the user of potential malicious activity.
2. **Geolocation Visualization**: Simultaneously, the IP addresses of attackers are plotted on a **heat map** within Azure Sentinel, providing a visual representation of the geographical distribution of the RDP brute force attempts.

This diagram encapsulates the flow of attack data from the initial compromise attempt through to the automated responses and visual analysis, showcasing the project's comprehensive approach to threat detection and response.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/9f1c1dcc-aea3-49e7-aec3-9cc894548b4e" alt="SIEM Project Overview" style="border: 2px solid #000; border-radius: 5px;">
</div>

*Ref 2: Azure Sentinel Map*
- Description: The Azure Sentinel heat map visually represents the geographical locations of IP addresses attempting to initiate Remote Desktop Protocol (RDP) connections to the vulnerable virtual machine (VM). Each point on the map corresponds to an IP address from which a login attempt was made.

### Key Features:
- **Geolocation Data**: The heat map uses geolocation data to accurately plot the origin of each IP address, allowing for a global view of where attack attempts are coming from.
- **Intensity Indicators**: The map utilizes color intensity to indicate the frequency of login attempts from specific regions. Hotter, more intense colors represent areas with higher concentrations of attack traffic.
- **Real-Time Visualization**: The map updates in real-time, providing an ongoing view of current attack patterns as they unfold.

This heat map is a critical component of the SIEM setup, enabling quick identification of potential threat sources and helping to inform defensive strategies based on the geographic distribution of attackers.

<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/7aae2869-2547-40a9-8a85-002297160f8c" alt="SIEM Project Overview" style="border: 2px solid #000; border-radius: 5px;">
</div>

*Ref 3: PowerShell Script Output*
- Description: This PowerShell script is designed to enhance the monitoring capabilities of the SIEM setup by using a third-party API to gather geolocation data for IP addresses involved in failed RDP login attempts.

### Key Features:
- **Event Filtering**: The script filters failed RDP login events from the Windows Event Viewer.
- **Geolocation API Integration**: For each failed login attempt, the script uses the [ipgeolocation.io](https://ipgeolocation.io/) API to retrieve the geographical location (latitude, longitude, state, and country) of the attacker's IP address.
- **Custom Log Creation**: The script generates a custom log file that stores the geolocation data along with details of the failed login attempt, including the timestamp, source IP, and destination host.
- **Sample Logs for Training**: It also creates sample log entries to assist with the training of extraction features in Azure Log Analytics Workspace.

This script automates the process of enriching RDP brute force attack data with geolocation information, which is then visualized on a heat map within Azure Sentinel.


<div style="text-align: center;">
  <img src="https://github.com/user-attachments/assets/1a831ef8-b00b-4ecf-b706-aaab3beb307e" alt="SIEM Project Overview" style="border: 2px solid #000; border-radius: 5px;">
</div> 

*Ref 4: Email Alerts*
- Description: To enhance the incident response capabilities of the SIEM setup, Azure Playbooks are configured to automatically send email alerts upon detecting suspicious activity.

### How It Works:
- **Trigger Condition**: The Playbook is triggered when Azure Sentinel detects ten consecutive failed RDP login attempts from a single IP address. This threshold is set to minimize false positives while identifying potential brute force attacks.
- **Automated Response**: Once triggered, the Playbook automatically sends an email alert to the specified recipients. The email contains details of the incident, including the IP address involved, the number of failed attempts, and the timestamp of the activity.
- **Integration with Azure Sentinel**: The Playbook is seamlessly integrated with Azure Sentinel, ensuring that critical security events are immediately flagged and communicated to the security team for further investigation.

This automation ensures that security teams are promptly notified of potential threats, allowing for quick action to mitigate risks.

