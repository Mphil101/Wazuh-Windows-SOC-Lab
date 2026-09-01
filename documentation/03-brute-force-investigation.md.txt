Brute-Force Authentication Investigation

Investigation Overview
A controlled authentication test was performed against the Windows endpoint to demonstrate how repeated failed logon attempts could be identified and investigated using Wazuh.


Detection

Windows Security Event ID 4625 was used to identify failed authentication attempts.

A total of 11 failed logon attempts were intentionally generated on the Windows endpoint. Windows Event Viewer recorded the events, while Wazuh successfully displayed multiple corresponding 4625 events.


Observed Failed Logon
A representative failed logon event contained the following information:

Field	Value
Event ID	4625
Target Username	Mark
Logon Type	2
Failure Reason	Unknown user or bad password
Source IP	10.0.2.3
Workstation	DESKTOP-MKQCJ1N$
Time	9:09:19 PM
Successful Authentication

Following the failed authentication activity, a successful Windows logon was observed using Event ID 4624.

Field	Value
Event ID	4624
Target Username	Mark
Logon Type	2
Source IP	10.0.2.3
Workstation	DESKTOP-MKQCJ1N$
Time	9:20:13 PM

Timeline

9:09:19 PM
    ↓
4625 — Failed logon

9:09–9:20 PM
    ↓
Additional failed logon attempts

9:20:13 PM
    ↓
4624 — Successful logon

Event Correlation
The failed and successful authentication events were correlated using common attributes including:

Target username
Source IP address
Workstation
Logon type
Event timestamps

The sequence of repeated failed authentication attempts followed by a successful authentication is a pattern that could warrant investigation in a production environment.

SOC Analyst Assessment

The activity was classified as a Controlled Brute-Force Simulation.

Although the event sequence resembles a potential brute-force scenario, the activity was intentionally generated for this lab.


MITRE ATT&CK Mapping
The authentication activity can be associated with:

T1110 — Brute Force
T1078 — Valid Accounts

These techniques provide a framework for describing the observed authentication behavior.

Recommended SOC Response
If similar activity were observed in a production environment, an analyst could:

1.Identify the affected account.
2.Determine the source IP and workstation.
3.Review the authentication timeline.
4.Determine whether the successful authentication was legitimate.
5.Review additional endpoint activity around the successful login.
6.Escalate or contain the activity if compromise is suspected.

Conclusion
The investigation demonstrated how Wazuh can be used to identify failed authentication attempts and correlate them with subsequent successful authentication activity.
The exercise also demonstrated the importance of investigating event sequences and context rather than treating an individual security event as automatically malicious.