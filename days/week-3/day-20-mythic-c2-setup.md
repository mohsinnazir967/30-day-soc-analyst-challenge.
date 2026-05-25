# Day 20 — Setting Up Mythic C2 Instance

**Week:** 3 | **Topic:** Adversary Simulation Lab Setup
**Original file:** `Day 20 Setting Up Mythic C2 Instance.md`

---

## 📋 Overview
Deploying the Mythic C2 framework on a separate Vultr server to simulate attacker infrastructure for the lab attack simulation.

## 🎯 Key Steps
- Deploy a new Ubuntu server on Vultr for the Mythic C2 instance
- Clone the Mythic repository from GitHub
- Install Mythic using `./mythic-cli install`
- Start Mythic services and access the Mythic web UI
- Configure a C2 profile (HTTP listener)
- Generate a Mythic agent payload (Apollo agent)
- Verify the Mythic server is ready to receive beacons

## ⚠️ Lab Context
> Mythic C2 is deployed in an isolated cloud lab environment for educational purposes. The simulated attack targets only machines within this private lab.

## 📝 Notes
> Refer to the original day file for full installation screenshots and commands.

*← [Back to Week 3](.) | [Back to README](../../README.md)*
