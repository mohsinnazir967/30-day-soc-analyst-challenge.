# Day 15: Understanding and Protecting Against RDP Abuse

**Week:** 2 | **Phase:** Threat Detection Theory
**← [Back to README](../../README.md) | [← Day 14](./day-14-ssh-alerts-dashboards.md)**

---

## 1. Introduction

**Goal:** Learn about RDP, its uses, how attackers abuse it, and how to protect against it.

---

## 2. What is RDP?

- **Definition:** Remote Desktop Protocol (RDP) is used for communication between the terminal server and the terminal server client.
- **Port:** Default port is `3389`.
- **Usage:** Allows authorized users to connect remotely to another machine.

---

## 3. Why Use RDP?

**Benefits:**
- Remote connection to endpoints for work or troubleshooting.
- Saves commute time and increases accessibility and convenience.

---

## 4. How Attackers Abuse RDP

**Methods:**

1. **Exposed RDP Service:** Attackers connect to exposed RDP services and attempt to authenticate via brute force or valid credentials obtained through phishing.
2. **Credential Dumping:** Once inside, attackers gather valid credentials to move laterally within the network.
3. **Actions on Objectives:** Exfiltrate data, deploy ransomware, or both.

---

## 5. Finding Exposed RDP Services

**Tools:**

**Shodan:**
- Create an account on [shodan.io](https://shodan.io).
- Search for `port:3389` to find assets with RDP open.

**Censys:**
- Go to [censys.com](https://censys.com) and click **Search Now**.
- Search for `3389` to find remote access services.

---

## 6. Protecting Against RDP Abuse

1. **Disable Unnecessary RDP** — If RDP is not needed, disable it.
2. **Use VPN** — Place RDP behind a Virtual Private Network to restrict access.
3. **Use MFA** — Enable multifactor authentication for an additional layer of security.
4. **Restrict Access** — Implement firewall rules to allow access only from specific IP ranges.
5. **Use Strong Passwords** — Ensure passwords are at least 15 characters with uppercase, lowercase, numbers, and special characters.
6. **Avoid Default Accounts** — Disable default local accounts and create uniquely named administrator accounts.

---

*→ Next: [Day 16 — RDP & SSH Brute Force Rules](./day-16-rdp-ssh-rules.md)*
