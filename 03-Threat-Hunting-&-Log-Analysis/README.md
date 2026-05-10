#  ThreatHunter powershell automation 

> A PowerShell-based threat hunting and log analysis engine for Windows endpoints. Automatically scans event logs, registry, scheduled tasks, and Sysmon for indicators of compromise — and generates a full HTML report with a single run.

---

##  Overview

ThreatHunter.ps1 is a standalone Windows threat hunting script designed for security analysts, sysadmins, and incident responders. It runs six hunting modules in sequence, collects findings, exports per-module CSVs, and produces a dark-themed HTML report you can review or share with your team.

No dependencies beyond Windows PowerShell — no third-party modules required.

---

## ⚡ Quick Start

```powershell
# Run as Administrator
.\ThreatHunter.ps1
```

The report and CSVs are saved automatically to a `Reports\` folder in the same directory as the script. The HTML report opens in your browser when the hunt completes.

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

## 🚨 Risk Levels

| Level | Colour | Examples |
|---|---|---|
| `CRITICAL` | 🔴 Red | Audit log cleared, Defender disabled, Mimikatz invocation, user added to admin group |
| `HIGH` | 🟠 Orange | Download cradles, registry persistence, WMI subscriptions, encoded commands |
| `MEDIUM` | 🟡 Yellow | Execution policy bypass, RDP logons, SMB access, Kerberos anomalies |
| `LOW` | ⚪ Grey | Non-Microsoft scheduled tasks, general file creation |

---

## 📁 Output Structure

```
Reports/
├── ThreatHunt_Report_<timestamp>.html       # Full HTML report (auto-opens)
├── ThreatHunt_Log_<timestamp>.txt           # Console log with timestamps
└── ThreatHunt_Report_<timestamp>_CSVs/
    ├── PowerShell_Threats.csv
    ├── Security_Threats.csv
    ├── Sysmon_Threats.csv
    ├── Defender_Threats.csv
    ├── Persistence_Threats.csv
    └── LateralMovement_Threats.csv
```

---

## 🛡️ Prerequisites

- **Windows** 10 / Server 2016 or later
- **PowerShell** 5.1+ (built into Windows)
- **Administrator privileges** (required for reading Security and Sysmon logs)
- **Script Block Logging / Module Logging** enabled for richer PowerShell hunting (optional but recommended)
- **Sysmon** installed for the Sysmon module to produce results (optional)

---

## ⚙️ Enabling Recommended Logging

For best results, enable these Windows logging policies via Group Policy or the registry before running ThreatHunter:

```powershell
# Enable PowerShell Script Block Logging
$path = "HKLM:\SOFTWARE\Policies\Microsoft\Windows\PowerShell\ScriptBlockLogging"
New-Item $path -Force | Out-Null
Set-ItemProperty $path -Name "EnableScriptBlockLogging" -Value 1

# Enable Process Creation command-line auditing (Event ID 4688)
auditpol /set /subcategory:"Process Creation" /success:enable /failure:enable
```

---

## 🧩 Using as a Module

ThreatHunter.ps1 can be dot-sourced to call individual hunt functions:

```powershell
# Dot-source to load functions without running
. .\ThreatHunter.ps1

# Run individual modules
$psFindings        = Hunt-PowerShellLogs
$secFindings       = Hunt-SecurityEvents
$persistFindings   = Hunt-Persistence
```

---

## 📊 HTML Report Preview

The report includes:

- **Summary cards** — Critical / High / Total findings / Modules run
- **Per-module tables** — Sorted by risk level, with command snippets in monospace
- **Highlighted risk levels** — Colour-coded inline for fast triage
- **Footer** — CSV paths for follow-up analysis

---

## 🔧 Customisation

**Add your own hunt patterns** in `Hunt-PowerShellLogs`:
```powershell
@{Pattern="YourPattern"; Name="Your Detection Name"; Risk="HIGH"; Description="What this catches"}
```

**Change the lookback window** (default: 24 hours):
```powershell
$startTime = (Get-Date).AddHours(-48)   # extend to 48 hours
```

**Limit event volume** by adjusting `Select-Object -First N` in each module.

---

## ⚠️ Disclaimer

This tool is intended for **authorised security testing and incident response** on systems you own or have explicit permission to assess. Unauthorised use against systems you do not own may be illegal. The author assumes no liability for misuse.

---

## 📄 License

MIT — see [LICENSE](LICENSE) for details.
