# Day 10 — Ingesting Sysmon and Microsoft Defender Logs into Elasticsearch

**Week:** 1 | **Topic:** Log Ingestion
**Original file:** `Day 10 Ingesting Sysmon and Microsoft Defender Logs into Elasticsearch.md`

---

## 📋 Overview
Configuring the Elastic Agent policy to collect Sysmon and Microsoft Defender logs from the Windows endpoint and verifying they appear in Kibana Discover.

## 🎯 Key Steps
- Add Windows integration to the Elastic Agent policy in Fleet
- Configure Sysmon log collection: `Microsoft-Windows-Sysmon/Operational`
- Configure Microsoft Defender log collection: `Microsoft-Windows-Windows Defender/Operational`
- Assign the updated policy to the Windows Agent
- Verify log ingestion in Kibana → Discover
- Run a basic KQL query for Sysmon: `event.provider: "Microsoft-Windows-Sysmon"`

## 📝 Notes
> Refer to the original day file for full screenshots and configuration steps.

*← [Back to Week 1](.) | [Back to README](../../README.md)*
