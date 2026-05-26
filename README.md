# 🛡️ 30-Day SOC Analyst Challenge — MyDFIR

> A hands-on 30-day SOC lab covering SIEM deployment, brute force detection, C2 simulation, and incident response — built entirely on cloud infrastructure using the ELK Stack.

![Challenge](https://img.shields.io/badge/Challenge-30%20Day%20SOC-blue?style=flat-square)
![SIEM](https://img.shields.io/badge/SIEM-Elastic%20Stack-005571?style=flat-square&logo=elastic)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen?style=flat-square)
![Days](https://img.shields.io/badge/Days%20Completed-30%2F30-orange?style=flat-square)
![Cloud](https://img.shields.io/badge/Cloud-Vultr-007BFC?style=flat-square)
![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Ubuntu-lightgrey?style=flat-square)

---

## 📋 About This Challenge

The **MyDFIR 30-Day SOC Analyst Challenge** is a free, practical programme designed for cybersecurity learners who hold certifications but lack real-world hands-on experience. Over 30 days, I built a fully functional SOC home lab from scratch in the cloud — deploying a SIEM, ingesting real endpoint logs, simulating attacks, detecting threats in Kibana, and running end-to-end incident investigations.

> **Original challenge by:** [MyDFIR on YouTube](https://www.youtube.com/playlist?list=PLG6KGSNK4PuBb0OjyDIdACZnb8AoNBeq6)

---

## 📂 Repository Structure

```
30-day-soc-analyst-challenge/
├── README.md
├── .gitignore
├── docs/
│   ├── elastic-port-reference.md       ← Elastic Stack default port assignments
│   └── soc-student-resources.md        ← 10 cybersecurity resources with student discounts
├── images/
│   ├── Network_Diagram.png             ← Full lab network diagram
│   ├── Attack_Diagram.png              ← Attack simulation diagram
│   └── Server_Proof.png                ← Proof of completed lab servers
└── days/
    ├── week-1/                         ← Days 01–10 | ELK Setup & Log Ingestion
    ├── week-2/                         ← Days 11–17 | Brute Force Detection & Dashboards
    ├── week-3/                         ← Days 18–22 | C2 Simulation & Detection
    └── week-4/                         ← Days 23–30 | Ticketing, IR & Finalisation
```

---

## 🧰 Tools & Technologies

| Category | Tools |
|----------|-------|
| SIEM | Elasticsearch, Logstash, Kibana (ELK Stack) |
| Endpoint Telemetry | Sysmon, Elastic Agent, Fleet Server |
| Endpoint Protection | Microsoft Defender, Elastic Defend |
| C2 Framework | Mythic C2 |
| Ticketing / IR | osTicket |
| Cloud Infrastructure | Vultr (Windows Server 2022 + Ubuntu 22.04/24.04) |
| Attack Simulation | SSH/RDP Brute Force (Crowbar), Mythic C2 Agent (Apollo) |
| Diagramming | draw.io |
| Attack OS | Kali Linux (VMware) |

---

## 🗺️ Lab Architecture

```
┌──────────────────────────────────────────────────────────┐
│                       Vultr Cloud                        │
│                                                          │
│  ┌─────────────────┐       ┌──────────────────────────┐ │
│  │  ELK Stack      │◄──────│  Windows Server 2022     │ │
│  │  Elasticsearch  │       │  + Sysmon                │ │
│  │  Kibana (SIEM)  │       │  + Elastic Agent         │ │
│  │  Fleet Server   │       │  + MS Defender           │ │
│  └────────┬────────┘       └──────────────────────────┘ │
│           │                                              │
│           │                ┌──────────────────────────┐ │
│           └────────────────│  Ubuntu SSH Server       │ │
│                            │  + Elastic Agent         │ │
│                            └──────────────────────────┘ │
│                                                          │
│  ┌─────────────────┐       ┌──────────────────────────┐ │
│  │  Mythic C2      │       │  osTicket Server         │ │
│  │  (Attack Sim)   │       │  (Ticketing / IR)        │ │
│  └─────────────────┘       └──────────────────────────┘ │
└──────────────────────────────────────────────────────────┘
         ▲
         │  Attacker Laptop (Kali Linux — local VM)
```

---

## 📅 Daily Curriculum

### ✅ Week 1 — ELK Stack Setup & Log Ingestion (Days 01–10)

| Day | Topic |
|-----|-------|
| 01 | [Introduction and Network Diagram Creation](./days/week-1/day-01-introduction-and-network-diagram.md) |
| 02 | [ELK Stack — Elasticsearch, Logstash and Kibana](./days/week-1/day-02-elk-stack-overview.md) |
| 03 | [Setting Up an Elasticsearch Instance](./days/week-1/day-03-setting-up-elasticsearch.md) |
| 04 | [Installing and Configuring Kibana](./days/week-1/day-04-installing-kibana.md) |
| 05 | [Setting Up a Windows Server in the Cloud](./days/week-1/day-05-windows-server-cloud.md) |
| 06 | [Understanding Fleet Server and Elastic Agent](./days/week-1/day-06-fleet-server-elastic-agent.md) |
| 07 | [Setting Up Fleet Server and Installing Elastic Agent on Windows](./days/week-1/day-07-fleet-server-setup.md) |
| 08 | [Understanding and Using Sysmon](./days/week-1/day-08-understanding-sysmon.md) |
| 09 | [Installing and Configuring Sysmon](./days/week-1/day-09-installing-sysmon.md) |
| 10 | [Ingesting Sysmon and Microsoft Defender Logs into Elasticsearch](./days/week-1/day-10-ingesting-sysmon-defender-logs.md) |

### ✅ Week 2 — Brute Force Detection & Dashboards (Days 11–17)

| Day | Topic |
|-----|-------|
| 11 | [Understanding and Defending Against Brute Force Attacks](./days/week-2/day-11-brute-force-theory.md) |
| 12 | [Setting Up an SSH Server and Reviewing Authentication Logs](./days/week-2/day-12-ssh-server-setup.md) |
| 13 | [Installing Elastic Agent on SSH Server](./days/week-2/day-13-elastic-agent-ssh.md) |
| 14 | [Creating SSH Brute Force Alerts and Dashboards](./days/week-2/day-14-ssh-alerts-dashboards.md) |
| 15 | [Understanding and Protecting Against RDP Abuse](./days/week-2/day-15-rdp-abuse.md) |
| 16 | [Creating RDP and SSH Brute Force Detection Rules](./days/week-2/day-16-rdp-ssh-rules.md) |
| 17 | [Creating a Dashboard for RDP Activity](./days/week-2/day-17-rdp-dashboard.md) |

### ✅ Week 3 — C2 Simulation & Advanced Detection (Days 18–22)

| Day | Topic |
|-----|-------|
| 18 | [Command and Control (C2) in Cyber Security](./days/week-3/day-18-c2-theory.md) |
| 19 | [Creating an Attack Diagram](./days/week-3/day-19-attack-diagram.md) |
| 20 | [Setting Up Mythic C2 Instance](./days/week-3/day-20-mythic-c2-setup.md) |
| 21 | [Performing a Brute Force Attack and Establishing a C2 Session](./days/week-3/day-21-brute-force-c2-session.md) |
| 22 | [Creating Alerts and Dashboards for Mythic C2 Activity](./days/week-3/day-22-mythic-alerts-dashboards.md) |

### ✅ Week 4 — Ticketing, Incident Response & Finalisation (Days 23–30)

| Day | Topic |
|-----|-------|
| 23 | [Introduction to Ticketing Systems](./days/week-4/day-23-ticketing-systems.md) |
| 24 | [Setting Up and Configuring osTicket](./days/week-4/day-24-osticket-setup.md) |
| 25 | [Integrating osTicket into Your Tech Stack](./days/week-4/day-25-osticket-integration.md) |
| 26 | [Investigating an SSH Brute Force Alert](./days/week-4/day-26-investigating-ssh-alert.md) |
| 27 | [Investigating an RDP Brute Force Alert](./days/week-4/day-27-investigating-rdp-alert.md) |
| 28 | [Investigating Mythic C2 Framework](./days/week-4/day-28-investigating-mythic-c2.md) |
| 29 | [Installing Elastic Defend](./days/week-4/day-29-elastic-defend.md) |
| 30 | [Troubleshooting and Finalising Setup](./days/week-4/day-30-troubleshooting-and-finalising.md) |

---

## 🧠 Skills Gained

- ✅ Deployed and configured a full **ELK Stack SIEM** on cloud infrastructure from scratch
- ✅ Ingested endpoint telemetry using **Sysmon**, **Elastic Agent**, and **Fleet Server**
- ✅ Built **Kibana detection rules** for SSH and RDP brute force attacks
- ✅ Created **custom Kibana dashboards** for real-time threat visualisation
- ✅ Deployed and operated **Mythic C2** to simulate real attacker post-compromise behaviour
- ✅ Detected **C2 beaconing activity** and built corresponding alert rules
- ✅ Set up and integrated **osTicket** for SOC alert triage and ticketing workflows
- ✅ Conducted end-to-end **incident investigations**: SSH brute force, RDP abuse, C2 activity
- ✅ Installed and configured **Elastic Defend** for endpoint detection and response (EDR)
- ✅ Built **network and attack diagrams** to document full lab architecture

---

## 📚 Reference Docs

- [Elastic Stack Default Port Reference](./docs/elastic-port-reference.md)
- [10 Cybersecurity Resources with Student Discounts](./docs/soc-student-resources.md)

---

## 🔗 Resources

- 🎥 [MyDFIR YouTube Challenge Playlist](https://www.youtube.com/playlist?list=PLG6KGSNK4PuBb0OjyDIdACZnb8AoNBeq6)
- ☁️ [Vultr Cloud — $300 Free Credit for New Accounts](https://www.vultr.com/?ref=9632889-9J)
- 📖 [Elastic Stack Documentation](https://www.elastic.co/guide/index.html)
- 🔧 [Sysmon — Microsoft Sysinternals](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
- 🎯 [Mythic C2 Framework](https://github.com/its-a-feature/Mythic)
- 🎫 [osTicket Documentation](https://docs.osticket.com)

---

## 🗂️ My Other Security Projects

- 🔍 [KC7 KQL Query Repository](https://github.com/mohsinnazir967/kc7-kql-queries) — 79 documented KQL queries across 4 investigations, mapped to MITRE ATT&CK

---

## 👤 About Me

SOC Analyst in training — building hands-on skills through real lab environments, structured challenges, and cybersecurity investigation games.

- 📍 Rawalpindi, Pakistan

---

*Completed as part of the free MyDFIR 30-Day SOC Analyst Challenge. All lab work performed on personal cloud infrastructure for educational purposes.*
