# Day 16: Creating RDP & SSH Brute Force Rules

**Week:** 2 | **Phase:** Detection Engineering
**← [Back to README](../../README.md) | [← Day 15](./day-15-rdp-abuse.md)**

---

## 1. Introduction

**Goal:** Review authentication logs from the Windows server and create a Brute Force alert.

---

## 2. Query Logs for RDP Brute Force Activity

1. Log into Elasticsearch and click on the hamburger icon > **Discover**.
2. Set the time frame to "Today".
3. Filter for the Windows server by clicking on the agent name (e.g., `Challenge-WIN-Haji`).

---

## 3. Identify Key Fields

**Fields to Track:**
1. **Failed Attempts:** Look for failed authentication attempts (Event ID `4625`).
2. **User:** Identify the user attempting to log in.
3. **Source IP:** Determine the source IP of the authentication attempts.

---

## 4. Filter for Failed Attempts

1. Search for Event ID `4625` in the logs.
2. Confirm the field name is `event.code`.
3. Add `source.ip` and `user.name` fields to the table.
4. Verify the data by expanding the first event and checking the message.

---

## 5. Save the Query

Save the query as `Challenge RDP failed activity`.

---

## 6. Create Alert

1. Click on the **Alerts** tab and select **Create Search Threshold Rule**.
2. Name the alert: `Challenge Failed RDP alert`.
3. Set the threshold (e.g., greater than 5 failed attempts within 5 minutes).
4. Test the query to ensure it matches documents.
5. Save the rule.

---

## 7. Create Detailed Detection Rule for RDP

1. Click on **Rules** and select **Create New Rule**.
2. Choose **Threshold** as the rule type.
3. Use the custom query:

```
event.code:4625 AND agent.name:"Challenge-WIN-Haji" and user.name:"Administrator"
```

4. In the `Group by` add `user.name` and `source.ip` fields.
5. For the required field also add `user.name` and `source.ip`.
6. Name the rule: `Challenge-RDP-Brute-Force-Attempt-Haji`.
7. Set the severity to medium and configure advanced settings if needed.
8. Schedule the rule to run every 5 minutes.
9. Create and enable the rule.

---

## 8. Create Detailed Detection Rule for SSH

1. Click on **Rules** and select **Create New Rule**.
2. Choose **Threshold** as the rule type.
3. Use the custom query:

```
system.auth.ssh.event : * and agent.name:"Challenge-Linux-Steve" and system.auth.ssh.event : "Failed" AND user.name:"root"
```

4. In the `Group by` add `user.name` and `source.ip` fields.
5. For the required field also add `user.name` and `source.ip`.
6. Name the rule: `Challenge-SSH-Brute-Force-Attempt-Steve`.
7. Set the severity to medium and configure advanced settings if needed.
8. Schedule the rule to run every 5 minutes.
9. Create and enable the rule.

---

## 9. Test the Rules

1. Perform a brute force attack to generate alerts.
2. Check the alerts for detailed information such as username and source IP.

---

*→ Next: [Day 17 — RDP Dashboard](./day-17-rdp-dashboard.md)*
