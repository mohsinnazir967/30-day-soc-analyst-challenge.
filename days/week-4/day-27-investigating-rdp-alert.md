# Day 27: Investigating an RDP Brute Force Alert

**Week:** 4 | **Phase:** Incident Investigation
**← [Back to README](../../README.md) | [← Day 26](./day-26-investigating-ssh-alert.md)**

---

## 1. Introduction

**Goal:** Learn how to investigate an RDP Brute Force alert and identify key indicators.

---

## 2. Accessing Alerts

1. Click on the hamburger icon and select `Alerts` under the security tab.
2. Filter for RDP Brute Force alerts and select the first one for investigation.
3. Expand the alert by clicking on `View Details`.
4. Review the description and details, including the source IP and targeted username.

---

## 3. Investigative Methodology

### Question 1: Is the IP Known for Brute Force Activity?

- Use tools like **AbuseIPDB** and **GreyNoise** to check the reputation of the IP address.
- *Example: An IP reported 55 times with 48% confidence of abuse is suspicious.*

### Question 2: Were Any Other Users Affected by This IP?

- Search for the IP address in Kibana's Discover tab.
- Check for distinct users targeted by the IP.
- *Example: Only the administrator account was targeted.*

### Question 3: Were Any Logins Successful?

- Search for successful login attempts using event code `4624`.
- Ensure correct query syntax.
- *Example: No successful logins found for the IP address.*

### Question 4: What Activity Occurred After Successful Logins?

- If there were successful logins, investigate subsequent activities.
- Look for signs of malicious behavior: downloading scripts, running discovery commands, or executing malicious files.

---

## 4. Example Investigation

1. **Check IP Reputation** — Use AbuseIPDB and GreyNoise. *Example: An IP reported 7 times with 25% confidence of abuse is suspicious.*
2. **Check for Affected Users** — Search for the IP address in Kibana Discover. *Example: Only the administrator account was targeted.*
3. **Check for Successful Logins** — Search using event code `4624`. *Example: Three successful logins found for the IP address.*

---

## 5. Investigating Post-Login Activity

1. **Determine Time Zone:**
   - Go to `Stack Management` → **Advanced Settings** under Kibana.
   - Set the time zone to UTC for consistency.

2. **Identify Logon ID:**
   - Expand the event details and find the target `logon ID`.
   - Use the `logon ID` to filter for all activities during the session.

3. **Analyze Events:**
   - Check for special privileges assigned to the new logon.
   - Investigate subsequent events like logoff times and any automated sessions.

4. **Document Findings:**
   - Note the start and end times of the compromise.
   - Investigate activities within the time frame: process creations, persistence mechanisms, lateral movements, exfiltration attempts, and command and control activities.

---

*→ Next: [Day 28 — Investigating Mythic C2](./day-28-investigating-mythic-c2.md)*
