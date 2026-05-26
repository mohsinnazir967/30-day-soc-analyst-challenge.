# Day 30: Troubleshooting and Finalizing Setup

**Week:** 4 | **Phase:** Lab Review & Completion
**← [Back to README](../../README.md) | [← Day 29](./day-29-elastic-defend.md)**

---

## 1. Introduction

**Goal:** Troubleshoot and finalize the setup of your environment, ensuring all components are fully functional.

---

## 2. Troubleshooting Connection Issues

1. **Check Firewall Rules** — Ensure the firewall rules on your Vultr instance allow the necessary ports. *Example: Allow port range `1-65535` from your public IP address.*
2. **Modify Firewall on Virtual Machine** — Use `ufw` to allow specific ports. *Example: `ufw allow 5601` for Kibana.*
3. **Verify System Services:**

```bash
systemctl status kibana.service
systemctl status elasticsearch.service
```

---

## 3. Configuring Fleet Server

1. Ensure the firewall rules allow ports for the Fleet server:

```bash
ufw allow 8220
ufw allow 443
```

2. Go to **Fleet settings** in the Elastic web GUI.
3. Change the port from `443` to `8220` and save the settings.

---

## 4. Enrolling Elastic Agent

1. Navigate to the Elastic Agent directory and run the install command:

```bash
sudo ./elastic-agent install
```

2. **Troubleshoot Enrollment Issues:**
   - Check for network connection issues.
   - Ensure the Fleet server is accessible and the necessary ports are open.
   - Use `--insecure` flag to bypass certificate errors if using a self-signed certificate.

---

## 5. Finalizing Setup

1. **Verify Enrollment** — Ensure the Elastic Agent is successfully enrolled and connected to the Fleet server.
2. **Test Connectivity:**

```bash
ping <Fleet_Server_IP>
```

3. **Check for Errors** — Review any error messages. *Example: Connection refused errors may indicate firewall or port issues.*

---

## 6. Configuring phpMyAdmin

1. Go to phpMyAdmin → **User Accounts**.
2. Modify the root account to use the public IP address.
3. Set the password to `Winter2024!`.
4. Update `config.inc.php` to use the public IP address and the new password.
5. Save the changes and reconnect to phpMyAdmin.

---

## 7. Creating Database for osTicket

1. Go to phpMyAdmin and click **New**.
2. Name the database `Challenge-30day-db` and click **Create**.
3. Go to **User Accounts** and ensure the root account has privileges to access the new database.
4. Navigate to the osTicket setup page and enter the database details to complete the installation.

---

## 8. Troubleshooting Webhook Errors

1. **Check Network Connection** — Ensure the ELK server can communicate with the osTicket server. *Example: Ping the osTicket server from the ELK server.*
2. **Update Configuration** — Change the osTicket configuration to use the private IP address. Save the changes and rerun the test.

---

## 9. Final Lab Checklist

- ✅ ELK Stack running and accessible
- ✅ Windows Server enrolled in Fleet with Sysmon and Defender logs ingested
- ✅ Ubuntu SSH Server enrolled with auth logs ingested
- ✅ Brute force detection rules active for SSH and RDP
- ✅ Mythic C2 detection rules and dashboards active
- ✅ osTicket integrated with Kibana alert actions
- ✅ Elastic Defend deployed on Windows endpoint
- ✅ All dashboards built, named, and saved

---

## 🎉 Challenge Complete!

30 days of hands-on SOC work — from zero to a fully functional cloud SIEM environment with detection rules, dashboards, EDR, and an integrated ticketing workflow.

---

*← [Back to README](../../README.md)*
