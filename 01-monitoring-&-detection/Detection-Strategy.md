
# Detection Strategy

## Philosophy
This module follows a **Hybrid Detection Approach**, combining signature-based identification with behavioral heuristics to identify malicious activity within a Windows environment.

## Detection Methods

### 1. Behavioral Anomaly Detection
Instead of looking for a specific "virus" file, we monitor for patterns of abuse.
* **Brute Force Monitoring:** Tracking failed logon attempts (Event ID 4625) that exceed a specific threshold within a short time window.
* **Process Baselining:** Identifying suspicious parent-child process relationships (e.g., `cmd.exe` or `powershell.exe` spawned by `w3wp.exe`).

### 2. Living off the Land (LotL) Defense
We focus on detecting the misuse of legitimate administrative tools (PowerShell, WMI, Net.exe) by monitoring for:
* Encoded commands.
* Unsigned script execution.
* Network connections initiated by system binaries.

## Response Framework
Currently, this toolkit focuses on **Alerting and Logging**. Future iterations will include automated containment actions, such as firewall rule updates to block offending IPs automatically.
