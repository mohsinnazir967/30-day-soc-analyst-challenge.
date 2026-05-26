# Day 11: Understanding and Defending Against Brute Force Attacks

**Week:** 2 | **Phase:** Threat Detection Theory
**← [Back to README](../../README.md) | [← Day 10](../week-1/day-10-ingesting-sysmon-defender-logs.md)**

---

## 1. Introduction

**Goal:** Learn about Brute Force attacks, common tools used, and protection methods.

---

## 2. What is a Brute Force Attack?

- **Definition:** An attacker tries every password combination to compromise an account.
- **Example:** Trying every combination on a luggage keypad lock.
- **Prevalence:** Common due to ease of use and accessibility.

---

## 3. Common Types of Brute Force Attacks

**Simple Brute Force Attack:**
- Tries every combination starting from 0000.
- Automated attempts to gain unauthorized access.

**Dictionary Attack:**
- Uses a word list containing common words, phrases, and passwords from credential dumps.
- Higher success rate due to repeated passwords.

**Credential Stuffing:**
- Uses credential dumps to try every username and password combination.
- Commonly seen in honeypots.

---

## 4. Protecting Against Brute Force Attacks

**Long Passwords/Passphrases:**
- Use 15+ character passwords or passphrases.
- Include uppercase letters, numbers, and special characters.
- Use a password manager to generate and store passwords.

**Multifactor Authentication (MFA):**
- Adds an additional layer of security.
- Prompts for an additional authentication method (SMS, email, authenticator).
- Recommended to use an authenticator over SMS or email.

**Vigilance** *(the action or state of keeping careful watch for possible danger or difficulties)*:
- Adopt a mindset of questioning and high alert.
- Verify the source and purpose of emails asking for login.
- Sign up for alerts on [haveibeenpwned.com](https://haveibeenpwned.com) to check if your email was compromised.

---

## 5. Additional Protection Measures

**Check Attack Surface:**
- Identify publicly available assets and services (e.g., SSH, RDP).
- Disable unnecessary services or place them behind a firewall.

---

## 6. Common Tools Used in Brute Force Attacks

- **Hydra**
- **Hashcat**
- **John the Ripper**

> ⚠️ **Note:** Use these tools ethically — only on machines you own or have explicit permission to test.

---

*→ Next: [Day 12 — SSH Server Setup](./day-12-ssh-server-setup.md)*
