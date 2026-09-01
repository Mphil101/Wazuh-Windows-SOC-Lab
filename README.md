Wazuh Windows Endpoint Monitoring & SOC Investigation Lab

Project Overview
This project demonstrates a hands-on Security Operations Center (SOC) lab using Wazuh to monitor and investigate activity from a Windows endpoint.

The lab consists of an Ubuntu virtual machine running the Wazuh server and a Windows virtual machine running the Wazuh Agent and Sysmon.

The goal was to collect Windows security and endpoint telemetry, investigate authentication and endpoint activity, and apply a basic SOC investigation workflow.

Lab Architecture
Windows VM
├── Wazuh Agent
├── Windows Security Events
└── Sysmon
        │
        │ Endpoint Telemetry
        ▼
Ubuntu VM
├── Wazuh Manager
├── Wazuh Indexer
└── Wazuh Dashboard
        │
        ▼
SOC Investigation & Analysis

Objectives

Deploy and configure Wazuh in an Ubuntu virtual machine
Connect a Windows endpoint to Wazuh
Collect Windows Security event telemetry
Integrate Sysmon endpoint telemetry
Verify security events are being ingested into Wazuh
Investigate authentication activity
Investigate process creation activity
Investigate file creation activity
Create a custom Wazuh monitoring dashboard
Document investigations using a SOC analyst workflow

Tools & Technologies
Wazuh
Wazuh Agent
Wazuh Dashboard
Sysmon
Windows Event Viewer
Ubuntu
Windows
VirtualBox

Telemetry Investigated
Event	Source	Purpose
4624	Windows Security	Successful logon
4625	Windows Security	Failed logon
1	Sysmon	Process creation
11	Sysmon	File creation

Investigations
1.Authentication / Brute-Force Simulation

A controlled authentication test was performed by intentionally generating multiple failed Windows logon attempts.

The investigation identified:

Multiple Event ID 4625 failed logons
Target account: Mark
Source IP: 10.0.2.3
Logon Type: 2
A subsequent Event ID 4624 successful logon
Successful logon occurred at approximately 9:20 PM

The activity was classified as a controlled brute-force simulation because the failed authentication attempts were intentionally generated as part of the lab.



2. File Creation Investigation

Sysmon Event ID 11 was reviewed to investigate file creation activity.

One representative event involved:

Process: mousocoreworker.exe
File path: C:\Windows\SoftwareDistribution\Downloads

The activity was assessed as likely benign / expected Windows activity because mousocoreworker.exe is associated with Windows Update and the file path is within the Windows Update directory.



3. Process Creation Investigation

Sysmon Event ID 1 was reviewed to investigate process execution.

A representative event contained:

Process: cmd.exe
Command line: C:\Windows\System32\msiexec /V
Parent process: msiexec
User: Mark
Process ID: 9164

The activity was classified as likely benign / requires context based on the available process path, command line, parent-child relationship, and user context.



Wazuh Dashboard

A custom Wazuh dashboard was created to visualize endpoint activity.

The dashboard includes:
Failed logon counts
Successful logon counts
Process creation by executable
File creation activity over time




Evidence

Screenshots documenting the lab and investigations are available in the screenshots directory.

Examples include:
Wazuh agent status
Successful authentication events
Failed authentication events
Sysmon file creation events
Sysmon process creation events
Custom Wazuh dashboard



Skills Demonstrated

SIEM deployment and configuration
Wazuh
Windows endpoint monitoring
Sysmon telemetry analysis
Authentication event analysis
Brute-force investigation
Process investigation
File activity investigation
Event correlation
SOC alert triage
Benign vs. suspicious activity classification
Security event documentation
Basic incident investigation workflow

Conclusion
This project demonstrates an end-to-end SOC monitoring workflow in a controlled virtual environment.

Windows security and Sysmon telemetry were collected through Wazuh and analyzed to investigate authentication, process, and file activity.

The project emphasizes the importance of examining security events in context rather than automatically treating every event as malicious.