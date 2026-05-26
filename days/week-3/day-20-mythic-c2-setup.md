# Day 20: Setting Up Mythic C2 Instance

**Week:** 3 | **Phase:** Adversary Simulation Lab Setup
**← [Back to README](../../README.md) | [← Day 19](./day-19-attack-diagram.md)**

---

## Introduction

This session covers setting up **Mythic C2**, a Command and Control (C2) framework.

Uses **Vultr Cloud Provider** for hosting the Mythic C2 instance.

**Kali Linux** is also installed for penetration testing.

---

## 1. Deploying a Server on Vultr

1. Login to Vultr and click **Deploy New Server**.
2. Select:
   - **Cloud Compute** (Shared CPU)
   - **Location:** Singapore
   - **OS:** Ubuntu (4GB RAM)
   - Disable **Auto Backups & IPv6**
   - Set **hostname:** `Challenge-Mythic`
3. Deploy the server.

---

## 2. Installing Kali Linux

1. Download Kali Linux from [kali.org](https://www.kali.org/).
2. Select **Virtual Machine** version (VMware used in this setup).
3. Extract the downloaded file using **7-Zip**.
4. Locate and open the **.vmx** file in VMware Workstation.
5. Power on the **Kali VM**.

---

## 3. Setting Up Mythic C2

**Access the Vultr Instance:**

```bash
ssh root@<challenge_mythic_server_ip>
```

**Update & Upgrade System:**

```bash
apt-get update && apt-get upgrade -y
```

**Install Dependencies:**

```bash
apt-get install docker-compose make -y
```

**Clone & Install Mythic:**

```bash
git clone https://github.com/its-a-feature/Mythic.git
cd Mythic
./install_docker_ubuntu.sh
```

**Start Mythic:**

```bash
make
./mythic-cli start
```

---

## 4. Fixing Docker Issues

If Docker fails to start, restart the service:

```bash
systemctl restart docker
systemctl status docker
```

---

## 5. Configuring Firewall

Create a Firewall Group `Challenge-Mythic-Firewall` on Vultr.

**Allow TCP Traffic from trusted IPs only:**
- TCP `1-65535` (Source: Personal IP)
- TCP `1-65535` (Source: `Challenge-WIN-Haji`)
- TCP `1-65535` (Source: `Challenge-Linux-Steve`)

Apply `Challenge-Mythic-Firewall` to the Mythic Server.

---

## 6. Accessing Mythic C2 Web Interface

Copy the server's public IP and navigate to:

```
https://<mythic-server_ip>:7443
```

**Login Credentials:**

Default username: `mythic_admin`

Password stored in the `.env` file:

```bash
cat .env
```

**Change Operation Name** — Default: `operation-cima` → Can be renamed (e.g., `operation-challenge`).

---

## 7. Mythic C2 Dashboard Overview

| Section | Description |
|---------|-------------|
| Callbacks | List of connected agents |
| Payloads | Preconfigured exploits |
| File Hosting | Upload/download files |
| Artifacts | Keylogging, screenshots, credentials, reports |
| MITRE ATT&CK Mapping | Identify attack techniques |
| Tags | Categorize targets |

---

*→ Next: [Day 21 — Brute Force Attack & C2 Session](./day-21-brute-force-c2-session.md)*
