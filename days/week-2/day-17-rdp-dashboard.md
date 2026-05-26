# Day 17: Creating a Dashboard for RDP Activity

**Week:** 2 | **Phase:** Threat Visualisation
**← [Back to README](../../README.md) | [← Day 16](./day-16-rdp-ssh-rules.md)**

---

## 1. Introduction

**Goal:** Create a dashboard focusing on RDP activity from the Windows server and table visualization.

**Task:** Create a map similar to the SSH activity map, focusing on Windows Server authentication attempts related to RDP, and create table visualization.

---

## 2. Steps to Create the Dashboard

**Navigate to Elastic web GUI** — Click on the hamburger icon and select **Maps**.

**Query Setup** — Use the saved search query for event code `4625` (failed logins) and agent name:

```
event.code:4625 AND agent.name:"Challenge-WIN-Haji"
```

**Add Layer** — Click on Add Layer, select Choropleth, and choose World Countries for the EMS boundary.

**Data View** — Select data view and join field `source.geo.country_iso_code`.

**Save Map** — Title it `RDP Failed Authentication`.

**Add to Dashboard** — Select the existing dashboard `Challenge Authentication Activity`.

---

## 3. Creating a Query for Successful Authentications

**Event Code** — Change from `4625` to `4624` for successful logins. Focus on logon types `10` and `7`:

```
event.code:4624 and (winlog.event_data.LogonType:10 or winlog.event_data.LogonType:"7") and agent.name:"Challenge-WIN-Haji"
```

**Save and Add to Dashboard:**
- Save the query: `Challenge-RDP Successful Authentication Activity`.
- Duplicate the existing dashboard, update the query, and name the new map `Challenge-RDP Successful Authentication Activity`.

---

## 4. Adding a Table

**Fields to Include:** Time, source IP, username, and country.

**Use Queries** — Use saved search queries for both failed and successful activities.

**Add Table to Dashboard** — Include the table with usernames, source IPs, and country names for quick reference.

---

## 5. Creating Table Visualizations

### 5.1 SSH Failed Activity Table

**Create Visualization** — Click on Create Visualization and select Table.

**Query:**
```
system.auth.ssh.event : * and agent.name:"Challenge-Linux-Steve" and system.auth.ssh.event : "Failed"
```

**Add Fields:** timestamp, source IP, username, and country name.

**Configure Rows:** Set top values to 10 and uncheck "group remaining values as other".

**Sort Records:** Sort by count of records in descending order.

**Save:** `Challenge-SSH Failed Authentication Activity (Table)`

---

### 5.2 SSH Successful Activity Table

Duplicate the SSH failed activity table.

**Update Title:** `Challenge-SSH Successful Authentication Activity (Table)`

**Modified Query:**
```
system.auth.ssh.event : * and agent.name:"Challenge-Linux-Steve" and system.auth.ssh.event : "Accepted"
```

---

### 5.3 RDP Failed Activity Table

Duplicate the SSH failed activity table.

**Update Title:** `Challenge-RDP Failed Authentication Activity (Table)`

**Modified Query:**
```
event.code:4625 AND agent.name:"Challenge-WIN-Haji"
```

---

### 5.4 RDP Successful Activity Table

Duplicate the RDP failed activity table.

**Update Title:** `Challenge-RDP Successful Authentications Activity (Table)`

**Modified Query:**
```
event.code:4624 and (winlog.event_data.LogonType:10 or winlog.event_data.LogonType:"7") and agent.name:"Challenge-WIN-Haji"
```

---

## 6. Finalizing the Dashboard

**Review and Save** — Ensure all visualizations are correctly configured and save the dashboard.

**Summary** — The dashboard now includes visualizations for both SSH and RDP failed and successful authentications.

---

*→ Next: [Day 18 — C2 Theory](../week-3/day-18-c2-theory.md)*
