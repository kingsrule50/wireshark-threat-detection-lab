# 🛡️ Network Threat Detection & Packet Analysis Lab

## 📌 Overview

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

## 🛡️ Detection Strategy

* Monitor abnormal SYN packet spikes
* Detect multi-port scanning patterns
* Identify repeated SMB enumeration attempts
* Correlate attacker IP across multiple services
* Use packet filtering to isolate malicious traffic

---

## 🔐 Mitigation

* Restrict SMB access (port 445)
* Disable guest/anonymous authentication
* Implement network segmentation (pfSense)
* Monitor network traffic for scanning behavior
* Enforce authentication controls

---

## 📊 Packet Analysis Evidence

### 🔹 SYN Scan Detection

![SYN Scan](screenshots/syn_scan.png)

---

### 🔹 RST/ACK Responses (Closed Ports)

![RST ACK](screenshots/rst_ack.png)

---

### 🔹 SMB Enumeration Attempt

![SMB Enumeration](screenshots/smb_enum.png)

---

### 🔹 Traffic Capture Overview

![Traffic Overview](screenshots/traffic_capture.png)

---

### 🔹 Filtered Packet Analysis

![Filtered View](screenshots/filtered_view.png)

---

### 🔹 Scan Activity Overview

![Scan Overview](screenshots/scan_overview.png)

---

### 🔹 Detailed Packet Analysis

![Analysis View](screenshots/analysis_view.png)

---

## 📁 Project Structure

wireshark-threat-detection-lab/
│
├── README.md
├── screenshots/
├── report/
│   ├── wireshark-lab-report.pdf
│   └── wireshark-lab-report.docx
├── pcap/
├── queries/

---

## 🎯 MITRE ATT&CK Mapping

* **Reconnaissance:** Active Scanning (T1595)
* **Discovery:** Network Service Discovery (T1046)
* **Lateral Movement (Attempted):** SMB/Windows Admin Shares (T1021.002)

---

## 🎯 Conclusion

This lab successfully demonstrates how reconnaissance and enumeration activities appear in network traffic and how defensive controls such as authentication enforcement and segmentation reduce attack success.

---

## 👤 Author

**Chinedu Kingsley Asuzu**
Cybersecurity Analyst | SOC | Cloud Security Engineer

