# LetsDefend-EventID-316-Lumma-Stealer
Let's Defend Incident Report for SOC338 - Lumma Stealer - DLL Side-Loading via Click Fix Phishing

## 🛡️ Incident Report: Lumma Stealer - DLL Side-Loading via ClickFix Phishing
### 📄 Executive Summary
On March 13, 2025, at 09:44 AM, a critical security alert was triggered involving a "ClickFix" phishing attack. The attack targeted a user named **Dylan** with a social engineering lure promising a free Windows 11 Pro upgrade. The investigation confirmed the user interacted with a malicious URL, leading to a Lumma Stealer infection delivered via DLL side-loading
### 🔍 Incident Details
- Event ID: 316
- Rule Name: SOC338 - Lumma Stealer - DLL Side-Loading via Click Fix Phishing.
- Severity: Critical
- Target Host: Dylan
- Host IP: 172.16.20.151
- Final Action: Allowed

## 🧪 Technical Analysis
**1. Inital Access 📧**
- **Sender Address:** update@windows-update.site
- **SMTP IP:** 132.232.40.201
- **Subject:** "Upgrade your system to Windows 11 Pro for Free."
- **Phishing URL:** https://www.windows-update[.]site/


<img width="618" height="166" alt="image" src="https://github.com/user-attachments/assets/be8f1396-6669-4420-809b-2b922cf3d305" />


**2. Execution & Malware Behavior ⚙️**
  
  The user visited the malicious site, which used "ClickFix" social engineering to trick the user into executing a script.
  - **Payload Delivery:** A file disguised as a video, **maloy.mp4**, was accessed.
  - **Process Execution:** The system utilized mshta.exe with **PID 7384** to execute malicious code.
  - **Living-off-the-Land:** Terminal history shows PowerShell.exe being used to initiate commands.
  - **Malware Family:** Identified as a variant of AsyncRAT and Lumma Stealer.
--

## Command and Control (C2) 🌐

The infected host established outbound connections to the attacker's infrastructure.
- **C2 Domain:** overcoatpassably[.]shop
- **C2 IP:** 172.67.139.19
- **C2 Port:** 443 (HTTPS)

<img width="619" height="184" alt="image" src="https://github.com/user-attachments/assets/e77eb887-bf40-4fa0-a0d5-920a4aae690c" />

## 🗺️ MITRE ATT&CK Mapping
| **Tactic**         | **Technique**                     | **ID**    |
| ------------------ | --------------------------------- | --------- |
| **Initial Access** | Phishing: Spearphishing Link      | T1566.002 |
| **Execution**      | Command and Scripting Interpreter | T1059     |
| **Execution**      | User Execution: Malicious Link    | T1204.001 |
| **Discovery**      | Account Discovery                 | T1087     |
| **Discovery**      | System Service Discovery          | T1007     |

## 🚩 Indicators of Compromise (IOCs)
| **Type**         | **Value**                                                  |
| ---------------- | ---------------------------------------------------------- |
| **Phishing URL** | `https://www.windows-update[.]site/`                       |
| **SMTP IP**      | `132.232.40[.]201`                                         |
| **C2 URL**       | `https://overcoatpassably[.]shop/Z8UZbPyVpGfdRS/maloy.mp4` |
| **C2 IPv4**      | `172.67.139.19`                                            |

## 🛠️ Containment & Remediation Actions
1. **Host Isolation:** The host machine **Dylan (172.16.20.151)** was isolated from the network.
2. **Email Purge:** The malicious email was deleted from the user's mailbox.
3. **Credential Reset:** Recommended a full reset of user credentials for the affected account.
4. **Security Awareness:** Targeted phishing training recommended to help the user identify future social engineering attempts.
---
This report was generated as a part of a Digital Forensics and Incident Response (DFIR) exercise. 
