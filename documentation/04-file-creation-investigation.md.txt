Sysmon File Creation Investigation

Investigation Overview
Sysmon Event ID 11 (FileCreate) was reviewed to demonstrate how file creation activity can be monitored through Wazuh.
The purpose of the investigation was to determine whether an observed file creation event represented potentially suspicious activity or expected Windows system behavior.

Observed Event

A Sysmon Event ID 11 event was observed in Wazuh with the following information:

Field	Value
Event ID	11
Target Filename	C:\Windows\SoftwareDistribution\Downloads
Image	C:\Windows\System32\mousocoreworker.exe
User	Mark
Event Time	10:12:12 PM


Analysis

The process associated with the event was:

mousocoreworker.exe

The executable is a Windows component associated with Windows Update activity.


The target location:

C:\Windows\SoftwareDistribution\Downloads

is also associated with Windows Update operations.


The combination of the process and file location provides context suggesting that the activity is related to normal Windows Update behavior.


SOC Analyst Assessment

Classification: Likely Benign / Expected Windows Activity

The event was not automatically classified as malicious simply because Sysmon detected file activity.
Additional context, including the process responsible for the activity and the destination path, was used to assess the event.


Investigation Process
The analysis followed a basic SOC triage workflow:

1.Identify the file creation event.
2.Identify the process responsible for the activity.
3.Review the target file/path.
4.Determine whether the process and path are associated with expected system behavior.
5.Classify the activity based on available evidence.

Conclusion
This investigation demonstrated how Sysmon FileCreate events can provide visibility into endpoint file activity.
It also demonstrated the importance of contextual analysis when reviewing security telemetry. A detected event does not automatically indicate malicious behavior.