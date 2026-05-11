
## Overview

`ThreatHunter.ps1` is a standalone Windows threat hunting script designed for security analysts, sysadmins, and incident responders. It runs six hunting modules in sequence, collects findings, exports per-module CSVs, and produces a dark-themed HTML report you can review or share with your team.

No dependencies beyond Windows PowerShell — no third-party modules required.

---

##  Quick Start

```powershell
# Run as Administrator
.\ThreatHunter.ps1
```

The report and CSVs are saved automatically to a `Reports\` folder in the same directory as the script. The HTML report opens in your browser when the hunt completes.

### ThreatHunter GUI

![ThreatHunter GUI](https://raw.githubusercontent.com/vetementsvmnts/Powershell-Automation/main/03-Threat-Hunting-%26-Log-Analysis/Assets/ThreatHunter-GUI.png)

---

## 🔍 Hunt Modules

| Module | What It Hunts | Key Signals |
|---|---|---|
| **PowerShell Logs** | Event IDs 4103, 4104 + history files | Encoded commands, download cradles, Mimikatz, obfuscation, LOLBAS |
| **Security Events** | Windows Security log (last 24h) | Brute force, privilege escalation, account creation, audit log clearing, Kerberoasting |
| **Sysmon** | Sysmon Operational log (if installed) | Process injection, LSASS access, DNS queries, ADS file creation, DLL loads |
| **Windows Defender** | Defender Operational log + live status | Malware detections, real-time protection disabled |
| **Persistence** | Registry, Scheduled Tasks, WMI | Run keys, script-based tasks, WMI event subscriptions |
| **Lateral Movement** | SMB, RDP, remote service installs | SMB share access, RDP logons, PSExec/RemCom service creation |

---

## Risk Levels

| Level | Colour | Examples |
|---|---|---|
| **CRITICAL** | 🔴 Red | Audit log cleared, Defender disabled, Mimikatz invocation, user added to admin group |
| **HIGH** | 🟠 Orange | Download cradles, registry persistence, WMI subscriptions, encoded commands |
| **MEDIUM** | 🟡 Yellow | Execution policy bypass, RDP logons, SMB access, Kerberos anomalies |
| **LOW** | ⚪ Grey | Non-Microsoft scheduled tasks, general file creation |

---

## 📊 HTML Report Preview

The report includes:

- **Summary cards** — Critical / High / Total findings / Modules run
- **Per-module tables** — Sorted by risk level, with command snippets in monospace
- **Highlighted risk levels** — Colour-coded inline for fast triage
- **Footer** — CSV paths for follow-up analysis

### Security Threat Dashboard

![Security Threat Dashboard](https://raw.githubusercontent.com/vetementsvmnts/Powershell-Automation/main/03-Threat-Hunting-%26-Log-Analysis/Assets/Security-Threat-Dashboard.png)

### Sysmon & Defender Alerts

![Sysmon & Defender Alerts](https://raw.githubusercontent.com/vetementsvmnts/Powershell-Automation/main/03-Threat-Hunting-%26-Log-Analysis/Assets/Sysmon-%26Defender-Alert.png)

### Persistence Mechanisms

![Persistence Mechanisms](https://raw.githubusercontent.com/vetementsvmnts/Powershell-Automation/main/03-Threat-Hunting-%26-Log-Analysis/Assets/Persistence-Mechanisms.png)

### Web Browser Dashboard

![Web Browser Dashboard](https://raw.githubusercontent.com/vetementsvmnts/Powershell-Automation/main/03-Threat-Hunting-%26-Log-Analysis/Assets/Web%20Browser%20Dashboard.png)

---

## 📁 Output Structure
Reports/
├── ThreatHunt_Report_<timestamp>.html
├── ThreatHunt_Log_<timestamp>.txt
└── ThreatHunt_Report_<timestamp>_CSVs/
├── PowerShell_Threats.csv
├── Security_Threats.csv
├── Sysmon_Threats.csv
├── Defender_Threats.csv
├── Persistence_Threats.csv
└── LateralMovement_Threats.csv

---

## 🛡️ Prerequisites

- Windows 10 / Server 2016 or later
- PowerShell 5.1+ (built into Windows)
- Administrator privileges
- Script Block Logging / Module Logging enabled *(optional but recommended)*
- Sysmon installed *(optional)*

---

## ⚙️ Enabling Recommended Logging

```powershell
# Enable PowerShell Script Block Logging
$path = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging"
New-Item $path -Force | Out-Null
Set-ItemProperty $path -Name "EnableScriptBlockLogging" -Value 1

# Enable Process Creation auditing (Event ID 4688)
auditpol /set /subcategory:"Process Creation" /success:enable /failure:enable
```

---

## 🧩 Using as a Module

```powershell
. .\ThreatHunter.ps1

$psFindings       = Hunt-PowerShellLogs
$secFindings      = Hunt-SecurityEvents
$persistFindings  = Hunt-Persistence
```

---

## 🔧 Customisation

Add patterns in `Hunt-PowerShellLogs`:

```powershell
@{Pattern="YourPattern"; Name="Your Detection Name"; Risk="HIGH"; Description="What this catches"}
```

Change the lookback window (default 24h):

```powershell
$startTime = (Get-Date).AddHours(-48)
```

---

## ⚠️ Disclaimer

For authorised security testing and incident response only. Unauthorised use may be illegal.

---

## 📄 License

MIT — see [LICENSE](LICENSE) for details.
Each image is placed exactly as discussed — the GUI right after Quick Start, then the dashboard screenshots grouped under the HTML Report Preview section. The image URLs use the raw.githubusercontent.com format which GitHub renders correctly in READMEs.
One thing to double-check: the Sysmon-&Defender-Alert.png filename contains an ampersand — I've encoded it as %26 in the URL. If GitHub stored it differently (e.g. with a literal &), the image might not load. You can verify by clicking on that file in your Assets folder and copying the raw URL from the browser.
