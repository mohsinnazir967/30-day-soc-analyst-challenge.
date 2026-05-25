# Day 18 — Command and Control (C2) in Cyber Security

**Week:** 3 | **Topic:** Adversary Simulation Theory
**Original file:** `Day 18 Command and Control (C2) in Cyber Security.md`

---

## 📋 Overview
Understanding how attackers establish and use Command and Control infrastructure — a core concept for any SOC analyst detecting post-compromise activity.

## 🎯 Key Concepts
- What C2 is: attacker-controlled servers that communicate with compromised endpoints
- C2 communication methods: HTTP/S, DNS, SMB, custom protocols
- C2 frameworks used in real attacks: Cobalt Strike, Metasploit, Mythic, Sliver
- Beaconing behaviour: regular check-ins from implant to C2 server
- Detection signals: unusual outbound connections, beaconing intervals, non-standard ports

## 🔍 MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|--------|-----------|-----|
| Command & Control | Application Layer Protocol | T1071 |
| Command & Control | Encrypted Channel | T1573 |
| Command & Control | Ingress Tool Transfer | T1105 |

## 📝 Notes
> Refer to the original day file for full explanations and diagrams.

*← [Back to Week 3](.) | [Back to README](../../README.md)*
