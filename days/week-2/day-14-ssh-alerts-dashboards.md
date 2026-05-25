# Day 14 — Creating SSH Brute Force Alerts and Dashboards

**Week:** 2 | **Topic:** Detection Engineering
**Original file:** `Day 14 Creating SSH Brute Force Alerts and Dashboards.md`

---

## 📋 Overview
Building the first custom detection rule and Kibana dashboard for SSH brute force activity — the core SOC skill of turning raw logs into actionable alerts.

## 🎯 Key Steps
- Write a KQL query to detect SSH failed login spikes
- Create a threshold-based alert rule in Kibana Security
- Configure alert actions and severity levels
- Build a Kibana dashboard with: failed login count, top source IPs, geo map
- Test the alert by simulating brute force activity
- Verify alerts appear in Kibana Alerts queue

## 🔍 KQL Detection Query
```kql
event.dataset: "system.auth" and event.outcome: "failure" and event.action: "ssh_login"
```

## 📝 Notes
> Refer to the original day file for full rule configuration and dashboard screenshots.

*← [Back to Week 2](.) | [Back to README](../../README.md)*
