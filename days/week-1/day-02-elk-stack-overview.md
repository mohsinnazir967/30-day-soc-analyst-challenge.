# Day 02 — ELK Stack: Elasticsearch, Logstash and Kibana

**Week:** 1 | **Topic:** SIEM Theory
**Original file:** `Day 02 ELK Stack – Elasticsearch Logstash and Kibana.md`

---

## 📋 Overview

Deep dive into the ELK Stack — what each component does, how they work together, and why it is one of the most widely used open-source SIEM platforms in the industry.

---

## 🎯 Key Concepts

### Elasticsearch
- Distributed search and analytics engine
- Stores all ingested log data in JSON format
- Queried using REST API or Kibana Query Language (KQL)
- Scales horizontally across nodes in a cluster

### Logstash
- Data processing pipeline: **Ingest → Filter → Output**
- Accepts data from multiple input sources (Beats, Syslog, HTTP)
- Transforms/enriches data using filter plugins (grok, mutate)
- Outputs processed data to Elasticsearch

### Kibana
- Web-based UI for Elasticsearch
- Used for: dashboards, visualisations, alert rules, and investigations
- Key sections for SOC work: **Discover**, **Alerts**, **Dashboards**, **SIEM**

### Elastic Agent / Beats
- Lightweight data shippers installed on endpoints
- Elastic Agent replaces individual Beats with a single unified agent
- Managed centrally via **Fleet Server**

---

## 🔄 Data Flow

```
Endpoint (Sysmon / Windows Event Logs)
    │
    ▼
Elastic Agent
    │
    ▼
Fleet Server → Elasticsearch → Kibana (SIEM UI)
```

---

## 📝 Notes

- ELK is free and open-source (with paid Elastic Cloud option)
- In this lab we self-host the full stack on Vultr

---

*← [Back to Week 1](.) | [Back to README](../../README.md)*
