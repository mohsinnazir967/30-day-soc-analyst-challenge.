# Day 14: Creating SSH Brute Force Alerts and Dashboards

**Week:** 2 | **Phase:** Detection Engineering
**← [Back to README](../../README.md) | [← Day 13](./day-13-elastic-agent-ssh.md)**

---

## 1. Introduction

**Goal:** Create SSH Brute Force alerts and dashboards to visualize attack sources.

---

## 2. Query Logs for Brute Force Activity

1. Log into Elasticsearch and click on the hamburger icon > **Discover**.
2. Filter for the SSH server by clicking on `agent.name` (e.g., `Challenge-Linux-Steve`).
3. Set the time range to `Today` for initial analysis.

---

## 3. Identify Key Fields

**Fields to Track:**
1. **Failed Attempts:** Look for failed authentication attempts.
2. **User:** Identify the user attempting to log in.
3. **Source IP:** Determine the source IP of the authentication attempts.

---

## 4. Filter for Failed Attempts

1. Search for "failed" in the logs.
2. If no relevant data, explore available fields on the left.
3. Use `system.auth.ssh.event` field to filter for failed, invalid, and accepted attempts.
4. Add `system.auth.ssh.event` as a column.
5. Filter where `system.auth.ssh.event` exists to narrow down results.
6. Select `failed` from the table and then add it to the filter.

---

## 5. Add Relevant Fields

1. Add `user.name` field to track usernames.
2. Add `source.ip` field to track source IP addresses.
3. Optionally, add `geoip.country_name` to see the country of origin.

---

## 6. Save the Query

Save the query as `SSH failed activity`.

---

## 7. Create Alert

1. Click on the **Alerts** tab and select **Create Search Threshold Rule**.
2. Name the alert: `Challenge - SSH Brute Force Activity - Steve`.
3. The query is automatically populated based on the saved search.
4. Set the threshold (e.g., greater than 5 failed attempts within 5 minutes).
5. Test the query to ensure it matches documents.
6. Set the rule to check every 1 minute.
7. Save the rule.

---

## 8. Create Dashboard

1. Click on the hamburger icon > **Maps** under the **Analytics** tab.
2. Use the saved search query to filter data:

```
system.auth.ssh.event : * and agent.name:"Challenge-Linux-Steve" and system.auth.ssh.event : "Failed"
```

3. Add a layer to visualize geolocation based on source IP.
4. Select **Choropleth Layer** and choose **World Countries**.
5. Use the appropriate data view and join field: `source.geo.country_iso_code`.
6. Save the map as `Challenge-SSH Failed Authentication Activity` and add it to a new dashboard.
7. Save & Name the dashboard: `Challenge SSH Authentication Activity`.

---

## 9. Create Successful Authentication Dashboard

1. Duplicate the failed authentication dashboard.
2. Change the title to `Challenge-SSH Successful Authentication Activity`.
3. Adjust the query to filter for successful attempts:

```
system.auth.ssh.event : * and agent.name:"Challenge-Linux-Steve" and system.auth.ssh.event : "Accepted"
```

4. Save the updated dashboard.

---

*→ Next: [Day 15 — RDP Abuse Theory](./day-15-rdp-abuse.md)*
