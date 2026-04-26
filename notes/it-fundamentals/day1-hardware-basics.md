# Day 1: IT Fundamentals, Hardware Risks & Forensic Logs
**Date:** April 26, 2026
**Focus:** Hardware Security, Windows Event Logs, and Sabotage Frameworks

---

## 🛡️ 1. Hardware Security & Forensics
*Deep-dive into how physical components dictate system integrity.*

### The Hardware-Security Matrix
| Component | Primary Risk | SOC/Forensic Insight |
| :--- | :--- | :--- |
| **CPU** | **Side-Channel Attacks:** (e.g., Spectre) stealing keys via timing. | Enforces **Memory Isolation** to prevent cross-app spying. |
| **RAM** | **Volatile Data Loss:** Reboots wipe "Data in Use." | Contains "Live Evidence" like decrypted passwords and active malware. |
| **SSD** | **Forensic Nightmare:** The **TRIM** command wipes deleted data automatically. | **Secure Erase** uses voltage spikes for instant data destruction. |
| **Motherboard** | **Supply Chain Attacks:** Malicious chips added during builds. | Houses the **TPM** and **UEFI** for "Secure Boot" integrity. |
| **Hypervisor** | **VM Escape:** Virus "leaking" from a guest VM to the host. | Used by analysts to safely "detonate" malware in a sandbox. |

### File Systems: The Gatekeepers
* **NTFS:** The Windows standard. Supports **Permissions** (Read/Write/Execute) and **Journaling** for crash recovery.
* **FAT32:** The "Universal" threat. No permissions/security. Hackers use it to move malware easily across different OS platforms.

---

## 🔍 2. Investigation: Windows Event Viewer
**Target:** Event ID 4624 (Successful Logon)
**Analysis:**
I identified a **Logon Type 5 (Service Logon)**. While usually benign (system background tasks), I've documented the "Red Flags" for future threat hunts:

* **Normal:** `C:\Windows\System32\services.exe` triggering the logon.
* **Suspicious:** Any process path involving `\Temp\`, `\Users\Public\`, or `\Downloads\`.
* **Lateral Movement:** A Type 5 log showing a remote IP address instead of a local address suggests an attacker moving through the network.

---

## 📰 3. Threat Intelligence & Case Studies
*Analysis of today's top stories from The Hacker News.*

### A. The "Missing Link": Fast16 (Equation Group)
* **The Discovery:** A 2005 Windows malware framework using a **Lua 5.0 engine** for encrypted logic.
* **Method:** Deployed a kernel driver (`fast16.sys`) to perform **Kernel-level Sabotage**.
* **Impact:** Silently corrupted mathematical simulations in engineering software. **Lesson:** Digital attacks can cause physical structural failure.

### B. Vulnerability Tracking (CISA KEV)
* **Samsung MagicINFO (CVE-2024-7399):** A **Path Traversal** flaw allowing Mirai botnets to gain SYSTEM authority.
* **D-Link DIR-823X (CVE-2025-29635):** **Command Injection** on End-of-Life (EoL) routers.
* **Takeaway:** EoL hardware is a "sitting duck." If it can't be patched, it must be decommissioned.

---

## 🧠 4. New Technical Vocabulary
* **Persistence:** The ability of malware to stay on a system after reboots (often via backdoors).
* **Cryptojacking:** Using a victim's **GPU** power to mine cryptocurrency.
* **Hard Power Cycle:** Physically pulling the plug to clear deep-seated malware that a software restart can't touch.
* **Privilege Escalation:** Exploiting a bug to gain "Admin" or "Root" (Total Control) powers.
* **Botnet:** A network of "zombie" devices (IoT/Routers) controlled for large-scale attacks.

---

## ✅ Progress Summary
- [x] **Messer A+:** Completed 1.1 & 1.2 (CPU, RAM, Motherboard, Power).
- [x] **TryHackMe:** Completed 4 "Pre-Security" rooms.
- [x] **Anki:** 10 core hardware/security terms reviewed.
- [x] **Lab:** Successfully parsed Event ID 4624 fields.
