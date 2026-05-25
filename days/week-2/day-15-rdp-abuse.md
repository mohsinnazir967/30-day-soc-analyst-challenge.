# Day 15 — Understanding and Protecting Against RDP Abuse

**Week:** 2 | **Topic:** Threat Detection Theory
**Original file:** `Day 15 Understanding and Protecting Against RDP Abuse.md`

---

## 📋 Overview
Deep dive into Remote Desktop Protocol (RDP) abuse techniques — one of the most common attack vectors for ransomware operators and nation-state actors.

## 🎯 Key Concepts
- What RDP is and why it is commonly exploited (port 3389)
- Attack types: brute force, credential stuffing, BlueKeep/DejaBlue (CVE exploits)
- Post-compromise RDP abuse: lateral movement and persistence
- Key Windows Event IDs for RDP detection:

| Event ID | Description |
|----------|-------------|
| 4625 | Failed logon (including RDP failures) |
| 4624 | Successful logon — check Logon Type 10 (RemoteInteractive) |
| 4778 | Session reconnected |
| 4779 | Session disconnected |

- Defensive controls: NLA enforcement, RDP Gateway, geo-blocking, MFA

## 📝 Notes
> Refer to the original day file for full explanations and examples.

*← [Back to Week 2](.) | [Back to README](../../README.md)*
