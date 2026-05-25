# Day 12 — Setting Up an SSH Server and Reviewing Authentication Logs

**Week:** 2 | **Topic:** Lab Expansion
**Original file:** `Day 12 Setting Up an SSH Server and Reviewing Authentication Logs.md`

---

## 📋 Overview
Deploying a new Ubuntu SSH server on Vultr exposed to the public internet to generate real-world brute force telemetry, and reviewing authentication log structure.

## 🎯 Key Steps
- Deploy Ubuntu 22.04 server on Vultr (public IP, port 22 open)
- Review `/var/log/auth.log` for incoming SSH authentication attempts
- Identify failed vs successful login patterns
- Understand sshd log format: timestamp, source IP, username, result
- Observe real-world brute force attempts hitting the public server within minutes of deployment

## 📝 Notes
> Refer to the original day file for full screenshots and log examples.

*← [Back to Week 2](.) | [Back to README](../../README.md)*
