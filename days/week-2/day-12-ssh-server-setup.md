# Day 12: Setting Up an SSH Server and Reviewing Authentication Logs

**Week:** 2 | **Phase:** Lab Expansion
**← [Back to README](../../README.md) | [← Day 11](./day-11-brute-force-theory.md)**

---

## 1. Introduction

**Goal:** Set up an SSH server in the cloud and review authentication logs in real time.

---

## 2. Set Up SSH Server

1. Go to [Vultr](https://www.vultr.com/) and sign in.
2. Click on **Deploy** > **Deploy New Server**.
3. Select **Cloud Compute** > **Shared CPU**.
4. Choose **Singapore** and **Ubuntu 24.04**.
5. Select **1 CPU and 1 GB of memory**.
6. Disable auto backups and IPv6.
7. Name the server `Challenge-Linux-Steve`.
8. Click on **Deploy Now**.

---

## 3. Access the Server

1. Wait for the server to be ready.
2. Open a PowerShell session.
3. SSH into the server:

```bash
ssh root@<IP_address>
```

4. Accept the connection and enter the password.

---

## 4. Update and Upgrade Repositories

```bash
apt-get update
apt-get upgrade -y
```

---

## 5. Review Authentication Logs

1. Navigate to the log directory: `cd /var/log`
2. List the logs: `ls`
3. View the authentication log: `cat auth.log`

---

## 6. Filter Authentication Logs

Filter for failed attempts:

```bash
grep -i failed auth.log
```

Filter for root user:

```bash
grep -i root auth.log
```

Extract IP addresses using cut command:

```bash
grep -i failed auth.log | grep -i root | cut -d ' ' -f 11
```

---

*→ Next: [Day 13 — Elastic Agent on SSH Server](./day-13-elastic-agent-ssh.md)*
