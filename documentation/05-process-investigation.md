# Sysmon Process Creation Investigation

## Investigation Overview

Sysmon Event ID 1 (Process Creation) was reviewed to demonstrate how newly created processes can be monitored and investigated through Wazuh.

The goal was to examine the process, command line, parent process, and user context to determine whether the activity appeared suspicious or benign.

---

## Observed Event

A representative Sysmon Event ID 1 event was observed in Wazuh.

| Field | Value |
|---|---|
| Event ID | 1 |
| Image | `C:\Windows\System32\cmd.exe` |
| Command Line | `C:\Windows\System32\msiexec /V` |
| Parent Image | `C:\Windows\System32\msiexec` |
| User | Mark |
| Process ID | 9164 |
| Event Time | 09:54:52 AM |

![EventID 1](<../screenshots/VirtualBox wazuh process creation.png>)

---

## Analysis

The process image was:

`C:\Windows\System32\cmd.exe`

The command line referenced:

`C:\Windows\System32\msiexec /V`

The parent process was also:

`C:\Windows\System32\msiexec`

Both executables were located under the Windows System32 directory.

The presence of `msiexec.exe` and `cmd.exe` can occur during software installation or other legitimate Windows activity. However, process creation events should be reviewed in context because command-line execution can also be associated with malicious activity.

---

## SOC Analyst Assessment

**Classification: Likely Benign / Requires Context**

Based on the available event information, there was insufficient evidence to classify the activity as malicious.

The process paths, parent-child relationship, command line, and user context were reviewed before reaching the assessment.

---

## Investigation Process

The investigation followed a basic process-analysis workflow:

1. Identify the newly created process.
2. Review the executable path.
3. Examine the command line.
4. Identify the parent process.
5. Review the user associated with the process.
6. Determine whether the observed process relationship appears expected or suspicious.
7. Classify the event based on available evidence.

---

## Conclusion

This investigation demonstrated how Sysmon Event ID 1 can provide valuable endpoint visibility into process execution.

Reviewing the process image, command line, parent process, and user context allows a SOC analyst to distinguish potentially suspicious activity from legitimate system behavior.
