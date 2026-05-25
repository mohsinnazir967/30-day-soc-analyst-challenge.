# Day 26 — Investigating an SSH Brute Force Alert

**Week:** 4 | **Topic:** Incident Investigation
**Original file:** `Day 26 Investigating an SSH Brute Force Alert.md`

---

## 📋 Overview
End-to-end investigation of a real SSH brute force alert — from alert triage in Kibana through to ticket resolution in osTicket using a structured IR methodology.

## 🎯 Investigation Steps

### 1. Alert Triage
- Review alert details in Kibana Security Alerts
- Identify: source IP, target username, number of attempts, timeframe

### 2. Log Analysis
- Query Kibana Discover for full auth log context
- Check if any failed attempts were followed by a successful login
- Identify the top attacking IPs and geolocate them

### 3. Threat Intelligence
- Submit attacker IP to VirusTotal
- Check if IP appears on threat intel feeds
- Determine: opportunistic scanner vs targeted attack

### 4. Containment
- If login was successful: isolate the affected host
- If failed only: document and monitor
- Update firewall rules to block attacker IP

### 5. Ticket Resolution
- Document findings in osTicket
- Set resolution: True Positive / False Positive / Benign
- Close ticket with full investigation notes

## 📝 Notes
> Refer to the original day file for full investigation walkthrough and screenshots.

*← [Back to Week 4](.) | [Back to README](../../README.md)*
