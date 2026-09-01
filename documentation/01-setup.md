# Wazuh Windows Endpoint Monitoring & Investigation Lab — Setup

## Overview

This project demonstrates the deployment of a Wazuh-based security monitoring environment for Windows endpoint telemetry and SOC investigation.

The lab consists of an Ubuntu virtual machine running the Wazuh server components and a Windows virtual machine configured as a monitored endpoint.

---

## Lab Architecture

```text
Windows VM
├── Wazuh Agent
├── Windows Security Logs
└── Sysmon
│
│ Endpoint Telemetry
▼
Ubuntu VM
├── Wazuh Manager
├── Wazuh Indexer
└── Wazuh Dashboard
```

## Environment


### Ubuntu VM
The Ubuntu virtual machine hosts the Wazuh server environment, including:

- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard

### Windows VM
The Windows virtual machine acts as the monitored endpoint and contains:

- Wazuh Agent
- Windows Security Event Logging
- Microsoft Sysmon

---

## Objective
The primary objective of this lab was to build an endpoint monitoring environment and demonstrate a basic SOC investigation workflow.

The project focuses on:

- Deploying Wazuh.
- Connecting a Windows endpoint to Wazuh.
- Collecting Windows Security telemetry.
- Collecting Sysmon endpoint telemetry.
- Investigating authentication activity.
- Investigating process and file activity.
- Correlating events and determining whether activity appears benign or suspicious.
- Visualizing endpoint activity through the Wazuh Dashboard.

---

## Network Configuration
The Ubuntu and Windows virtual machines communicate through a VirtualBox NAT Network.
The Windows VM communicates with the Ubuntu Wazuh server as its monitored endpoint.

---

## Security Monitoring Components

### Wazuh

Wazuh was used as the central security monitoring and analysis platform.

### Wazuh Agent

The Wazuh Agent was installed on the Windows VM to collect and forward endpoint security telemetry to the Wazuh Manager.

### Sysmon

Sysmon was used to provide additional endpoint telemetry, including process creation and file creation events.

---

## Project Scope
This project focuses on practical endpoint monitoring and investigation.
The investigations were performed in a controlled lab environment to demonstrate the SOC analysis process.
