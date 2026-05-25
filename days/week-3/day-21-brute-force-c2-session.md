# Day 21 — Performing a Brute Force Attack and Establishing a C2 Session

**Week:** 3 | **Topic:** Adversary Simulation
**Original file:** `Day 21 Performing a Brute Force Attack and Establishing a C2 Session.md`

---

## 📋 Overview
Executing the simulated attack: brute forcing SSH credentials, gaining access, downloading the Mythic C2 agent, and establishing a C2 beacon — all within the isolated lab environment.

## 🎯 Attack Simulation Steps
- Use brute force tool against the lab SSH server
- Authenticate with obtained credentials
- Download Mythic Apollo agent to the compromised machine
- Execute the agent to establish a C2 beacon to the Mythic server
- Verify the beacon appears in the Mythic C2 console
- Run basic post-compromise commands via the C2 session

## 🔍 Logs Generated for Detection
- SSH authentication events in `system.auth`
- Process creation events (Sysmon Event ID 1)
- Network connection events (Sysmon Event ID 3)
- Outbound connections to Mythic C2 IP

## ⚠️ Lab Context
> All activity performed within an isolated private cloud lab. No real systems targeted.

## 📝 Notes
> Refer to the original day file for full walkthrough and screenshots.

*← [Back to Week 3](.) | [Back to README](../../README.md)*
