# Day 18: Command and Control (C2) in Cyber Security

**Week:** 3 | **Phase:** Adversary Simulation Theory
**← [Back to README](../../README.md) | [← Day 17](../week-2/day-17-rdp-dashboard.md)**

---

## 1. Introduction

**Goal:** Understand Command and Control (C2) and its significance in cyber security.

---

## 2. What is Command and Control (C2)?

**Definition:** Techniques used by adversaries to communicate with systems under their control within a victim's network.

**Importance:** Allows attackers to perform additional actions to achieve their objectives — e.g., stealing credentials, moving laterally, stealing sensitive information, executing ransomware.

---

## 3. Common Tools and Frameworks

**Metasploit:**
- Popular framework in Kali Linux.
- Owner: Rapid7.
- Contains various exploits and auxiliaries.

**Cobalt Strike:**
- Commercial product built for adversary emulation by Fortra.
- Commonly seen in compromised environments.
- Detection resources available (e.g., DFIR Report).

**Sliver:**
- Open-source framework by Bishop Fox.
- Supports mTLS, HTTP, HTTPS, DNS, WireGuard.
- Designed as an open-source alternative to Cobalt Strike.

**Mythic:**
- Used in the 30-day challenge.
- Built with Golang, Docker, Docker Compose, web browser UI.
- Tracks payloads and C2 profiles; supports 21 different agents.

---

## 4. Next Steps

**Tasks:**
- Craft an attack on a Windows server.
- Set up a Mythic server.
- Deploy an agent to establish a successful C2 session.

---

*→ Next: [Day 19 — Attack Diagram](./day-19-attack-diagram.md)*
