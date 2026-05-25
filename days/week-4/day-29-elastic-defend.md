# Day 29 — Installing Elastic Defend

**Week:** 4 | **Topic:** Endpoint Detection & Response
**Original file:** `Day 29 Installing Elastic Defend.md`

---

## 📋 Overview
Installing Elastic Defend — Elastic's EDR (Endpoint Detection and Response) solution — on the Windows endpoint to add automated threat prevention alongside SIEM detection.

## 🎯 Key Steps
- Add the Elastic Defend integration to the Windows Agent policy in Fleet
- Configure Elastic Defend protection mode: Detection vs Prevention
- Deploy the updated policy to the Windows Elastic Agent
- Verify Elastic Defend is active in Kibana → Security → Endpoints
- Review Elastic Defend's built-in detection capabilities
- Compare SIEM detection (Sysmon) vs EDR prevention (Elastic Defend)

## 🔍 Elastic Defend vs Sysmon

| Feature | Sysmon | Elastic Defend |
|---------|--------|---------------|
| Log Collection | ✅ | ✅ |
| Threat Detection | ❌ | ✅ |
| Active Prevention | ❌ | ✅ |
| Managed via Fleet | ❌ | ✅ |
| Cost | Free | Free (basic) |

## 📝 Notes
> Refer to the original day file for full installation screenshots and configuration.

*← [Back to Week 4](.) | [Back to README](../../README.md)*
