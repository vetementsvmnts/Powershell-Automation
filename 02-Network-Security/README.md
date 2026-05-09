#   Network Security Powershell Automation
A proactive network defence framework that combines PowerShell-based network auditing with a Python-driven threat visualization layer — built for security analysts who need actionable intelligence fast.

## 📊 Security Dashboard
![NetSentinel Dashboard](Assets/NetSentinel-Dashboard.png)

---

## 🔍 Overview

NetSentinel is a cross-platform network security automation suite designed to surface vulnerabilities, suspicious connections, and policy violations across your environment. It bridges low-level network interrogation (PowerShell) with a clean analyst-facing dashboard (Python), turning raw telemetry into prioritised, colour-coded threat intelligence.

---

## 🛠️ How it Works

### 1. The Engine (PowerShell)
- Enumerates all **active network connections** and maps them to owning processes via PID resolution.
- Audits **open ports** against a configurable allowlist — flagging any unexpected listeners.
- Interrogates **firewall rules** for misconfigurations, disabled policies, or shadow rules that bypass corporate baselines.
- Performs **DNS anomaly detection** by cross-referencing resolved hostnames against known threat intelligence feeds.
- Applies **heuristic scoring** to flag high-risk indicators: unusual outbound ports, connections to non-standard geolocations, or processes binding to `0.0.0.0` without authorisation.
- Exports a structured `telemetry.json` feed and a timestamped `Network_Audit_Report.txt` for compliance and incident logging.

### 2. The Dashboard (Python)
- A custom **Tkinter GUI** that ingests the JSON telemetry feed in real time.
- Displays **live connection stats**: active sessions, flagged anomalies, blocked ports, and clean processes.
- Features a colour-coded triage system:
  - 🔴 `RED` — High-risk: unknown processes, suspicious remote IPs, or policy violations
  - 🟡 `AMBER` — Warn: elevated risk requiring analyst review
  - 🟢 `GREEN` — Verified: known-good system processes and authorised connections
- Includes an **export panel** for one-click incident report generation.

---

## 🧰 Technical Stack

| Component | Technology |
|-----------|-----------|
| Network Auditing | PowerShell (NetTCPIP, NetSecurity, WMI) |
| Threat Visualization | Python 3.x (Tkinter, Threading) |
| Telemetry Format | JSON (structured bridge layer) |
| Compliance Output | `.txt` timestamped audit logs |
| UI Design | Dark-mode, high-contrast analyst interface |

---


## ⚠️ Disclaimer

This tool is intended for **authorised security auditing and defensive monitoring only**. Always obtain explicit written permission before running on any network infrastructure you do not own or administer. Misuse may violate computer fraud and network access laws.

---

## 📜 License

MIT License — see [`LICENSE`](LICENSE) for details.
