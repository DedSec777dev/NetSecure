# NetSecure - Advanced Packet Sniffer & Intrusion Detection System (IDS)

A powerful **web-based network monitoring and intrusion detection tool** built with Python.  
This application captures and analyzes network packets in real time, detects suspicious activity using signature and behavioral analysis, and allows administrators to actively block malicious traffic.

The tool is designed for **network monitoring, security analysis, and digital forensics**, providing both high-level insights and deep packet inspection capabilities.

---

## Features

### Real-Time Packet Capture
Capture live network traffic from selected network interfaces using **Scapy** and underlying **libpcap/Npcap** libraries.

### Intrusion Detection System (IDS)
Detect suspicious activities using:
- Signature-based detection (regex payload analysis)
- Behavioral detection (metadata thresholds)
- Port scan detection
- Suspicious payload pattern matching

### Target Domain Monitoring
Monitor traffic related to specific domains by resolving them to IP addresses and flagging packets associated with them.

### BPF Packet Filtering
Use **Berkeley Packet Filter (BPF)** expressions to capture only relevant packets.

Examples:
```
tcp port 80
host 192.168.1.10
src host 10.0.0.5 and dst port 22
icmp
```

### PCAP File Analysis
Upload `.pcap` or `.pcapng` files and analyze historical network traffic for threats.

### Dynamic IP / Domain Blocking
Automatically block malicious IP addresses or domains using system firewall rules.

- **Linux:** `iptables`
- **Windows:** `netsh advfirewall`

### Flagged Packet Logging
Suspicious packets are logged with:
- Source & destination IP
- Protocol
- Reason for detection
- Payload information

### Export Suspicious Traffic
Flagged packets can be exported to a **PCAP file**, allowing further analysis in tools like **Wireshark**.

### Web-Based Interface
A clean web dashboard provides:
- Live packet monitoring
- Suspicious packet alerts
- Firewall block management
- Searchable packet logs

---

# Architecture Overview

```
Network Traffic
       │
       ▼
Packet Capture (Scapy)
       │
       ▼
Packet Processing Engine
       │
 ┌───────────────┬────────────────┐
 ▼               ▼                ▼
Signature IDS   Behavioral IDS   Target Monitoring
       │
       ▼
Flagged Packet Detection
       │
       ▼
Firewall Blocking + Logging + PCAP Export
```

---

# Tech Stack

### Backend
- Python
- Flask
- Scapy
- Regex (Signature Detection)

### Networking
- libpcap (Linux)
- Npcap (Windows)

### System Modules
- threading
- subprocess
- socket
- collections
- tempfile

### Frontend
- HTML
- CSS
- JavaScript (Fetch API)

---

# Dependencies

Install required Python packages:

```bash
pip install flask scapy
```

### Linux Requirements

```
sudo apt install libpcap-dev
```

### Windows Requirements

Install **Npcap** from:

https://nmap.org/npcap/

During installation enable:

```
Install Npcap in WinPcap API-compatible Mode
```

---

# Running the Application

### Linux

Run with root privileges:

```bash
sudo python3 app.py
```

### Windows

Run command prompt as **Administrator**:

```bash
python app.py
```

Then open:

```
http://localhost:5000
```

---

# How to Use

### 1 Select Network Interface
Choose the interface from the dropdown to monitor network traffic.

### 2 Apply BPF Filter (Optional)
Add a BPF filter to capture specific traffic.

Example:

```
tcp port 443
```

### 3 Start Capture
Begin live packet monitoring.

### 4 Monitor Suspicious Packets
View flagged packets in the **Flagged Packets Log**.

### 5 Block Malicious IPs/Domains
Add IPs or domains in the **Blocking Management** section and apply firewall rules.

### 6 Analyze PCAP Files
Upload `.pcap` files for forensic analysis.

---

# Example Detection Capabilities

The IDS engine detects:

- Port scanning behavior
- Suspicious payload patterns
- DNS anomalies
- Large packet anomalies
- Suspicious keywords in payload
- Traffic to monitored domains

---

# Exported Data

Flagged packets are saved as:

```
flagged_packets.pcap
```

You can analyze them using:

- Wireshark
- tcpdump
- NetworkMiner

---

# Security Notice

This tool requires **Administrator / Root privileges** because:

- Packet sniffing requires raw socket access
- Firewall rules require elevated permissions

Use responsibly and only on networks you are authorized to monitor.

---

# Use Cases

- Network monitoring
- Security research
- Intrusion detection experiments
- Cybersecurity education
- Digital forensic analysis

---

# Future Improvements

- Machine Learning based anomaly detection
- Alert notifications
- Distributed network monitoring
- Advanced attack signatures
- Threat intelligence integration

---

# Repository

GitHub:
https://github.com/DedSec777dev/NetSecure

---

# License

This project is intended for **educational and research purposes only**.

---

# Author

Sahil Bisht

Cybersecurity Enthusiast | Network Security | Threat Detection

