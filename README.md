# Malware Reverse Engineering Portfolio

**Author:** Mazin Saleh  
**Role:** Cybersecurity Researcher & Software Engineer  
**Tools:** Ghidra, x64dbg, Wireshark, PEStudio, YARA, Process Monitor, INetSim

---

## 📂 Overview

This repository contains detailed technical analysis reports of various malware samples, ranging from commodity infostealers to sophisticated ransomware families. 

Each report documents the full reverse engineering lifecycle:
1.  **Static Analysis:** Examining PE headers, imports, and entropy to identify packing.
2.  **Dynamic Analysis:** Behavior monitoring, API call tracing, and persistence mechanisms.
3.  **Network Forensics:** C2 communication simulation and traffic analysis.
4.  **Defensive Countermeasures:** Extraction of IOCs and creation of custom YARA rules.

---

## 🦠 Analysis Reports

### 1. RootTeam Stealer Analysis
**Type:** Infostealer / Spyware  
**Focus:** Memory Forensics & C2 Simulation  

A reverse engineering analysis of a 64-bit packed infostealer. The investigation uncovered "smash-and-grab" tactics targeting Chrome credentials and crypto-wallets.
* **Key Findings:** Identified dynamic import rebuilding and traced credential theft routines in memory.
* **Network:** Simulated C2 communications using INetSim to capture DNS fallbacks.
* **Detection:** Authored YARA rules based on unique PDB strings.

[📄 **Read Full Report**](https://docs.google.com/document/d/1pXgbM-5dEu9U8-_6j1EUnw0gq-raHaG0SK1Sk7KjKNU/edit?usp=sharing)

---

### 2. Wotsuper Dropper Analysis
**Type:** Trojan Dropper  
**Focus:** Infection Chain & Traffic Analysis  

Analysis of a multi-stage dropper classified as `Trojan:Win32/Gozi`. This report details how the malware obfuscates its infection chain to deploy secondary payloads.
* **Key Findings:** Observed the dropping of `wotsuper.exe` into protected directories and registry manipulation for persistence.
* **Network:** Captured HTTP POST exfiltration to malicious domains and tracking pixels used for victim profiling.

[📄 **Read Full Report**](https://docs.google.com/document/d/1-vKgYswDTzosxuW4oVFl6kQvW3djnVRHE17buI_WnbY/edit?usp=sharing)

---

### 3. Remote Access Trojan (RAT) Analysis
**Type:** RAT / Backdoor  
**Focus:** Obfuscation & "Living off the Land"  

Full-scope analysis of a RAT designed for persistent remote command execution. The malware utilized XOR-based encryption to hide configuration data.
* **Key Findings:** Uncovered the abuse of `rundll32.exe` for stealthy DLL execution to bypass static signatures.
* **Network:** Intercepted persistent TCP beacons to a hard-coded adversary IP on port 443.
* **Artifacts:** Identified hidden configuration files created in `System32` via API monitoring.

[📄 **Read Full Report**](https://docs.google.com/document/d/11GVjU-GA_ZeqKj0SYsaZ7MPPXTun8SiDgfxxYN3pc0w/edit?usp=sharing)

---

### 4. DarkSide Ransomware Analysis
**Type:** Ransomware  
**Focus:** Unpacking & Evasion Techniques  

Dissection of a packed sample from the DarkSide ransomware family. The analysis focuses on the malware's evasion techniques and cryptographic operations.
* **Key Findings:** Successfully unpacked the sample in-memory to identify dynamic API resolution.
* **Persistence:** Mapped the usage of `AppInit_DLLs` and fake uninstall keys to maintain system presence.
* **Destructive Capabilities:** Documented shadow copy deletion routines used to prevent system recovery.

[📄 **Read Full Report**](https://docs.google.com/document/d/1DGtNUYlayocie2kwqCM0FYc6prv-ygazlcsBVDkmwhw/edit?usp=sharing)

---

## 🛠️ Technical Stack & Methodologies

* **Disassemblers/Debuggers:** Ghidra, x64dbg
* **Static Analysis:** PEStudio, Floss, Capa
* **Dynamic Analysis:** Process Monitor, Process Hacker, RegShot
* **Network Analysis:** Wireshark, FakeDNS, INetSim
* **Signature Dev:** YARA

---

### ⚠️ Disclaimer
*These reports are for educational and defensive purposes only. The samples analyzed were handled in a secure, isolated sandbox environment. Do not attempt to run live malware on a production network.*
