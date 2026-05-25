# Day 25 — Integrating osTicket into Your Tech Stack

**Week:** 4 | **Topic:** SIEM-Ticketing Integration
**Original file:** `Day 25 Integrating OS Ticket into Your Tech Stack.md`

---

## 📋 Overview
Connecting Kibana alerts to osTicket so that when a detection rule fires, a ticket is automatically created in the ticketing system — simulating a real SOC alert pipeline.

## 🎯 Key Steps
- Configure Kibana alert actions to POST to osTicket API
- Set up osTicket API key for Kibana integration
- Map Kibana alert fields to osTicket ticket fields (subject, priority, description)
- Test the integration by triggering a brute force detection rule
- Verify tickets are automatically created in osTicket
- Practice working the ticket: acknowledge → investigate → resolve

## 🔄 Integrated Alert Flow
```
Kibana Alert Fires
      │
      ▼
osTicket API
      │
      ▼
Ticket Created (SSH Brute Force — High Priority)
      │
      ▼
SOC Analyst Assigned → Investigation → Resolution
```

## 📝 Notes
> Refer to the original day file for full integration configuration screenshots.

*← [Back to Week 4](.) | [Back to README](../../README.md)*
