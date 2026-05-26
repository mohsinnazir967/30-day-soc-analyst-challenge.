# Day 08: Understanding and Using Sysmon

**Week:** 1 | **Phase:** Endpoint Monitoring Theory
**← [Back to README](../../README.md) | [← Day 07](./day-07-fleet-server-setup.md)**

---

## 1. Introduction

**Goal:** Learn about Sysmon and its capabilities.

---

## 2. Importance of Endpoint Visibility

- **Visibility:** Crucial for investigating potential compromises.
- **Default Logging:** Enabled by default on Windows but insufficient.
- **Solution:** Configure auditing settings or install Sysmon.

---

## 3. What is Sysmon?

- **Tool:** Free Microsoft tool, part of the Sysinternals suite.
- **Telemetry:** Monitors events like process creations, network connections, file creations.
- **Customization:** Uses a configuration file to control logged events.
- **Version:** Latest version is 15.15 with 30 event IDs.

---

## 4. Sysmon Capabilities

- **Process Creations:** Logs command lines for parent and current processes.
- **Hashes:** Records process hashes for additional context.
- **Process GUID:** Correlates events for a bigger picture.
- **Network Connections:** Logs source and destination IPs, ports, and involved processes *(disabled by default)*.

---

## 5. Important Event IDs

| Event ID | Description | Notes |
|----------|-------------|-------|
| **1** | Process Creation | Tracks new processes and command lines. Logs file hashes for additional context. |
| **3** | Network Connections | Disabled by default — must be enabled via config file. Tracks network connections, source/destination IPs, ports. |
| **6** | Driver Loaded | Identifies potential defense evasion techniques. |
| **7** | Image Load | Disabled by default. Used for detecting process injection. |
| **8** | Create Remote Thread | Identifies process injection techniques. |
| **10** | Process Access | Common for detecting credential access attempts on LSASS. |
| **22** | DNS Query | Tracks domain requests — useful for identifying compromised endpoints. |

📖 [Read More About Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

---

*→ Next: [Day 09 — Installing Sysmon](./day-09-installing-sysmon.md)*
