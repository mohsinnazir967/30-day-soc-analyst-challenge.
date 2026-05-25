# Day 09 — Installing and Configuring Sysmon

**Week:** 1 | **Topic:** Endpoint Monitoring Setup
**Original file:** `Day 09 Installing and Configuring Sysmon.md`

---

## 📋 Overview
Hands-on installation of Sysmon on the Windows Server using the Olaf Hartong community config, and verifying logs appear in Event Viewer.

## 🎯 Key Steps
- Download Sysmon from Microsoft Sysinternals
- Download the Olaf Hartong Sysmon modular config
- Install Sysmon: `sysmon64.exe -accepteula -i sysmonconfig.xml`
- Verify Sysmon service is running: `Get-Service sysmon64`
- Confirm events in Event Viewer under: `Applications and Services Logs → Microsoft → Windows → Sysmon → Operational`
- Verify Event ID 1 (Process Create) is being generated

## 📝 Notes
> Refer to the original day file for full screenshots and commands.

*← [Back to Week 1](.) | [Back to README](../../README.md)*
