# SOC-Home-Lab

## Objective
The aim of this project is to design and implement a comprehensive Security Operations Center (SOC) Home Lab. This environment will facilitate hands-on experience in:
- Threat Detection
- Incident Response
- Security Monitoring
By deploying and configuring various open-source security tools within a cloud-based infrastructure, the lab will simulate real-world scenarios encountered by SOC analysts.

### Skills Learned
Throughout the development and utilization of this SOC Home Lab, the following skills were acquired and honed:

 SIEM Implementation and Log Analysis:
  -  Deploying and configuring the ELK Stack for effective log collection and analysis.
  - Creating dashboards and visualizations in Kibana to monitor security events.

Endpoint Security Management:
  - Setting up Fleet Server to manage Elastic Agents across various endpoints.
  - Utilizing Velociraptor for in-depth endpoint monitoring and threat hunting.
  - Threat Hunting and Incident Response:

Simulating attack scenarios using Mythic C2 and Kali Linux to test detection capabilities.
  - Responding to security incidents and analyzing artifacts to determine the root cause.

Cloud Infrastructure Management:
  - Deploying and managing virtual machines and services in a cloud environment.
  - Configuring network settings, security groups, and storage solutions.

Automation and Scripting:
  - Developing scripts to automate the deployment and configuration of security tools.
  - Automating log collection and alerting processes to enhance efficiency.

Network Security Monitoring:
  - Implementing Security Onion for comprehensive network traffic analysis.
  - Setting up intrusion detection systems to monitor and alert on suspicious activities.

### Tools Used
The lab incorporates the following tools:
- ELK Stack (Elasticsearch, Logstash, Kibana): For centralized log management and analysis.
- Fleet Server: To manage and monitor endpoint agents.
- Velociraptor: For endpoint monitoring, threat hunting, and digital forensics.
- Wazuh: An open-source security monitoring platform for threat detection, integrity monitoring, and incident response.
- Security Onion: A platform for intrusion detection, network security monitoring, and log management.
- Kali Linux: Used for simulating attacks to test detection and response capabilities.
- Mythic C2: A command and control framework for simulating adversary activities.
- OS Ticket Server: For managing security alerts and incident tickets.

## Steps
The following steps outline the process of setting up the SOC Home Lab:
To provide a visual overview of the SOC Home Lab architecture, refer to the network diagram below:

![Network Diagram](https://github.com/kdcervantes/SOC-Home-Lab/blob/main/SOC%20Network%20Diagram.jpg)

### Cloud Environment Setup:
Vultr VPC 2.0 allows me to create a private, isolated network to securely connect all my SOC components.

Step 1: Creating the VPC 2.0 Network
 - Navigated to VPC 2.0 in the Vultr dashboard.
 - Created a new private network with the following details:
 - VPC Name: SOC-Home-Lab
 - CIDR Block: 172.31.0.0/24
 - Subnet Mask: 255.255.255.0
 - IP Range: 172.31.0.1 - 172.31.0.254
 - Enabled private networking for internal communication between SOC components.

Step 2: Configuring Firewall Rules
 - Created security groups for network segmentation.
 - Configured Firewall Rules to restrict traffic between machines:
 - Allow SSH (Port 22) from Analyst Laptop
 - Allow RDP (Port 3389) for Windows Server
 - Allow Fleet Server to communicate with ELK Stack
 - Deny inbound traffic from Attack Laptop to ELK Stack

Step 3: Deploying Virtual Machines
 - With the VPC 2.0 configured, I am now deploying the necessary machines.

Machine	OS	Role	Private IP
 - ELK Stack	Ubuntu 22.04	SIEM & log management	172.31.0.10
 - Fleet Server	Ubuntu 22.04	Endpoint monitoring (Elastic)	172.31.0.11
 - Windows Server	Windows 2022	Log forwarding (RDP enabled)	172.31.0.20
 - Ubuntu Server	Ubuntu 22.04	SSH-enabled logging server	172.31.0.21
 - Mythic C2	Ubuntu 22.04	Attack simulation platform	172.31.0.200
 - OS Ticket	Ubuntu 22.04	Incident management system	172.31.0.30

Next Steps
Now that the Vultr VPC and virtual machines are deployed, the following steps include:

Installing and Configuring ELK Stack for log collection.
Setting up Fleet Server & Elastic Agents for endpoint monitoring.
Deploying Velociraptor for threat hunting.
Configuring network security policies to restrict unauthorized access.

ELK Stack Deployment:
Install Elasticsearch, Logstash, and Kibana on a dedicated VM.
Configure each component to ensure seamless data flow and accessibility.

Fleet Server and Elastic Agent Configuration:
Set up Fleet Server to manage Elastic Agents.
Deploy Elastic Agents on Windows and Linux endpoints to collect logs and metrics.

Velociraptor Deployment:
Install Velociraptor server and configure it for endpoint monitoring.
Deploy Velociraptor agents on endpoints for threat hunting and forensic analysis.

Wazuh Integration:
Set up Wazuh manager and agents for comprehensive security monitoring.
Integrate Wazuh with the ELK Stack for unified analysis.

Security Onion Setup:
Deploy Security Onion for network security monitoring and intrusion detection.
Configure network taps or port mirroring to capture and analyze traffic.

Attack Simulation:
Set up Mythic C2 server to simulate adversary command and control operations.
Use Kali Linux to perform penetration testing and validate detection mechanisms.

Incident Management:
Install OS Ticket Server to manage and track security incidents.
Integrate alerting mechanisms to generate tickets for identified threats.

Monitoring and Alerting:
Develop dashboards in Kibana to visualize security metrics and events.
Set up alerting rules to notify of suspicious activities or policy violations.

Documentation and Continuous Improvement:
Document configurations, processes, and lessons learned throughout the project.
Regularly review and update the lab environment to incorporate new tools and techniques.
