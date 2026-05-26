# Day 28: Investigating Mythic C2 Framework

**Week:** 4 | **Phase:** Advanced Incident Investigation
**← [Back to README](../../README.md) | [← Day 27](./day-27-investigating-rdp-alert.md)**

---

## 1. Introduction

**Goal:** Learn how to investigate a common C2 framework called Mythic and identify key indicators.

---

## 2. Accessing Events

1. Click on the hamburger icon and select **Discover**.
2. Set the time frame to 30 days.
3. Search for the Mythic C2 agent executable (e.g., `servicehost-haji.exe`).
4. Sort the events from old to new to follow the chain of events.

---

## 3. Identifying C2 Activity

**Methods:**

1. **Network Telemetry** — Look for back-and-forth traffic indicating a C2 session. Check for high byte transfers and top talkers.
2. **Heartbeat Detection** — Use tools like Rita from Black Hills Security to detect potential C2 traffic.
3. **Process and Network Creations** — Use `Sysmon event ID 3` for network creations. Couple process creations with network connections to identify suspicious activity.

---

## 4. Using Dashboards

1. Click on the hamburger icon and select `Dashboards` under analytics.
2. Select the `Challenge Suspicious Activity` dashboard.
3. Set the time range to 30 days.

**Analyze Panels:**

| Panel | What to Look For |
|-------|-----------------|
| Process Creations | Suspicious processes like PowerShell, CMD, and rundll32 |
| Network Connections | Processes initiating connections from unusual directories (e.g., `C:\Users\Public\Downloads`) |

---

## 5. Example Investigation

1. **Identify Suspicious Event** — Find a suspicious outbound connection, such as PowerShell calling out to an external IP address.
2. **Build Timeline:**
   - Copy the `destination IP address` and search for related events.
   - Create a timeline of network connections to the IP address.
3. **Correlate Events:**
   - Use the `process GUID` to correlate all events generated from the PowerShell session.
   - Sort events from old to new and follow the chain of events.
4. **Document Findings:**
   - Note the timestamps and details of file creations, network connections, and other activities.
   - *Example: A file named `servicehost-haji.exe` was created using PowerShell.*

---

## 6. Investigating Further

1. **Search for Process GUID** — Use the process GUID of the executable to search for related events.
2. **Analyze Process ID** — Check for `process ID` and any spawned processes. *Example: Process ID 6496 and parent process ID.*
3. **Search for Known Files** — Search for specific files like `passwords.txt` to identify related events. Look for file creation and access events.

---

*→ Next: [Day 29 — Elastic Defend](./day-29-elastic-defend.md)*
