# Day 07: Setting Up Fleet Server and Installing Elastic Agent on Windows

**Week:** 1 | **Phase:** Agent Deployment
**← [Back to README](../../README.md) | [← Day 06](./day-06-fleet-server-elastic-agent.md)**

---

## 1. Introduction

**Goal:** Set up Fleet Server for centralized management and install Elastic Agent on the Windows Server.

---

## 2. Create Fleet Server VM

- Click on **Deploy** > **Deploy New Server**.
- Select **Singapore** and **Ubuntu 22.04** (1 CPU, 4 GB RAM).
- Disable auto backups and IPv6.
- Select **Virtual Private Cloud** — ensure network is selected (IP: `172.31.0.4`).
- Name the server `Challenge-Fleet-Server`.
- Click **Deploy**.

---

## 3. Access Web GUI

1. Go to `Challenge-ELK` public IP address on port `5601`.
2. Select hamburger icon > **Fleet** under **Management**.
3. Click **Add Fleet Server** > Choose **Quick Start**.
4. Name the server `Challenge-Fleet-Server`.
5. Enter the public IP of `Challenge-Fleet-Server` (e.g., `155.138.1.155`) with port `8220`.
6. Ensure URL is in HTTPS format.
7. Click **Generate Fleet Server Policy**.

> 📖 For advanced setup: [Home Lab — Ingesting Data with Agent and Fleet](https://www.leveleffect.com/blog/home-lab-ingesting-data-with-agent-and-fleet)

---

## 4. Install Fleet Server

1. Copy the generated token and configuration.
2. Access the Fleet server via SSH.
3. Update repositories: `apt-get update` and `apt-get upgrade -y`.
4. Paste the copied configuration to install Elastic Agent.
5. Ensure connection to Elasticsearch (port `9200`).
6. Allow `Challenge-WIN-Haji` to communicate with `Challenge-ELK`. Update the `SOC Simulation` firewall to allow `TCP` port `1-65535` from `Challenge-Fleet-Server` public IP.
7. Allow port 9200 on `Challenge-ELK`:

```bash
sudo ufw allow 9200
```

---

## 5. Troubleshooting

**Firewall Rules:**

1. Modify firewall rules to allow Fleet Server to access Elasticsearch.
2. Use `ufw allow 9200` on the ELK server.
3. Ensure Fleet Server can communicate with ELK Server.

---

## 6. Enroll Elastic Agent

1. Confirm Fleet Server connection.
2. Click **Continue Enrolling Elastic Agent**.
3. Create a policy (e.g., `Challenge Windows Policy`).
4. Select **Windows** as the host type.
5. Copy the installation command.

---

## 7. Install Agent on Windows Server

1. Access Windows Server via console.
2. Open PowerShell as Administrator.
3. Paste and run the installation command.
4. Ensure the agent downloads and installs successfully.

---

## 8. Additional Troubleshooting

1. Check network connections and firewall settings.
2. Allow port 8220 on the Fleet server: `ufw allow 8220`
3. Allow port 443 on the Fleet server: `ufw allow 443`
4. Modify Fleet server settings in the Elastic web GUI to use port `8220`.
5. Use `--insecure` flag to bypass self-signed certificate error.
6. Allow `Challenge-WIN-Haji` to communicate with `Challenge-ELK` on port `9200` by adding a rule in the `SOC Simulation` Firewall.

---

## 9. Verify Enrollment

1. Check the Elastic web GUI for the enrolled Windows server.
2. Go to **Discover** and search for logs from the Windows server.
3. Verify logs are being captured (e.g., event code `4625` for failed logon attempts).

---

*→ Next: [Day 08 — Understanding Sysmon](./day-08-understanding-sysmon.md)*
