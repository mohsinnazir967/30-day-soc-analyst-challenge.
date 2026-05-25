# Day 13 — Installing Elastic Agent on SSH Server

**Week:** 2 | **Topic:** Log Ingestion
**Original file:** `Day 13 Installing Elastic Agent on SSH Server.md`

---

## 📋 Overview
Enrolling the Ubuntu SSH server into Fleet and configuring it to ship authentication logs to Elasticsearch for SIEM analysis.

## 🎯 Key Steps
- Create a new Fleet Agent Policy for Linux endpoints
- Add the System integration to collect auth logs (`/var/log/auth.log`)
- Download and install Elastic Agent on the Ubuntu SSH server
- Enroll the agent using the Fleet enrollment token
- Verify the SSH server appears as healthy in Kibana Fleet
- Confirm auth logs appear in Kibana Discover

## 📝 Notes
> Refer to the original day file for full screenshots and commands.

*← [Back to Week 2](.) | [Back to README](../../README.md)*
