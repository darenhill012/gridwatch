
<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:101827,100:0d1117&height=220&section=header&text=GRIDWATCH&fontSize=90&fontColor=00D4FF&fontAlignY=36&desc=Network%20Security%20Automation%20Platform&descAlignY=58&descColor=94A3B8&animation=fadeIn" width="100%"/>

<br/>

[![License: MIT](https://img.shields.io/badge/License-MIT-00D4FF?style=for-the-badge)](LICENSE)
[![Python](https://img.shields.io/badge/Python-3.8+-101827?style=for-the-badge&logo=python&logoColor=00D4FF)](https://www.python.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux-101827?style=for-the-badge&logo=linux&logoColor=00D4FF)](#-getting-started)
[![Status](https://img.shields.io/badge/Status-Active%20Development-101827?style=for-the-badge&logo=github&logoColor=00D4FF)](#-roadmap)
[![Syndrax](https://img.shields.io/badge/Sponsored%20by-Syndrax-101827?style=for-the-badge&logoColor=00D4FF)](https://www.syndrax.io)

<br/>

> ### Automated network visibility, threat intelligence, malware scanning, and RAT detection — all in one lightweight platform.

<br/>

[Features](#-features) &nbsp;•&nbsp; [How It Works](#-how-it-works) &nbsp;•&nbsp; [Dashboard](#-dashboard-preview) &nbsp;•&nbsp; [Getting Started](#-getting-started) &nbsp;•&nbsp; [Team](#-team) &nbsp;•&nbsp; [Roadmap](#-roadmap)

<br/>

**A [Syndrax](https://www.syndrax.io) sponsored project &nbsp;•&nbsp; [syndrax.io/gridwatch](https://www.syndrax.io/gridwatch)**

</div>

---

## ⚡ Why Gridwatch?

Most networks — especially in small businesses and nonprofits — have zero visibility into what is actually happening on their infrastructure. No SIEM. No SOC. No monitoring stack. Gridwatch fills that gap with a practical, deployable security platform that any team can run.

```
No subscription.   No license fees.   No manual updates.   Just protection.
```

- **Discover** every device on your network automatically
- **Block** thousands of known malicious IPs nightly
- **Detect** suspicious outbound connections and RAT behavior in real time
- **Scan** active processes with multiple AV engines simultaneously
- **Report** findings in plain English for technical and non-technical audiences

---

## ✨ Features

<table>
<tr>
<td width="50%" valign="top">

### 🔴 Engine 1 — Threat Intelligence
Pulls live malicious IP lists nightly from **EmergingThreats**, **AbuseIPDB**, and **FireHOL**. Deduplicates everything into one master blocklist and pushes it directly to your firewall automatically. Zero manual steps after setup.

</td>
<td width="50%" valign="top">

### 🟠 Engine 2 — Network Scanner
Maps every device on your subnet by IP, MAC address, open ports, and device type. Flags unknown devices that were not there yesterday and keeps a rolling network inventory updated automatically.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🟡 Engine 3 — Multi-AV Scanner
Runs multiple antivirus engines simultaneously against active files and processes. If one engine misses something, another catches it. Built for defense in depth with no single point of failure.

</td>
<td width="50%" valign="top">

### 🟢 Engine 4 — RAT Watch
Monitors every outbound connection in real time. Detects Remote Access Trojans and spyware by catching processes phoning home to unknown or malicious IPs before damage is done.

</td>
</tr>
</table>

---

## 🔧 How It Works

```text
┌──────────────────────────────────────────────────────────────────────┐
│                           GRIDWATCH CORE                             │
│                                                                      │
│   ┌──────────────┐    ┌──────────────┐    ┌──────────────┐          │
│   │  Engine 1    │    │  Engine 2    │    │  Engine 3    │          │
│   │ Threat Intel │    │ Net Scanner  │    │  Multi-AV    │          │
│   └──────┬───────┘    └──────┬───────┘    └──────┬───────┘          │
│          └──────────────────┬┴─────────────────── ┘                 │
│                             │                                        │
│                    ┌────────▼────────┐                               │
│                    │   Engine 4      │                               │
│                    │   RAT Watch     │                               │
│                    └────────┬────────┘                               │
│                             │                                        │
│          ┌──────────────────┼──────────────────┐                    │
│          ▼                  ▼                  ▼                    │
│   ┌─────────────┐   ┌─────────────┐   ┌─────────────┐              │
│   │  Dashboard  │   │   Alerts    │   │ PDF Report  │              │
│   └─────────────┘   └─────────────┘   └─────────────┘              │
└──────────────────────────────────────────────────────────────────────┘
```

| Step | Stage | What Happens |
|:---:|:---|:---|
| 1 | Initialize | Load config and verify dependencies |
| 2 | Fetch Threats | Pull and merge malicious IP lists from all sources |
| 3 | Scan Network | Discover and inventory all devices on the subnet |
| 4 | Analyze Processes | Cross-reference active connections against blocklist |
| 5 | AV Scan | Multi-engine scan against active files and processes |
| 6 | Output | Dashboard results, security alerts, and PDF report |

---

## 🗂️ Architecture

```text
gridwatch/
├── gridwatch.py                  # Main orchestrator
├── blocklist.txt                 # Generated malicious IP blocklist
├── discovered_devices.txt        # Live network device inventory
│
├── engines/
│   ├── threat_intel.py           # Engine 1 — Threat intelligence
│   ├── network_scan.py           # Engine 2 — Network discovery
│   ├── multi_av.py               # Engine 3 — Multi-AV scanner
│   └── rat_watch.py              # Engine 4 — RAT & spyware detection
│
├── reports/
│   └── report_generator.py       # PDF report generation
│
├── config/
│   └── settings.yaml             # Runtime configuration
│
└── utils/
    └── helpers.py                # Shared utility functions
```

---

## 📊 Dashboard Preview

```text
╔══════════════════════════════════════════════════════════════╗
║              GRIDWATCH  —  Network Security Monitor          ║
╚══════════════════════════════════════════════════════════════╝

  📡 NETWORK
  ──────────────────────────────────────────────────────────
  Devices Discovered         127
  New Devices                0
  Unknown Devices            0

  🛡️  THREAT INTELLIGENCE
  ──────────────────────────────────────────────────────────
  Malicious IPs Blocked      3,275
  Sources Active             FireHOL · AbuseIPDB · EmergingThreats
  Last Update                2026-05-17  03:00:01

  🦠 ANTIVIRUS
  ──────────────────────────────────────────────────────────
  Engines Running            ClamAV ✓   YARA ✓
  Last Scan                  2026-05-17  02:45:00
  Threats Found              0

  🎯 RAT WATCH
  ──────────────────────────────────────────────────────────
  Connections Monitored      156
  Suspicious                 0
  Status                     ✓  All Clear

══════════════════════════════════════════════════════════════
```

---

## 🚨 Alert Example

```text
══════════════════════════════════════════════════════════════
  ⚠️  GRIDWATCH SECURITY ALERT  —  HIGH SEVERITY
══════════════════════════════════════════════════════════════

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
  ✓  Connection logged
  ✓  Process flagged
  ⚠  Manual review recommended

  RECOMMENDED NEXT STEPS
  1.  Kill or isolate the process immediately
  2.  Quarantine the file for forensic analysis
  3.  Run a full system antivirus scan
  4.  Check startup and persistence locations
  5.  Review full user and system activity logs

══════════════════════════════════════════════════════════════
```

---

## 📄 Report Generation

Gridwatch generates a professional PDF security report designed to be handed directly to an IT manager, director, or business owner without requiring technical knowledge to understand.

**Every report includes:**
- Security score out of 100 with letter grade
- Plain-English executive summary
- Full network device inventory
- Findings ranked by severity
- Prioritized action items with step-by-step fix instructions

```bash
python gridwatch.py --report
```

---

## 🚀 Getting Started

### Prerequisites

| Requirement | Details |
|:---|:---|
| Python 3.8+ | Required runtime |
| Admin / Root access | Required for network scanning |
| Npcap | Windows only — required for ARP scanning |
| libpcap-dev | Linux only — required for packet capture |

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

### Quick Checks

```bash
# View all discovered devices
cat discovered_devices.txt

# View the generated threat blocklist
cat blocklist.txt
```

---

## 📍 Roadmap

| Phase | Status | Focus |
|:---|:---:|:---|
| Phase 1 — Base Model | ✅ Complete | Threat intel, network scan, process analysis, terminal output |
| Phase 2 — Engine Expansion | 🔄 In Progress | AbuseIPDB, EmergingThreats, ClamAV, YARA, device fingerprinting |
| Phase 3 — Automation | 📅 Planned | Background service, scheduled scans, PDF reports, email alerts |
| Phase 4 — Web Dashboard | 🔮 Future | Full web UI, multi-site monitoring, login portal |
| Phase 5 — Enterprise | 🔮 Future | SIEM export, firewall sync, role-based access, audit logs |

---

## 👥 Team

<div align="center">

<table>
<tr>
<td align="center" width="220">
<img src="https://github.com/arthurperch.png" width="100" height="100" style="border-radius:50%; border: 3px solid #00D4FF;" alt="Oleg P"/>
<br/><br/>
<b><a href="https://www.linkedin.com/in/oleg-perchatkin-b90472161/">Oleg P</a></b>
<br/>
<sub>☁️ Lead Engineer & Infrastructure</sub>
<br/><br/>
<a href="https://github.com/arthurperch">
<img src="https://img.shields.io/badge/GitHub-arthurperch-101827?style=flat-square&logo=github&logoColor=00D4FF"/>
</a>
</td>
<td align="center" width="220">
<img src="https://github.com/Jackt5.png" width="100" height="100" style="border-radius:50%; border: 3px solid #00D4FF;" alt="Giovanny P"/>
<br/><br/>
<b><a href="https://www.linkedin.com/in/giovanny-jr-valerio-perdomo-6202a4138/">Giovanny P</a></b>
<br/>
<sub>⚙️ Engine Development</sub>
<br/><br/>
<a href="https://github.com/Jackt5">
<img src="https://img.shields.io/badge/GitHub-Jackt5-101827?style=flat-square&logo=github&logoColor=00D4FF"/>
</a>
</td>
<td align="center" width="220">
<img src="https://github.com/Tia-Henderson.png" width="100" height="100" style="border-radius:50%; border: 3px solid #00D4FF;" alt="Tia H"/>
<br/><br/>
<b><a href="https://www.linkedin.com/in/tia-henderson-/">Tia H</a></b>
<br/>
<sub>🛡️ Security & QA</sub>
<br/><br/>
<a href="https://github.com/Tia-Henderson">
<img src="https://img.shields.io/badge/GitHub-Tia--Henderson-101827?style=flat-square&logo=github&logoColor=00D4FF"/>
</a>
</td>
</tr>
</table>

</div>

---

## 🤝 Contributing

Gridwatch is modular by design — each engine is fully independent so contributors can build and improve one component without touching the rest of the platform.

```bash
# 1. Fork the repository

# 2. Create your feature branch
git checkout -b feature/your-improvement

# 3. Commit with a clear message
git commit -m "feat(engine-2): improve device fingerprinting accuracy"

# 4. Push your branch
git push origin feature/your-improvement

# 5. Open a pull request
```

**Guidelines:**
- Write clean, well-commented code — others build on top of it
- Add docstrings to all functions
- Test on both Windows and Linux when possible
- Update the README if behavior changes
- Keep security findings clear, factual, and reproducible

---

## 📝 License

Released under the MIT License. See [LICENSE](LICENSE) for full details.

---

<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0d1117,50:101827,100:0d1117&height=130&section=footer&animation=fadeIn" width="100%"/>

**Built by the Gridwatch Team**

Sponsored by [Syndrax](https://www.syndrax.io) &nbsp;•&nbsp; Protecting networks, one scan at a time.

</div>
````
