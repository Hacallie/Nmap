# Week 2: Nmap Network Scanning Lab

**Author:** Allison Abdullahi  
**Program:** Cybersecurity Personal Training 
**Date:** September 2026  
**Lab Environment:** VirtualBox NAT Network (10.0.0.0/24)

---

## 📋 Project Overview

This lab focuses on **network reconnaissance and host discovery** using Nmap, a fundamental security testing tool. The goal was to:

1. Identify active hosts on my lab network
2. Perform port scanning to discover open services
3. Attempt OS detection on target systems
4. Document findings and methodology
5. Learn practical network analysis skills

This is a **controlled lab environment** for educational purposes only.

---

## 🔬 Lab Environment

### Network Setup
- **Network Type:** VirtualBox NAT Network
- **Network Name:** CyberLab-NAT
- **Network Range:** 10.0.0.0/24
- **Gateway:** 10.0.0.1
- **Host Machine:** Windows 10 (Host OS)

### Systems in Lab
| IP Address | Hostname | OS | MAC Address | Role |
|---|---|---|---|---|
| 10.0.0.1 | NAT Gateway | Virtual | 52:54:00:12:35:00 | Network Gateway |
| 10.0.0.2 | Windows-10-Lab | Windows 10 | 08:00:27:1A:F4:99 | Target System |
| 10.0.0.3 | kali | Kali Linux | N/A | Scanning System |

### Tools Used
- **Nmap 7.99** - Network scanning and reconnaissance
- **Kali Linux** - Penetration testing platform
- **VirtualBox** - Virtualization platform

---

## 🎯 Scanning Methodology

### Scan 1: Ping Sweep (Network Discovery)

**Command:**
```bash
nmap -sn 10.0.0.0/24
```

**Purpose:**
- Identify all live hosts on the network
- Use ICMP ping to discover active devices
- `-sn` flag performs ping scan without port scanning

**Results:**
```
Nmap scan report for 10.0.0.1
Host is up (0.00061s latency).
MAC Address: 52:54:00:12:35:00 (QEMU virtual NIC)

Nmap scan report for 10.0.0.2
Host is up (0.00058s latency).
MAC Address: 08:00:27:1A:F4:99 (Oracle VirtualBox virtual NIC)

Nmap scan report for 10.0.0.3
Host is up.

Nmap done: 256 IP addresses (3 hosts up) scanned in 3.02 seconds
```

**Key Findings:**
- ✅ 3 active hosts discovered
- ✅ Gateway (10.0.0.1) responding
- ✅ Windows VM (10.0.0.2) is online
- ✅ Kali machine (10.0.0.3) confirmed active

---

### Scan 2: Full Port Scan (Service Discovery)

**Command:**
```bash
nmap -p- 10.0.0.2
```

**Purpose:**
- Scan all 65,535 TCP ports on Windows VM
- Identify any open/listening services
- `-p-` flag scans all ports

**Results:**
```
Nmap scan report for 10.0.0.2
Host is up (0.00016s latency).
All 65535 scanned ports on 10.0.0.2 are in ignored states.
Not shown: 65535 closed tcp ports (reset)
MAC Address: 08:00:27:1A:F4:99 (Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 6.43 seconds
```

**Key Findings:**
- ✅ Windows VM firewall is active
- ✅ All 65,535 ports are closed
- ✅ No exposed services discovered
- ✅ System is responding to network traffic

---

### Scan 3: OS Detection Scan

**Command:**
```bash
nmap -O 10.0.0.2
```

**Purpose:**
- Attempt to identify the operating system
- Use TCP/IP fingerprinting
- `-O` flag enables OS detection

**Results:**
```
Nmap scan report for 10.0.0.2
Host is up (0.00064s latency).
All 1000 scanned ports on 10.0.0.2 are in ignored states.
Not shown: 1000 closed tcp ports (reset)
MAC Address: 08:00:27:1A:F4:99 (Oracle VirtualBox virtual NIC)

Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Aggressive OS guesses: [Multiple device types listed]
No exact OS matches for host (test conditions non-ideal).
Network Distance: 1 hop

OS detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 2.40 seconds
```

**Key Findings:**
- ⚠️ OS detection inconclusive (requires open ports)
- ✅ Network distance = 1 hop (local network)
- ✅ System is responding to probes
- 💡 Closed ports actually protect OS fingerprinting

---

## 📊 Analysis & Learnings

### What the Scans Revealed

1. **Network Topology**
   - Successfully mapped all devices on CyberLab-NAT network
   - Confirmed three-system lab environment is functional
   - All systems communicating correctly

2. **Security Posture**
   - Windows VM has proper firewall configuration
   - No unnecessary open ports or services
   - Good security hygiene for a lab environment

3. **Nmap Capabilities**
   - Ping scans quickly identify live hosts
   - Port scanning reveals service exposure
   - OS detection requires open ports (fingerprinting limitation)
   - Latency times show local network connectivity

### Key Cybersecurity Concepts Learned

- **Network Reconnaissance:** First step in security testing
- **Host Discovery:** Identifying active systems before detailed scanning
- **Port Scanning:** Understanding what services are exposed
- **Firewall Behavior:** How firewalls respond to probe packets
- **OS Fingerprinting:** Techniques and limitations for identifying systems
- **Network Architecture:** Lab network design and isolation

---

## 🛡️ Ethical Scope & Authorized Testing

**IMPORTANT:** This lab work was performed on:
- ✅ Systems I own and control
- ✅ A personal lab environment (VirtualBox)
- ✅ An isolated network (10.0.0.0/24 NAT)
- ✅ With explicit authorization on all systems

This is **authorized security testing** for educational purposes within the NetworkWalks program.

**This lab does NOT involve:**
- ❌ Scanning external/production systems
- ❌ Testing systems without permission
- ❌ Attempting unauthorized access
- ❌ Malicious activity

---

## 🎓 Next Steps

Future lab work will explore:
- Service enumeration on intentionally vulnerable systems
- Vulnerability scanning and assessment
- Web application security testing
- More advanced Nmap techniques (NSE scripts, custom payloads)
- Integration with other security tools

---

## 📁 Repository Contents

```
Week2-Nmap-Lab/
├── README.md (this file)
├── screenshots/
│   ├── 01-nmap-version.png
│   ├── 02-ping-sweep-results.png
│   ├── 03-port-scan-results.png
│   └── 04-os-detection-results.png
├── lab-notes.md (raw notes from testing)
└── commands-reference.md (Nmap commands used)
```

---

## 🔗 Related Work

**Previous Lab:** [Week 1 - Kali Linux Lab Setup](https://github.com/Hacallie/Week1project)

**Program:** [NetworkWalks Cybersecurity Internship](https://networkwalks.com)

---

## 📝 Notes

- Nmap version: 7.99
- Lab OS: Kali Linux (x86_64)
- Testing date: September 11, 2026
- Lab duration: ~30 minutes for scanning
- Total lab time: ~2 hours (including documentation)

---

## 📧 Questions or Feedback?

This project is part of my journey building cybersecurity skills from the ground up. If you have questions about the methodology or findings, feel free to reach out.

**GitHub:** [Hacallie](https://github.com/Hacallie)

---

*Last updated: September 11, 2026*
