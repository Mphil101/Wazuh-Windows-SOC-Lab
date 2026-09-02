#  Custom Wazuh Visualization Dashboard

## Dashboard Overview

The Wazuh Dashboard was configured to provide a centralized view of Windows endpoint security telemetry collected from the monitored Windows virtual machine.

The dashboard contains four visualizations:

- Failed Logon Counts — Windows Event ID 4625
- Successful Logon Counts — Windows Event ID 4624
- Process Creation by Image — Sysmon Event ID 1
- File Creation Activity Over Time — Sysmon Event ID 11

---

## Dashboard

![Wazuh Dashboard](<../screenshots/VirtualBox wazuh dashboard.png>)

*Figure 1: Wazuh Dashboard displaying Windows authentication, process creation, and file creation activity.*

---

## SOC Value

The dashboard provides a centralized view of endpoint activity that can assist a SOC analyst during security monitoring and investigation.

The visualizations allow authentication, process, and file activity to be reviewed more efficiently and can help identify activity that may require additional investigation.

---

## Conclusion

The Wazuh Dashboard provided a centralized visualization layer for the endpoint telemetry collected during the lab.

The dashboard demonstrates how security telemetry can be transformed into visual information that supports SOC monitoring and investigation.
