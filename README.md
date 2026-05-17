<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:101827,100:0d1117&height=210&section=header&text=GRIDWATCH&fontSize=82&fontColor=00D4FF&fontAlignY=36&desc=Network%20Security%20Automation%20Platform%20by%20Syndrax&descAlignY=58&descColor=94A3B8&animation=fadeIn" width="100%" alt="Gridwatch header"/>

<br />

[![License: MIT](https://img.shields.io/badge/License-MIT-00D4FF?style=for-the-badge)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.8+-101827?style=for-the-badge&logo=python&logoColor=00D4FF)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-101827?style=for-the-badge&logo=linux&logoColor=00D4FF)](#-getting-started)
[![Status](https://img.shields.io/badge/Status-Active%20Development-101827?style=for-the-badge&logo=github&logoColor=00D4FF)](#-roadmap)
[![Sponsored by Syndrax](https://img.shields.io/badge/Sponsored%20by-Syndrax-101827?style=for-the-badge&logoColor=00D4FF)](https://www.syndrax.io)

<br />

### Automated network visibility, threat intelligence, malware scanning, and RAT detection.

Gridwatch is a modular security platform that helps teams discover devices, monitor network activity, check threat intelligence sources, and generate readable security reports from one lightweight Python tool.

<br />

[Features](#-features) • [Architecture](#-architecture) • [Dashboard](#-dashboard-preview) • [Install](#-getting-started) • [Roadmap](#-roadmap) • [Team](#-team)

<br />

**A [Syndrax](https://www.syndrax.io) sponsored project**  
[syndrax.io/gridwatch](https://www.syndrax.io/gridwatch)

</div>

---

## ⚡ Why Gridwatch?

Most small networks do not have a full security team, SIEM, SOC, or enterprise monitoring stack. Gridwatch is designed to give defenders a practical first layer of visibility:

- See what devices are on the network
- Pull known malicious IP intelligence
- Watch active connections for suspicious destinations
- Run basic multi-engine malware checks
- Generate clean reports for technical and non-technical audiences

> **Goal:** simple setup, useful output, and clear next steps when something looks wrong.

---

## ✨ Features

<table>
<tr>
<td width="50%" valign="top">

### 🔴 Threat Intel Engine

Pulls known-bad IP lists from threat intelligence sources, removes duplicates, and builds one clean blocklist for firewall or review workflows.

**Includes:**
- EmergingThreats
- AbuseIPDB
- FireHOL
- Nightly update workflow

</td>
<td width="50%" valign="top">

### 🟠 Network Scanner

Discovers devices on your subnet and builds a simple inventory of IP addresses, MAC addresses, ports, and device information.

**Useful for:**
- Finding unknown devices
- Daily network snapshots
- Device inventory tracking
- Small business audits

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🟡 Multi-AV Scanner

Runs multiple detection checks against active files and processes so one missed result does not become a blind spot.

**Designed for:**
- Active process review
- Suspicious file checks
- Lightweight malware scanning
- Reportable findings

</td>
<td width="50%" valign="top">

### 🟢 RAT Watch

Monitors outbound connections and flags processes communicating with suspicious or unknown destinations.

**Helps detect:**
- Remote Access Trojans
- Spyware behavior
- Unknown outbound traffic
- Suspicious process activity

</td>
</tr>
</table>

---

## 🔧 How It Works

```text
┌────────────────────────────────────────────────────────────────────┐
│                            GRIDWATCH                               │
│                                                                    │
│   ┌────────────────┐    ┌────────────────┐    ┌────────────────┐  │
│   │ Threat Intel   │    │ Network Scan   │    │ Multi-AV Scan  │  │
│   │ Blocklists     │    │ Device Map     │    │ File Checks    │  │
│   └───────┬────────┘    └───────┬────────┘    └───────┬────────┘  │
│           │                     │                     │           │
│           └─────────────────────┼─────────────────────┘           │
│                                 │                                 │
│                         ┌───────▼────────┐                        │
│                         │   RAT Watch    │                        │
│                         │ Connections    │                        │
│                         └───────┬────────┘                        │
│                                 │                                 │
│           ┌─────────────────────┼─────────────────────┐           │
│           ▼                     ▼                     ▼           │
│   ┌──────────────┐      ┌──────────────┐      ┌──────────────┐    │
│   │ Dashboard    │      │ Alerts       │      │ PDF Report   │    │
│   └──────────────┘      └──────────────┘      └──────────────┘    │
└────────────────────────────────────────────────────────────────────┘
```

### Execution flow

| Step | Stage | What happens |
|:---:|:---|:---|
| 1 | Initialize | Loads config and validates dependencies |
| 2 | Fetch Threats | Pulls and merges malicious IP lists |
| 3 | Scan Network | Discovers devices on the local subnet |
| 4 | Analyze Processes | Cross-checks active connections against threat data |
| 5 | AV Scan | Runs malware checks against selected files/processes |
| 6 | Output | Generates dashboard results, alerts, and PDF reports |

---

## 🗂️ Architecture

```text
gridwatch/
├── gridwatch.py              # Main orchestrator
├── blocklist.txt             # Generated malicious IP blocklist
├── discovered_devices.txt    # Current network inventory
│
├── engines/
│   ├── threat_intel.py       # Threat intelligence engine
│   ├── network_scan.py       # Network discovery engine
│   ├── multi_av.py           # Multi-engine AV scanner
│   └── rat_watch.py          # Outbound connection monitor
│
├── reports/
│   └── report_generator.py   # PDF report generator
│
├── config/
│   └── settings.yaml         # Runtime configuration
│
└── utils/
    └── helpers.py            # Shared helper functions
```

---

## 📊 Dashboard Preview

```text
╔══════════════════════════════════════════════════════════╗
║              GRIDWATCH — Network Security Monitor        ║
╚══════════════════════════════════════════════════════════╝

  📡 NETWORK
  ─────────────────────────────────────────────────────
  Devices Discovered       127
  New Devices              0
  Unknown Devices          0

  🛡️ THREAT INTELLIGENCE
  ─────────────────────────────────────────────────────
  Malicious IPs Blocked    3,275
  Sources Active           FireHOL · AbuseIPDB · EmergingThreats
  Last Update              2026-05-03 03:00:01

  🦠 ANTIVIRUS
  ─────────────────────────────────────────────────────
  Engines Running          ClamAV ✓   YARA ✓
  Last Scan                2026-05-03 02:45:00
  Threats Found            0

  🎯 RAT WATCH
  ─────────────────────────────────────────────────────
  Connections Monitored    156
  Suspicious               0
  Status                   ✓ All Clear

══════════════════════════════════════════════════════════
```

---

## 🚨 Alert Example

```text
══════════════════════════════════════════════════════════
  ⚠️  GRIDWATCH SECURITY ALERT — HIGH SEVERITY
══════════════════════════════════════════════════════════

  PROCESS
  Name          suspicious_app.exe
  PID           4832
  Path          C:\Users\Admin\AppData\Local\Temp\
  User          DESKTOP-XYZ\Administrator

  CONNECTION
  Destination   185.234.XX.XX : 443
  Protocol      TCP
  State         ESTABLISHED

  THREAT MATCH
  Source        FireHOL Level 1
  Category      Known C2 Server
  Confidence    HIGH

  ACTIONS TAKEN
  ✓ Connection logged
  ✓ Process flagged
  ⚠ Manual review recommended

  NEXT STEPS
  1. Kill or isolate the process
  2. Quarantine the file for analysis
  3. Run a full antivirus scan
  4. Check startup and persistence locations
  5. Review user and system activity logs

══════════════════════════════════════════════════════════
```

---

## 📄 Report Generation

Gridwatch can generate a professional PDF security report for IT managers, business owners, and technical teams.

**Report includes:**

- Security score and letter grade
- Plain-English executive summary
- Network device inventory
- Findings ranked by severity
- Recommended fixes and next steps

```bash
python gridwatch.py --report
```

---

## 🚀 Getting Started

### Prerequisites

| Requirement | Notes |
|:---|:---|
| Python 3.8+ | Required runtime |
| Admin/root access | Needed for network scanning features |
| Npcap | Required on Windows for ARP scanning |
| libpcap-dev | Required on Linux for packet/network scanning |

### Install

```bash
# Clone the repository
git clone https://github.com/Gridwatch-OS/gridwatch.git
cd gridwatch

# Install dependencies
pip install requests scapy psutil
```

### Run

```bash
# Windows — run terminal as Administrator
python gridwatch.py

# Linux — run with root privileges
sudo python3 gridwatch.py
```

### Quick checks

```bash
# View discovered devices
cat discovered_devices.txt

# View generated threat blocklist
cat blocklist.txt
```

---

## 📍 Roadmap

| Phase | Status | Focus |
|:---|:---:|:---|
| Phase 1 — Base Model | ✅ Complete | Threat intel, network scan, process analysis, terminal output |
| Phase 2 — Engine Expansion | 🔄 In Progress | AbuseIPDB, EmergingThreats, ClamAV, YARA, device fingerprinting |
| Phase 3 — Automation | 📅 Planned | Background service, scheduled scans, PDF reports, email alerts |
| Phase 4 — Dashboard | 🔮 Future | Web UI, multi-site monitoring, API layer |
| Phase 5 — Enterprise Integrations | 🔮 Future | SIEM export, firewall sync, role-based access, audit logs |

---

## 👥 Team

<div align="center">

<table>
<tr>
<td align="center" width="220">
<img src="https://github.com/arthurperch.png" width="90" height="90" style="border-radius:50%" alt="Oleg P"/>
<br /><br />
<b><a href="https://www.linkedin.com/in/oleg-perchatkin-b90472161/">Oleg P</a></b>
<br />
<sub>Lead Engineer & Infrastructure</sub>
<br /><br />
<a href="https://github.com/arthurperch">
<img src="https://img.shields.io/badge/GitHub-arthurperch-101827?style=flat-square&logo=github&logoColor=00D4FF" alt="GitHub arthurperch"/>
</a>
</td>
<td align="center" width="220">
<img src="https://github.com/Jackt5.png" width="90" height="90" style="border-radius:50%" alt="Giovanny P"/>
<br /><br />
<b><a href="https://www.linkedin.com/in/giovanny-jr-valerio-perdomo-6202a4138/">Giovanny P</a></b>
<br />
<sub>Engine Development</sub>
<br /><br />
<a href="https://github.com/Jackt5">
<img src="https://img.shields.io/badge/GitHub-Jackt5-101827?style=flat-square&logo=github&logoColor=00D4FF" alt="GitHub Jackt5"/>
</a>
</td>
<td align="center" width="220">
<img src="https://github.com/Tia-Henderson.png" width="90" height="90" style="border-radius:50%" alt="Tia H"/>
<br /><br />
<b><a href="https://www.linkedin.com/in/tia-henderson-/">Tia H</a></b>
<br />
<sub>Security & QA</sub>
<br /><br />
<a href="https://github.com/Tia-Henderson">
<img src="https://img.shields.io/badge/GitHub-Tia--Henderson-101827?style=flat-square&logo=github&logoColor=00D4FF" alt="GitHub Tia-Henderson"/>
</a>
</td>
</tr>
</table>

</div>

---

## 🤝 Contributing

Gridwatch is modular by design. Contributors can improve one engine without needing to rewrite the whole platform.

```bash
# 1. Fork the repository

# 2. Create a feature branch
git checkout -b feature/your-engine-improvement

# 3. Commit your work with a clear message
git commit -m "feat(engine-1): add AbuseIPDB source integration"

# 4. Push your branch
git push origin feature/your-engine-improvement

# 5. Open a pull request
```

### Contribution guidelines

- Keep code readable and well-commented
- Add docstrings to functions
- Test on Windows and Linux when possible
- Update the README when behavior changes
- Keep security findings clear, factual, and reproducible

---

## 📝 License

Gridwatch is released under the MIT License. See [LICENSE](LICENSE) for details.

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:101827,100:0d1117&height=120&section=footer&animation=fadeIn" width="100%" alt="Gridwatch footer"/>

**Built by the Gridwatch Team**  
Sponsored by [Syndrax](https://www.syndrax.io) • Protecting networks, one scan at a time.

</div>
