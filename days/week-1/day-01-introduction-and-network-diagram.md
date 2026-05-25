# Day 01 — Introduction and Network Diagram Creation

**Week:** 1 | **Topic:** Lab Planning & Architecture
**Original file:** `Day 01 Introduction and Network Diagram Creation.md`

---

## 📋 Overview

Introduction to the 30-day challenge and creating the network diagram for the full lab architecture. This day covers planning what the SOC lab will look like before building it.

---

## 🎯 Key Concepts

- What the 30-day challenge covers and why it matters for SOC roles
- How to plan a lab environment before deploying any infrastructure
- Network diagram components: servers, agents, data flows, and communication paths
- Why documentation and diagramming are core SOC analyst skills

---

## 🗺️ Lab Network Diagram

```
Internet
    │
    ▼
┌─────────────────────────────────────────────────────┐
│                    Vultr Cloud                      │
│                                                     │
│  ┌───────────────┐     ┌──────────────────────┐    │
│  │  ELK Stack    │◄────│  Windows Server 2022 │    │
│  │  (SIEM)       │     │  Sysmon + Agent      │    │
│  └───────┬───────┘     └──────────────────────┘    │
│          │                                          │
│          │             ┌──────────────────────┐    │
│          └─────────────│  Ubuntu SSH Server   │    │
│                        │  Elastic Agent       │    │
│  ┌───────────────┐     └──────────────────────┘    │
│  │  Mythic C2    │     ┌──────────────────────┐    │
│  └───────────────┘     │  osTicket Server     │    │
│                        └──────────────────────┘    │
└─────────────────────────────────────────────────────┘
```

---

## 📝 Notes

- Used **draw.io** to create the network diagram
- All VMs hosted on **Vultr** cloud platform
- Each component communicates on specific ports — see [Elastic Port Reference](../../docs/elastic-port-reference.md)

---

*← [Back to Week 1](.) | [Back to README](../../README.md)*
