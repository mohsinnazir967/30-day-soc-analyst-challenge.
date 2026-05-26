# Day 03: Setting Up an Elasticsearch Instance

**Week:** 1 | **Phase:** ELK Setup
**← [Back to README](../../README.md) | [← Day 02](./day-02-elk-stack-overview.md)**

---

## 1. Creating a Virtual Private Cloud (VPC)

- Sign up on **[Vultr](https://www.vultr.com/)** (use $300 credit if available).
- Navigate to **Products > Network > VPC 2.0**.
- Click **"Add VPC"** and configure:
  - **Location**: Ensure all VMs are in the same location (e.g., Singapore).
  - **IPv4 Range**: Set `172.31.0.0/20`.
  - **Name**: Example: `SOC_Simulation`.
  - Click **"Add Network"**.

---

## 2. Deploying the Virtual Machine (VM)

- Click **"Deploy"** > **"Deploy New Server"**.
- **Location**: Same as VPC (e.g., Singapore).
- **Image**: **Ubuntu** (64-bit).
- **Server Size**: **4 vCPUs, 16GB RAM**.
- **VPC Selection**: Choose the `SOC_Simulation`.
- **Hostname**: Example: `Challenge-ELK`.
- Click **"Deploy"** and wait until status is **Running**.

---

## 3. Connecting to the VM

Open **PowerShell** and use SSH:

```bash
ssh root@<your-public-IP>
```

Accept the connection (`yes`) and enter the copied password.

**Update the system:**

```bash
apt-get update && apt-get upgrade -y
```

---

## 4. Installing Elasticsearch

Download Elasticsearch:

```bash
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.17.2-amd64.deb
```

Install:

```bash
dpkg -i elasticsearch-8.17.2-amd64.deb
```

> ⚠️ **Save Security Auto-Configuration Details** — contains superuser credentials.

### Reset Elasticsearch Password (if needed)

```bash
/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
```

---

## 5. Configuring Elasticsearch

Open the configuration file:

```bash
nano /etc/elasticsearch/elasticsearch.yml
```

Modify the following settings:

**Network Host** — uncomment and edit:

```yaml
network.host: <your-public-IP>
```

**HTTP Port** — uncomment (leave as default `9200`).

Save and exit (`Ctrl + X`, `Y`, `Enter`).

---

## 6. Setting Up a Firewall

- Go to **Vultr > VM Settings > Firewall**.
- Click **"Manage"** > **"Add Firewall Group"**.
  - Name: `SOC-Simulation`.
  - Restrict SSH to your IP only.
- Assign the firewall to the VM under **Compute > VM > Settings > Firewall**.
  - Select the new firewall and update the setting.

---

## 7. Starting Elasticsearch Service

```bash
systemctl daemon-reload
systemctl enable elasticsearch.service
systemctl start elasticsearch.service
```

**Check Status:**

```bash
systemctl status elasticsearch.service
```

Ensure it is **active and running**.

---

*→ Next: [Day 04 — Installing Kibana](./day-04-installing-kibana.md)*
