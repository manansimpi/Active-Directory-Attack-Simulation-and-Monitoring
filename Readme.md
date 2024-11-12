# Active Directory Attack Simulation and Monitoring

## Project Description:
- This project involves creating a virtual environment with Active Directory (AD) to simulate and monitor security events. Four virtual machines (VMs) were set up in a NAT network for seamless communication. The project focuses on configuring AD, executing an RDP brute-force attack from Kali Linux, and analyzing telemetry in Splunk to observe security responses.


## Objectives
- Establish a secure NAT network with four VMs.
- Set up and configure Active Directory on Windows Server.
- Install and configure Splunk for telemetry monitoring.
- Simulate an RDP brute-force attack and analyze results in Splunk.

## Scope
- Configure a NAT network with four VMs.
- Set up Active Directory on Windows Server 2022.
- Install and configure Splunk on Ubuntu for telemetry and log monitoring.
- Conduct an RDP brute-force attack simulation from Kali Linux.
- Analyze and monitor security telemetry in Splunk.

## Requirements
### Functional Requirements:
- Set up four virtual machines in a NAT network with full communication.
- Configure Active Directory with user accounts and domain connectivity.
- Install Splunk for telemetry collection and monitoring.
- Execute and log an RDP attack from the Kali Linux VM.
### Technical Requirements:
  #### Virtual Operating Systems: 
- Windows 10, Windows Server 2022, Ubuntu, Kali Linux.
  #### Tools: 
- VirtualBox, Active Directory, Splunk, Sysmon.
  #### Protocols:
- RDP, TCP/IP, ICMP.


## Architecture and Design
### System Architecture:
The virtual environment architecture includes four primary components:

1. Windows 10 Target Machine – Connected to Active Directory for user access.
2. Kali Linux Attacker Machine – Executes RDP brute-force attacks.
3. Active Directory Server (Windows Server 2022) – Manages domain and user accounts.
4. Splunk Server (Ubuntu) – Monitors and logs attack telemetry in real-time.

### Network Diagrams:

![Screenshot 2024-11-08 033004](https://github.com/user-attachments/assets/88110a09-8385-455e-96f1-d45bedca7649)


## Implementation
### Setup and Configuration:

1. Install VirtualBox and create each VM.


![Screenshot 2024-10-27 173413](https://github.com/user-attachments/assets/83846721-abc1-4a92-94d0-a0a18f45b14c)

   
2. Set up a NAT network and add all VMs to enable inter-VM communication.


   ![Screenshot 2024-10-27 173413](https://github.com/user-attachments/assets/4a51c0f4-ff90-4575-9d4f-94c356a919a3)



### Ubuntu (Splunk Server) 
- Install Splunk and configure it to start on port 8000 at each startup.

  ![Screenshot 2024-10-27 174557](https://github.com/user-attachments/assets/0e0b535f-104c-43ea-88e6-7cb711557569)

- Enable telemetry logging in Splunk to capture and monitor events.
  
### Windows 10 (Endpoint) 
- Sysmon: Install Sysmon to capture telemetry (e.g., process creation, network connections).
- Use a custom XML file to filter and capture necessary event types in the Windows Event Log.
- Splunk Universal Forwarder: Install and configure it to send Sysmon logs to the Splunk server (Ubuntu) on the designated listening port.
- The forwarder transmits logs to the Splunk indexer for ingestion and storage.
- Ingested telemetry is analyzed in Splunk, allowing for custom dashboards, searches, and alerts based on Sysmon data.


### Splunk Configuration From either Target(Win 10)/Win Server
- Log into the Splunk web interface (http://<SplunkServerIP>:8000).

 ![Screenshot 2024-10-27 174713](https://github.com/user-attachments/assets/eb1b90ae-9e74-4534-abd8-7e252594fc0b)
 
- Go to Settings > Indexes and create a new index (e.g., sysmon) that matches the forwarder configuration.
- Configure the indexer’s listening port to align with the forwarder’s settings.


### Verifiction of Sysmon Data in Splunk:
- In the Splunk web interface, go to Search & Reporting.
- Use the search index="(e.g., sysmon)" to view the ingested Sysmon data from the Windows 10 endpoint.


### Windows Server 2022:
- Install and Configure the Windows Server with the Same configuration done in windows(ie sysmon and Splunk configurations)




### Windows Server 2022 (Active Directory Setup)
- Configure Windows Server as an Active Directory Domain Controller.
- Create two user accounts in different departments (e.g., IT and HR).
- Connect the Windows 10 machine to the AD domain.

  ![Screenshot 2024-10-27 173742](https://github.com/user-attachments/assets/4e3a5ea3-7cc6-48f8-9a56-9f0fa305b071)


  ![Screenshot 2024-10-27 173807](https://github.com/user-attachments/assets/6976a47b-8cc4-416b-b9c9-12bc2fb55c90)


![Screenshot 2024-10-27 174223](https://github.com/user-attachments/assets/d1dac8aa-9396-445e-b8b9-1af37ab8c544)


![Screenshot 2024-10-27 174335](https://github.com/user-attachments/assets/72d1f8db-debf-4b68-93c8-d8cb020555b9)




### Windows 10 Machine(RDP Setup) 
- Enabled RDP for both the Users under the AD Domain.  


### Kali Linux (Attack Simulation)
- Create a dictionary file with real and fake passwords to simulate brute-force attempts.

![Screenshot 2024-10-27 180449](https://github.com/user-attachments/assets/bff213ce-5d45-499c-979a-ca63a0b892a4)


- Use Crowbar on Kali to simulate an RDP brute-force attack on the AD accounts.

  ![Screenshot 2024-10-27 180320](https://github.com/user-attachments/assets/f9706e95-8ede-4c40-8322-9b07fc6e35ac)



### Monitoring in Splunk
- In the Splunk interface, go to Search & Reporting.
- Search the sysmon index to view and analyze telemetry from the RDP attack.

Figure showing the number of times Event code 4625(Failed login Attempts) has logged.
![Screenshot 2024-10-27 180654](https://github.com/user-attachments/assets/77e4c645-3039-4695-8f93-9ce338460456)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Figure shows the account name(lwalsh) with multiple logon's failed indicating a Brute Force attack. 

![Screenshot 2024-10-27 180726](https://github.com/user-attachments/assets/36773ff0-6aa6-4d85-a3df-4dab115c4d97)


-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


Figure showing some indepth description such as the attacker Address,Workstation name and more

![Screenshot 2024-10-27 180834](https://github.com/user-attachments/assets/23778a76-99b0-4087-aeba-36fd1834b467)




- Set up dashboards, custom searches, and alerts for real-time monitoring of Sysmon data.
