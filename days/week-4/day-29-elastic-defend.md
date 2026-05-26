# Day 29: Installing Elastic Defend

**Week:** 4 | **Phase:** Endpoint Detection & Response (EDR)
**← [Back to README](../../README.md) | [← Day 28](./day-28-investigating-mythic-c2.md)**

---

## 1. Introduction

**Goal:** Successfully install Elastic's EDR called Elastic Defend and view the telemetry it generates.

---

## 2. Installing Elastic Defend

1. Click on the `hamburger` icon and scroll down to `Integrations`.
2. Select `Elastic Defend` and click **Add Elastic Defend**.

**Configure Integration:**
- Name the integration: `Challenge EDR`.
- Choose the configuration type: `Complete EDR` for full telemetry.
- Select the target host: `Challenge-WIN-Haji` Server.
- Click **Save and Continue** → **Save and Deploy Changes**.

---

## 3. Verifying Installation

1. Go to `Security` → **Manage** → **Endpoints**.
2. Verify that the endpoint is running Elastic Defend.
3. *If using the 30-day trial, you can isolate the host remotely. Note: This feature is not available with the free subscription.*

---

## 4. Testing Elastic Defend

1. Open the console for the Windows server.
2. Terminate the `svrhost-haji.exe` process.
3. Attempt to run the executable again to see if Elastic Defend blocks it.
4. Verify that Elastic Defend generates a malware alert and quarantines the file.

---

## 5. Viewing Telemetry

1. Open a Discover tab and search for `malware`.
2. Set the time frame to the last 15 minutes and sort by timestamp.
3. Review alert details: file directory, quarantine path, file name, file owner, and file hash.
4. Check the **process tree** visualization to see the relationship between processes.

---

## 6. Configuring Response Actions

1. Go to `Detection Rules` and select the malware prevention alert rule.
2. Click on `Edit Rule Settings` and add a response action (e.g., **isolate host**).
3. Generate a new malware alert and verify that the response action (host isolation) is triggered.

---

## 7. Elastic Defend vs Sysmon Comparison

| Feature | Sysmon | Elastic Defend |
|---------|--------|---------------|
| Log Collection | ✅ | ✅ |
| Threat Detection | ❌ | ✅ |
| Active Prevention | ❌ | ✅ |
| Managed via Fleet | ❌ | ✅ |
| Cost | Free | Free (basic) |

---

*→ Next: [Day 30 — Troubleshooting & Finalising](./day-30-troubleshooting-and-finalising.md)*
