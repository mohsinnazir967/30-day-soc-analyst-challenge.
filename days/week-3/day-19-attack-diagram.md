# Day 19 — Creating an Attack Diagram

**Week:** 3 | **Topic:** Documentation & Planning
**Original file:** `Day 19 Creating an Attack Diagram.md`

---

## 📋 Overview
Creating an attack diagram that maps the full simulated attack flow — from initial access through C2 establishment — before executing the simulation.

## 🎯 Attack Flow Documented

```
Attacker Machine
      │
      │ 1. Brute Force SSH/RDP
      ▼
Target Server (Windows/Ubuntu)
      │
      │ 2. Credentials Obtained
      ▼
Establish Foothold
      │
      │ 3. Download Mythic C2 Agent
      ▼
Mythic C2 Server
      │
      │ 4. C2 Beacon Established
      ▼
Post-Compromise Activity
(Discovery, Lateral Movement)
```

## 🎯 Key Steps
- Map each attack phase to MITRE ATT&CK tactics
- Identify which logs each phase generates
- Plan detection rules needed to catch each phase
- Document the diagram using draw.io

## 📝 Notes
> Refer to the original day file for the full diagram image.

*← [Back to Week 3](.) | [Back to README](../../README.md)*
