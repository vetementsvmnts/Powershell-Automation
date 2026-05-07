
### 🔵 01 — Monitoring & Detection

[![PowerShell](https://img.shields.io/badge/PowerShell-5.1%2B%20%7C%207.x-0078D4?style=for-the-badge&logo=powershell&logoColor=white)](https://docs.microsoft.com/en-us/powershell/)
[![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK%20Mapped-FF6F00?style=flat-square)](https://attack.mitre.org/)
[![Blue Team](https://img.shields.io/badge/Blue%20Team-Detection%20%26%20Hunting-1565C0?style=flat-square)](.)

---

> **Continuous monitoring, threat detection, and security telemetry collection.**
> This module provides PowerShell-based detection engineering scripts for Windows environments, 
> focusing on real-time alerting, log-based hunting, and anomaly detection aligned with MITRE ATT&CK.

---

## 📋 Contents

- [✨ Overview](#-overview)
- [🚀 Capabilities](#-capabilities)
- [⚙️ Prerequisites](#️-prerequisites)
- [🗂️ Script Inventory](#️-script-inventory)
- [🟢 Quick Start](#-quick-start)
- [🔧 Advanced Usage](#-advanced-usage)
- [📊 Detection Coverage](#-detection-coverage)
- [🤝 Contributing](#-contributing)
- [⚠️ Disclaimer](#️-disclaimer)

---

## ✨ Overview

The **Monitoring & Detection** module is the defensive backbone of the Powershell-Automation toolkit. It contains scripts designed to:

- **Detect** malicious activity across Windows endpoints and servers
- **Hunt** for threats using event logs, process telemetry, and network artifacts
- **Monitor** critical security events in real-time with configurable alerting thresholds
- **Report** findings in human-readable formats (console, HTML, CSV, JSON)

Every script is built for two audiences:

| 👤 SOC Analysts & IT Admins | 🧑‍💻 Detection Engineers & Threat Hunters |
|---|---|
| Pre-configured detection rules with safe defaults | Customizable IOCs, YARA-like logic, and MITRE mapping |
| Auto-generated alert summaries | SIEM-ready JSON/CSV output for ingestion |
| One-liner execution with `-Help` available | Pipeline support and modular parameter sets |

---

## 🚀 Capabilities

| Script Category | Detection Focus | Data Sources |
|---|---|---|
| **Authentication Monitoring** | Brute-force, password sprays, impossible travel | Windows Security Log (4624/4625/4648) |
| **Process Anomaly Detection** | Masquerading, parent-child abuse, unsigned binaries | Sysmon (Event ID 1), WMI, Get-Process |
| **Network Surveillance** | C2 beacons, data exfiltration, lateral movement | Sysmon (Event ID 3), Netstat, DNS logs |
| **Threat Hunting** | MITRE ATT&CK TTP-based hunts across multiple vectors | Event Logs, Registry, File System, Memory |
| **Log Collection & Parsing** | Centralized parsing and IOC matching | Windows Event Logs, PowerShell Transcripts |

---

## ⚙️ Prerequisites
