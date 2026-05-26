# Day 13: Installing Elastic Agent on SSH Server

**Week:** 2 | **Phase:** Log Ingestion
**← [Back to README](../../README.md) | [← Day 12](./day-12-ssh-server-setup.md)**

---

## 1. Introduction

**Goal:** Install Elastic Agent on the SSH server to query logs in Elasticsearch.

---

## 2. Create Agent Policy

1. Log into Elasticsearch web GUI.
2. Click on the hamburger icon > **Fleet** under **Management**.
3. Click on **Agent Policy** > **Create Agent Policy**.
4. Name the policy: `Challenge-Linux-Policy`.
5. Click **Create Agent Policy**.

---

## 3. Configure Policy

1. Select the system integration (e.g., `system-3`).
2. Verify the log paths (e.g., `/var/log/auth*` for Ubuntu).
3. Confirm the policy covers Debian, Ubuntu, Red Hat, and CentOS (`/var/log/secure*`).

---

## 4. Enroll Agent

1. Click on **View All Agent Policies** > **Agents**.
2. Click on **Add Agent**.
3. Select the policy created: `Challenge-Linux-Policy`.
4. Choose **Enroll in Fleet** and select **Linux tar**.
5. Edit the `SOC Simulation` Firewall to add a rule that allows `Challenge-Linux-Steve` to communicate with `Challenge-ELK` on port `9200`.
6. Copy the command and run it in the SSH session on `Challenge-Linux-Steve`.
7. Add `--insecure` flag if using a self-signed certificate.

---

## 5. Verify Installation

1. Confirm agent enrollment and incoming data in Elasticsearch.
2. Click on the hamburger icon > **Discover**.
3. Filter by agent name to view logs from the SSH server.
4. Search for specific events (e.g., authentication failures).

---

## 6. Analyze Logs

Use the `grep` command to filter logs for failed authentication attempts:

```bash
grep -i failed auth.log | grep -i root | cut -d ' ' -f 11
```

Add relevant fields to the table in Elasticsearch for easier analysis.

---

*→ Next: [Day 14 — SSH Brute Force Alerts & Dashboards](./day-14-ssh-alerts-dashboards.md)*
