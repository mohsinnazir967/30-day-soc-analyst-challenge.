# Day 28 — Investigating a Mythic C2 Alert

**Week:** 4 | **Topic:** Advanced Incident Investigation
**Original file:** `Day 28 Investigating Mythic C2 Framework.md`

---

## 📋 Overview
The most complex investigation of the challenge — investigating the Mythic C2 alert generated during Week 3, tracing the full attack chain from initial access through C2 establishment.

## 🎯 Investigation Steps

### 1. Alert Triage
- Review C2 detection alert in Kibana
- Identify: affected host, suspicious process, outbound connection details

### 2. Process Investigation
- Query Sysmon Event ID 1 for the suspicious process creation
- Trace parent-child process relationships
- Identify how the C2 agent was delivered and executed

### 3. Network Investigation
- Query Sysmon Event ID 3 for outbound connections
- Identify the C2 IP, port, and communication pattern
- Check connection frequency for beaconing behaviour

### 4. Timeline Reconstruction
- Build a full attack timeline from initial access to C2 establishment
- Map each event to a MITRE ATT&CK technique

### 5. Containment & Remediation
- Isolate the compromised machine
- Kill the C2 process
- Block the C2 IP at the firewall
- Reset all credentials on the affected machine

### 6. Ticket Resolution
- Document full investigation in osTicket
- Include IOCs, timeline, and remediation steps taken

## 📝 Notes
> Refer to the original day file for full investigation walkthrough and screenshots.

*← [Back to Week 4](.) | [Back to README](../../README.md)*
