# Day 11 — Understanding and Defending Against Brute Force Attacks

**Week:** 2 | **Topic:** Threat Detection Theory
**Original file:** `Day 11 Understanding and Defending Against Brute Force Attacks.md`

---

## 📋 Overview
Deep dive into brute force attack techniques, tools attackers use, and the defensive controls and detection strategies a SOC analyst applies.

## 🎯 Key Concepts
- What brute force attacks are: credential stuffing, password spraying, dictionary attacks
- Common tools used: Hydra, Medusa, Ncrack
- Targets: SSH (port 22), RDP (port 3389), web login forms
- Detection signals: repeated failed auth events in short time windows
- Key log sources: `/var/log/auth.log` (Linux), Windows Event ID 4625 (failed logon)
- Defensive controls: account lockout policies, MFA, fail2ban, geo-blocking

## 🔍 Key Event IDs for Detection

| Event ID | Description | Log Source |
|----------|-------------|------------|
| 4625 | Failed logon attempt | Windows Security |
| 4624 | Successful logon | Windows Security |
| 4648 | Logon using explicit credentials | Windows Security |

## 📝 Notes
> Refer to the original day file for full explanations and examples.

*← [Back to Week 2](.) | [Back to README](../../README.md)*
