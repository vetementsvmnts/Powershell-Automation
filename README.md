<div align="center">

```
██████╗  ██████╗ ██╗    ██╗███████╗██████╗ ███████╗██╗  ██╗███████╗██╗     ██╗
██╔══██╗██╔═══██╗██║    ██║██╔════╝██╔══██╗██╔════╝██║  ██║██╔════╝██║     ██║
██████╔╝██║   ██║██║ █╗ ██║█████╗  ██████╔╝███████╗███████║█████╗  ██║     ██║
██╔═══╝ ██║   ██║██║███╗██║██╔══╝  ██╔══██╗╚════██║██╔══██║██╔══╝  ██║     ██║
██║     ╚██████╔╝╚███╔███╔╝███████╗██║  ██║███████║██║  ██║███████╗███████╗███████╗
╚═╝      ╚═════╝  ╚══╝╚══╝ ╚══════╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝
```

### ⚡ Cybersecurity Automation — From Hardening to Hunting

[![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B%20%7C%207.x-0078D4?style=for-the-badge&logo=powershell&logoColor=white)](https://docs.microsoft.com/en-us/powershell/)
[![Platform](https://img.shields.io/badge/Platform-Windows%2010%2F11%20%7C%20Server-0078D4?style=for-the-badge&logo=windows&logoColor=white)](https://www.microsoft.com/en-us/windows)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](./LICENSE)
[![Maintenance](https://img.shields.io/badge/Maintained-Yes-brightgreen?style=for-the-badge)](https://github.com/YourUsername/Powershell-Automation/commits)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-blueviolet?style=for-the-badge)](./CONTRIBUTING.md)

[![Blue Team](https://img.shields.io/badge/Blue%20Team-Detection%20%26%20Hardening-1565C0?style=flat-square)](.)
[![Red Team](https://img.shields.io/badge/Red%20Team-Authorized%20Testing%20Only-C62828?style=flat-square)](.)
[![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK%20Mapped-FF6F00?style=flat-square)](https://attack.mitre.org/)
[![CIS Benchmarks](https://img.shields.io/badge/CIS-Benchmark%20Aligned-2E7D32?style=flat-square)](https://www.cisecurity.org/)

</div>

---

<div align="center">

> **PowerShell automation toolkit for cybersecurity operations, built for technical and non-technical users.**
> Automates security hardening, incident response, log analysis, and compliance checks.
> Includes beginner-friendly documentation and advanced scripting modules for blue-team and red-team tasks.
> **Strengthen your security posture with confidence.**

</div>

---

## 📋 Table of Contents

- [✨ Overview](#-overview)
- [🚀 Features at a Glance](#-features-at-a-glance)
- [⚙️ Prerequisites](#️-prerequisites)
- [📦 Installation](#-installation)
- [🗂️ Module Structure](#️-module-structure)
- [🟢 Beginner Quick Start](#-beginner-quick-start)
- [🔧 Advanced Usage](#-advanced-usage)
- [🔵 Blue Team Modules](#-blue-team-modules)
- [🔴 Red Team Modules](#-red-team-modules)
- [🛡️ Compliance & Hardening](#️-compliance--hardening)
- [🚨 Incident Response](#-incident-response)
- [📊 Log Analysis](#-log-analysis)
- [🤝 Contributing](#-contributing)
- [⚠️ Disclaimer](#️-disclaimer)
- [📄 License](#-license)

---

## ✨ Overview

**Powershell-Automation** is a modular, extensible cybersecurity automation framework built entirely in PowerShell. Whether you're a seasoned penetration tester, a blue-team analyst, or an IT administrator stepping into security for the first time — this toolkit gives you the scripts, documentation, and workflows to operate with speed and precision.

Every module is built with two audiences in mind:

| 👤 Non-Technical Users | 🧑‍💻 Security Professionals |
|---|---|
| Plain-English step-by-step guides | Full parameter control & pipeline support |
| Safe read-only modes by default | SIEM integration & API hooks |
| Auto-generated HTML reports | Custom rule sets & advanced filters |
| No prior PowerShell knowledge needed | Extendable modular architecture |

---

## 🚀 Features at a Glance

| Module | Capability | Standards |
|---|---|---|
| 🔒 **Security Hardening** | CIS Benchmark & STIG automated audits | CIS L1/L2, STIG |
| 🚨 **Incident Response** | Containment, eradication & recovery workflows | NIST SP 800-61 |
| 📊 **Log Analysis** | Windows Event Logs, Sysmon, PowerShell transcript parsing | MITRE ATT&CK |
| ✅ **Compliance Checks** | Baseline audits with exportable reports | NIST, PCI-DSS, ISO 27001 |
| 🔴 **Red Team** | Enumeration, lateral movement simulation, password auditing | MITRE ATT&CK TTPs |
| 🔵 **Blue Team** | Threat hunting, anomaly detection, IOC searching | MITRE D3FEND |
| 📝 **Reporting** | Auto-generate HTML/CSV/JSON security audit reports | — |
| 🧩 **Modular Design** | Import only the modules you need | — |

---

## ⚙️ Prerequisites

Ensure the following before getting started:

```
✔ PowerShell 5.1+  OR  PowerShell Core 7.x  (recommended)
✔ Windows 10 / 11  OR  Windows Server 2016 / 2019 / 2022
✔ Administrator / Elevated Privileges  (required for most modules)
```

**Optional dependencies:**
- [Pester](https://pester.dev/) — for running module unit tests
- [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer) — for script linting

Check your PowerShell version:
```powershell
$PSVersionTable.PSVersion
```

---

## 📦 Installation

### Option 1 — Clone via Git *(Recommended)*
```powershell
git clone https://github.com/YourUsername/Powershell-Automation.git
cd Powershell-Automation
```

### Option 2 — Download ZIP
1. Click **`Code`** → **`Download ZIP`** on this page
2. Extract to a folder of your choice
3. Open PowerShell as Administrator and navigate to the folder

### Set Execution Policy
> ⚠️ Only apply this in a **trusted, controlled environment.**
```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

### Import the Toolkit
```powershell
Import-Module .\CyberSecToolkit.psm1

# Verify loaded modules
Get-Module CyberSecToolkit
```

---

## 🗂️ Module Structure

```
Powershell-Automation/
│
├── 📁 BlueTeam/                   # Detection, hunting & monitoring
│   ├── Invoke-ThreatHunt.ps1
│   ├── Get-SuspiciousProcesses.ps1
│   ├── Watch-NetworkConnections.ps1
│   └── Get-FailedLogons.ps1
│
├── 📁 RedTeam/                    # Authorized offensive testing
│   ├── Invoke-Enumeration.ps1
│   ├── Test-LateralMovement.ps1
│   ├── Get-LocalPrivileges.ps1
│   └── Invoke-PasswordAudit.ps1
│
├── 📁 Hardening/                  # System & policy hardening
│   ├── Invoke-CISBenchmark.ps1
│   ├── Set-SecureBaseline.ps1
│   ├── Disable-LegacyProtocols.ps1
│   └── Enable-AuditPolicies.ps1
│
├── 📁 IncidentResponse/           # IR workflows & forensics
│   ├── Start-IRWorkflow.ps1
│   ├── Invoke-Containment.ps1
│   ├── Collect-ForensicData.ps1
│   └── Export-IRReport.ps1
│
├── 📁 LogAnalysis/                # Log parsing & IOC detection
│   ├── Parse-EventLogs.ps1
│   ├── Analyze-SysmonLogs.ps1
│   ├── Get-PowerShellHistory.ps1
│   └── Find-IOCs.ps1
│
├── 📁 Compliance/                 # Regulatory baseline checks
│   ├── Test-NISTBaseline.ps1
│   ├── Test-PCIDSSControls.ps1
│   └── Export-ComplianceReport.ps1
│
├── 📁 Docs/                       # Guides & references
│   ├── BeginnerGuide.md
│   ├── AdvancedScripting.md
│   └── ModuleReference.md
│
├── 📁 Reports/                    # Auto-generated output reports
├── CyberSecToolkit.psm1           # Main module manifest
└── README.md
```

---

## 🟢 Beginner Quick Start

> No PowerShell experience? Follow these 5 steps and you'll be running your first security check in under 2 minutes.

**Step 1** — Open PowerShell as Administrator
```
Start Menu → Search "PowerShell" → Right-click → Run as Administrator
```

**Step 2** — Navigate to the toolkit folder
```powershell
cd C:\Path\To\Powershell-Automation
```

**Step 3** — Import the toolkit
```powershell
Import-Module .\CyberSecToolkit.psm1
```

**Step 4** — Run your first check *(safe, read-only)*
```powershell
# Check for failed login attempts in the last 24 hours
.\BlueTeam\Get-FailedLogons.ps1 -Hours 24
```

**Step 5** — View your report

Results display in the terminal **and** are saved to `.\Reports\` as an HTML file you can open in any browser.

> 💡 **Every script has built-in help.** Just add `-Help` to any command:
> ```powershell
> .\BlueTeam\Get-FailedLogons.ps1 -Help
> ```

---

## 🔧 Advanced Usage

All modules support pipeline input, custom parameters, verbose logging, and SIEM/API integration.

```powershell
# Full CIS Level 1 Benchmark audit — exported as HTML
.\Hardening\Invoke-CISBenchmark.ps1 -Level 1 -ExportHTML -OutputPath "C:\Reports\CIS_Audit.html"

# Threat hunt mapped to MITRE ATT&CK T1059 (Command & Scripting Interpreter)
.\BlueTeam\Invoke-ThreatHunt.ps1 -IOC "mimikatz" -Scope EventLog,ProcessList,Network -MITREMap

# Full ransomware IR workflow with forensic collection
.\IncidentResponse\Start-IRWorkflow.ps1 -IncidentType Ransomware -AffectedHost WORKSTATION-01 -CollectForensics

# Pipeline: get suspicious processes and pipe results to IOC finder
.\BlueTeam\Get-SuspiciousProcesses.ps1 | .\LogAnalysis\Find-IOCs.ps1 -SearchScope All
```

---

## 🔵 Blue Team Modules

### `Get-FailedLogons.ps1`
Queries Windows Security Event Log **(Event ID 4625)** for failed authentication attempts. Useful for detecting brute-force and password spray attacks.
```powershell
.\BlueTeam\Get-FailedLogons.ps1 -Hours 48 -ExportCSV -Threshold 5
```

### `Get-SuspiciousProcesses.ps1`
Identifies processes with anomalous parent-child relationships, unsigned binaries, or names matching known malicious patterns.
```powershell
.\BlueTeam\Get-SuspiciousProcesses.ps1 -CheckSignatures -CompareBaseline
```

### `Watch-NetworkConnections.ps1`
Monitors live network connections and flags traffic to known malicious IPs using a local or remote threat intel feed.
```powershell
.\BlueTeam\Watch-NetworkConnections.ps1 -ThreatFeed .\Data\malicious_ips.txt -Interval 30
```

### `Invoke-ThreatHunt.ps1`
Structured threat hunting across event logs, processes, registry keys, and network artifacts — mapped to MITRE ATT&CK playbooks.
```powershell
.\BlueTeam\Invoke-ThreatHunt.ps1 -Playbook MITRE_T1059 -Verbose
```

---

## 🔴 Red Team Modules

> 🚨 **AUTHORIZED USE ONLY.**
> These modules must only be run on systems you **own** or have **explicit written permission** to test.
> Unauthorized use is illegal. See [Disclaimer](#️-disclaimer).

### `Invoke-Enumeration.ps1`
Local and domain enumeration — users, groups, shares, services, and scheduled tasks.
```powershell
.\RedTeam\Invoke-Enumeration.ps1 -Target localhost -Scope Full
```

### `Test-LateralMovement.ps1`
Simulates lateral movement paths via WMI, PsExec, and WinRM to identify over-permissioned accounts and exposed attack paths.
```powershell
.\RedTeam\Test-LateralMovement.ps1 -TargetHost 192.168.1.50 -Method WinRM
```

### `Get-LocalPrivileges.ps1`
Identifies local privilege escalation vectors including weak service permissions, unquoted paths, and token abuse opportunities.
```powershell
.\RedTeam\Get-LocalPrivileges.ps1 -CheckAll
```

### `Invoke-PasswordAudit.ps1`
Tests password policies and checks active accounts against configurable wordlists to identify weak credentials.
```powershell
.\RedTeam\Invoke-PasswordAudit.ps1 -WordList .\Data\common_passwords.txt -Domain CORP
```

---

## 🛡️ Compliance & Hardening

### Run a CIS Benchmark Audit
```powershell
# Level 1 — Basic (most environments)
.\Hardening\Invoke-CISBenchmark.ps1 -Level 1

# Level 2 — Strict (high-security environments)
.\Hardening\Invoke-CISBenchmark.ps1 -Level 2 -ExportHTML
```

### Apply Secure Baseline
```powershell
# Always preview with -WhatIf first
.\Hardening\Set-SecureBaseline.ps1 -WhatIf

# Apply after review
.\Hardening\Set-SecureBaseline.ps1 -Confirm
```

### Disable Legacy Protocols
```powershell
# Disables SMBv1, TLS 1.0/1.1, RC4, and weak cipher suites
.\Hardening\Disable-LegacyProtocols.ps1 -All
```

### Enable Recommended Audit Policies
```powershell
.\Hardening\Enable-AuditPolicies.ps1 -Preset Recommended
```

---

## 🚨 Incident Response

### Launch a Full IR Workflow
```powershell
.\IncidentResponse\Start-IRWorkflow.ps1 -IncidentType Malware -AffectedHost WORKSTATION-01
```

The workflow automatically executes:

```
[1] Notify analyst via console prompt
[2] Isolate affected host          ← requires confirmation
[3] Collect volatile data          (processes, connections, memory artifacts)
[4] Pull Windows Event Logs        (Security, System, Application)
[5] Package all evidence           → timestamped ZIP
[6] Generate IR report             → HTML + JSON
```

### Collect Forensic Data Only
```powershell
.\IncidentResponse\Collect-ForensicData.ps1 -Host WORKSTATION-01 -OutputPath C:\IR\Evidence\
```

### Isolate a Host (Containment)
```powershell
.\IncidentResponse\Invoke-Containment.ps1 -Host WORKSTATION-01 -Method NetworkIsolation
```

---

## 📊 Log Analysis

### Parse Windows Event Logs
```powershell
# Logon events + failures over 7 days
.\LogAnalysis\Parse-EventLogs.ps1 -EventID 4624,4625,4648 -Days 7 -ExportCSV
```

### Analyze Sysmon Logs
```powershell
# Filter for suspicious network connections and process creations
.\LogAnalysis\Analyze-SysmonLogs.ps1 -Filter NetworkConnect,ProcessCreate -Suspicious
```

### Retrieve PowerShell Command History
```powershell
# Pull all users' PSReadLine history and transcript logs
.\LogAnalysis\Get-PowerShellHistory.ps1 -AllUsers -IncludeTranscripts
```

### Find Indicators of Compromise
```powershell
# Search across all log sources for known IOCs
.\LogAnalysis\Find-IOCs.ps1 -IOCFile .\Data\iocs.csv -SearchScope All -ExportReport
```

---

## 🤝 Contributing

Contributions are welcome — new detection scripts, improved documentation, bug fixes, and hardening rules all strengthen the community toolkit.

```
1. Fork the repository
2. git checkout -b feature/your-module-name
3. git commit -m "Add: description of what you added"
4. git push origin feature/your-module-name
5. Open a Pull Request
```

**Script standards for contributions:**
- All scripts must include comment-based help (`Get-Help` compatible)
- Follow PowerShell [Approved Verbs](https://docs.microsoft.com/en-us/powershell/scripting/developer/cmdlet/approved-verbs-for-windows-powershell-commands)
- Include at least one usage example per script
- Red team scripts must include an authorization warning at runtime

---

## ⚠️ Disclaimer

> **This toolkit is intended strictly for authorized security testing, research, and educational purposes.**
>
> Unauthorized use of any offensive modules against systems you do not own or have **explicit written authorization** to test is **illegal** under the Computer Fraud and Abuse Act (CFAA), the Computer Misuse Act (CMA), and equivalent legislation worldwide.
>
> The authors and contributors of this toolkit accept **no liability** for any misuse, damage, or legal consequences arising from unauthorized use. Always operate within legal and ethical boundaries.

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](./LICENSE) file for full details.

---

<div align="center">

---

**Built for defenders. Sharpened by attackers. Trusted by both.**

---

[![GitHub Stars](https://img.shields.io/github/stars/YourUsername/Powershell-Automation?style=social)](https://github.com/YourUsername/Powershell-Automation/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/YourUsername/Powershell-Automation?style=social)](https://github.com/YourUsername/Powershell-Automation/network/members)
[![GitHub Issues](https://img.shields.io/github/issues/YourUsername/Powershell-Automation?style=social)](https://github.com/YourUsername/Powershell-Automation/issues)

⭐ **Star this repo** if it helped you &nbsp;|&nbsp; 🐛 [Report a Bug](../../issues/new) &nbsp;|&nbsp; 💡 [Request a Feature](../../issues/new) &nbsp;|&nbsp; 💬 [Discussions](../../discussions)

</div>
