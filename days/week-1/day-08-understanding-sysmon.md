# Day 08 — Understanding and Using Sysmon

**Week:** 1 | **Topic:** Endpoint Monitoring Theory
**Original file:** `Day 08 Understanding and Using Sysmon.md`

---

## 📋 Overview
Theory and configuration deep-dive into Sysmon — Microsoft's free endpoint monitoring tool that provides rich telemetry on process creation, network connections, file creation, and more.

## 🎯 Key Concepts
- What Sysmon is and why it is essential for SOC detection
- Key Sysmon Event IDs used in threat detection:

| Event ID | Description |
|----------|-------------|
| 1 | Process Creation |
| 3 | Network Connection |
| 7 | Image Loaded |
| 11 | File Created |
| 12/13 | Registry Events |
| 22 | DNS Query |

- Sysmon configuration files and filtering rules
- SwiftOnSecurity vs Olaf Hartong config file comparison
- How Sysmon event logs appear in Elasticsearch

## 📝 Notes
> Refer to the original day file for full config examples and screenshots.

*← [Back to Week 1](.) | [Back to README](../../README.md)*
