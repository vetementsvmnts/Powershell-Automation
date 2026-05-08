# Log Requirements & Environment Setup

To ensure the scripts in this folder function correctly, the following Windows Audit Policies must be enabled. Without these logs, the scripts will return null results.

## 1. Advanced Audit Policy Configuration
Navigate to: `Computer Configuration > Windows Settings > Security Settings > Advanced Audit Policy`

| Category | Subcategory | Setting | Purpose |
| :--- | :--- | :--- | :--- |
| **Logon/Logoff** | Audit Logon | Success & Failure | Detects Brute Force (Event ID 4624/4625) |
| **Detailed Tracking** | Audit Process Creation | Success | Powers `Get-Suspiciousprocess.ps1` |
| **Account Management** | Audit User Account Mgmt | Success & Failure | Detects unauthorized account changes |

## 2. PowerShell Script Block Logging
This is critical for detecting obfuscated scripts and fileless malware.

* **Path:** `Administrative Templates > Windows Components > Windows PowerShell`
* **Setting:** Turn on **PowerShell Script Block Logging** (Enabled)
* **Setting:** Turn on **PowerShell Transcription** (Optional, but recommended)

## 3. Command Line Process Auditing
To see the actual commands being run (e.g., `net user /add`), enable:
* **Path:** `Administrative Templates > System > Process Creation`
* **Setting:** Include command line in process creation events (Enabled)
