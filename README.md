# 🛡️ Network Threat Detection & Packet Analysis Lab
![Status](https://img.shields.io/badge/status-completed-brightgreen)
![Tool](https://img.shields.io/badge/tool-Wireshark-blue)
![Focus](https://img.shields.io/badge/focus-threat--detection-red)
## 📌 Overview

This lab is designed to reflect real SOC investigation workflows using packet-level analysis.

This project simulates real-world attacker reconnaissance and service enumeration within a segmented lab environment. Network traffic was captured and analyzed using Wireshark to identify malicious behavior and validate defensive controls.

---

## 🧪 Lab Environment

* **Firewall:** pfSense (Network Segmentation)
* **Attacker Machine:** Kali Linux
* **Target Machine:** Windows 11
* **Tools Used:** Wireshark, Nmap, SMBclient

---

## 🚨 Attack Simulation

The attacker performed:

* SYN-based port scanning
* Service enumeration
* SMB enumeration attempts

Traffic was captured and analyzed to identify patterns associated with reconnaissance activity.

---

## 🔍 Key Findings

* Multiple ports probed across the target system
* Port **445 (SMB)** confirmed open
* RST/ACK responses observed on closed ports
* SMB enumeration attempts detected
* Anonymous and guest access denied

---

## 🛡️ SOC Analyst Perspective

From a SOC perspective, this activity would trigger alerts for:

- High volume SYN packets indicating port scanning
- Multiple connection attempts across different ports
- SMB enumeration attempts from a single source IP

An analyst would investigate:

- Source IP address (192.168.20.11)
- Frequency and timing of connection attempts
- Targeted services (especially SMB on port 445)
- Authentication failures and access denial logs

This behavior is consistent with reconnaissance activity in the early stages of an attack.

---

## 🛡️ Detection Strategy

* Monitor abnormal SYN packet spikes
* Detect multi-port scanning patterns
* Identify repeated SMB enumeration attempts
* Correlate attacker IP across multiple services
* Use packet filtering to isolate malicious traffic

> These detection patterns can be operationalized in SIEM platforms such as Splunk for real-time alerting.

---

## 🔐 Mitigation

* Restrict SMB access (port 445)
* Disable guest/anonymous authentication
* Implement network segmentation (pfSense)
* Monitor network traffic for scanning behavior
* Enforce authentication controls

---

## 📊 Packet Analysis Evidence

### 🔹 Wireshark Capture Initialization
Wireshark configured to capture traffic on the active interface.

![Capture Setup](screenshots/traffic_capture.png)

---

### 🔹 Nmap SYN Scan – Service Discovery  
TCP SYN scan identifies open ports on the target.

![Scan Overview](screenshots/scan_overview.png)


---

### 🔹 SYN Scan Activity Observed in Wireshark
Attacker scanning target; closed ports return RST/ACK, port 445 open.

![RST ACK](screenshots/rst_ack.png)

---

### 🔹 Filtered SYN Packets (Port Scanning Evidence)

Filter:
`tcp.flags.syn == 1 && tcp.flags.ack == 0`

![SYN Scan](screenshots/syn_scan.png)

---

### 🔹 Attacker Source Traffic Analysis

Filter:
`ip.src == 192.168.20.11`

![Attacker Traffic](screenshots/filtered_view.png)

---

### 🔹 SMB Enumeration Attempts with Access Denied
SMB enumeration attempts failed due to authentication controls.

![SMB Enumeration](screenshots/smb_enum.png)

---

## 📁 Project Structure

```
wireshark-threat-detection-lab/
│
├── README.md
├── screenshots/
├── report/
│   ├── wireshark-lab-report.pdf
│   └── wireshark-lab-report.docx
```

---

## 🎯 MITRE ATT&CK Mapping

* **Reconnaissance:** Active Scanning (T1595)
* **Discovery:** Network Service Discovery (T1046)
* **Lateral Movement (Attempted):** SMB/Windows Admin Shares (T1021.002)

---

## 🧠 Skills Demonstrated

- Network Traffic Analysis (Wireshark)
- Packet Inspection and Filtering
- Threat Detection & Pattern Recognition
- SYN Scan Identification
- SMB Enumeration Analysis
- Security Investigation Workflow

## 🎯 Conclusion

This project demonstrates how reconnaissance and enumeration activity can be identified at the packet level, enabling SOC analysts to detect early-stage attacks before exploitation occurs.

## 👤 Author

**Chinedu Kingsley Asuzu**
Cybersecurity Analyst | SOC | Cloud Security Engineer

