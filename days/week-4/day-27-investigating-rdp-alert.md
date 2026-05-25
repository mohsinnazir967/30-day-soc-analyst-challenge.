# Day 27 — Investigating an RDP Brute Force Alert

**Week:** 4 | **Topic:** Incident Investigation
**Original file:** `Day 27 Investigating an RDP Brute Force Alert.md`

---

## 📋 Overview
End-to-end investigation of an RDP brute force alert — applying the same IR methodology as Day 26 to a Windows-specific attack scenario.

## 🎯 Investigation Steps

### 1. Alert Triage
- Review RDP alert in Kibana Security
- Note: source IP, targeted account, Event ID 4625 count, timeframe

### 2. Log Analysis
- Query Windows Security logs: Event ID 4625 (failed) and 4624 (success)
- Check Logon Type: Type 10 = RemoteInteractive (RDP)
- Identify if a successful RDP login followed the brute force

### 3. Threat Intelligence
- Submit attacker IP to VirusTotal and AbuseIPDB
- Assess whether IP is a known scanner or targeted threat actor

### 4. Containment Decision
- Successful login: isolate machine, reset credentials, review what attacker accessed
- Failed only: block IP at firewall, document

### 5. Ticket Resolution
- Update osTicket with full investigation findings
- Classify: True Positive / False Positive
- Close with remediation actions taken

## 📝 Notes
> Refer to the original day file for full investigation walkthrough and screenshots.

*← [Back to Week 4](.) | [Back to README](../../README.md)*
