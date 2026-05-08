# 🖼️ Technical Assets & Documentation

This directory contains the visual telemetry and architectural breakdown for the **Endpoint Monitoring Suite**.

## 📊 Live Detection Dashboard
![Security Monitor](Security-Monitor.png)

---

## ⚙️ Engineering Breakdown

### 1. The Engine (PowerShell)
The backend engine performs high-privilege system audits to extract deep process telemetry:
* **Metadata Validation:** Extracts `MainModule` version info and vendor strings.
* **Heuristic Analysis:** Automatically flags binaries executing from non-standard paths (e.g., `%TEMP%`, `Downloads`, `%APPDATA%`).
* **Telemetry Generation:** Compiles findings into a structured `JSON` bridge and a legacy `Security_Audit_Report.txt`.

### 2. The Dashboard (Python)
A custom-built triage interface designed for rapid security analysis:
* **Real-time Triage:** Consumes the JSON telemetry to provide a color-coded feed.
* **Status Monitoring:** Instant counter for `RED` (Concerning) vs `GREEN` (Safe) processes.
* **Architecture:** Decoupled design allowing the scanner to run as a background service while the GUI remains lightweight.

## 🧰 Technical Stack
| Component | Technology |
| :--- | :--- |
| **Automation** | PowerShell (WMI & .NET System.Diagnostics) |
| **GUI Framework** | Python 3.x (Tkinter) |
| **Data Bridge** | JSON |
| **Design Style** | Stealth Wealth / Technical Dark Mode |

---
*Developed by Sterling Consulting | Security Initiative 2026*
