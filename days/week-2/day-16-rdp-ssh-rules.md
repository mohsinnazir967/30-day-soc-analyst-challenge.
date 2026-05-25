# Day 16 — Creating RDP and SSH Brute Force Detection Rules

**Week:** 2 | **Topic:** Detection Engineering
**Original file:** `Day 16 Creating RDP & SSH Brute Force Rules.md`

---

## 📋 Overview
Building threshold-based detection rules for both RDP and SSH brute force in Kibana Security — creating a comprehensive brute force detection capability.

## 🎯 Key Steps
- Create RDP failed login detection rule using Windows Event ID 4625 + Logon Type 3/10
- Set threshold: 5+ failed logins from same IP within 1 minute
- Create SSH failed login rule using `system.auth` dataset
- Configure alert severity, risk scores, and MITRE ATT&CK tagging (T1110)
- Test both rules by simulating brute force attempts
- Verify alerts fire correctly in the Kibana Alerts queue

## 🔍 KQL for RDP Detection
```kql
event.code: "4625" and winlog.event_data.LogonType: ("3" or "10")
```

## 📝 Notes
> Refer to the original day file for full rule configuration screenshots.

*← [Back to Week 2](.) | [Back to README](../../README.md)*
