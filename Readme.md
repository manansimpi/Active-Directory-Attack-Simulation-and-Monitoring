# Active Directory Attack Simulation and Monitoring

## Project Description:
- This project establishes a virtual environment with Active Directory to simulate and monitor security events. Four virtual machines were set up in a NAT network for seamless communication. Key tasks include configuring AD, executing an RDP attack from Kali Linux, and analyzing telemetry in Splunk to understand security responses.


## Objectives
- Create a secure NAT network with four VMs.
- Set up and configure Active Directory.
- Install and configure Splunk for telemetry monitoring.
- Simulate an RDP attack and analyze results in Splunk.

## Scope
- Setting up a NAT network with four VMs.
- Configuring Active Directory on Windows Server 2022.
- Installing and configuring Splunk on Ubuntu for log monitoring.
- Executing an RDP brute-force attack simulation from Kali Linux.
- Analyzing security telemetry and monitoring results in Splunk.

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
- VirtualBox, Active Directory, Splunk, NAT networking.


## Architecture and Design
### System Architecture:
The virtual environment architecture includes four main components:

- Windows 10 Target Machine – Connected to the Active Directory for user access.
- Kali Linux Attacker Machine – Executes RDP brute-force attacks.
- Active Directory Server (Windows Server 2022) – Manages domain and user accounts.
- Splunk Server (Ubuntu) – Monitors and logs attack telemetry in real time.

### Diagrams:

Network Diagram: Attached (diagram illustrates the NAT network layout, showing connectivity between all virtual machines).
System Architecture Diagram: Displays interactions among the Windows 10, Active Directory, Kali Linux, and Splunk VMs.
