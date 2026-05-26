# Day 04: Installing and Configuring Kibana

**Week:** 1 | **Phase:** ELK Setup
**← [Back to README](../../README.md) | [← Day 03](./day-03-setting-up-elasticsearch.md)**

---

## 1. Introduction

- **Goal:** Set up and install a Kibana instance.
- Visit [elastic.co/downloads/kibana](https://www.elastic.co/downloads/kibana) to download Kibana.

---

## 2. Download and Install Kibana

Select `Deb x86_64` version (as of recording, version 8.15).

Download it in the SSH session:

```bash
wget https://artifacts.elastic.co/downloads/kibana/kibana-8.17.2-amd64.deb
```

Verify the download:

```bash
ls
```

Install Kibana:

```bash
dpkg -i kibana-8.17.2-amd64.deb
```

---

## 3. Configure Kibana

Open the configuration file:

```bash
sudo vim /etc/kibana/kibana.yml
```

Modify the following lines:

```yaml
server.port: 5601
server.host: <your_public_IP>
```

Save and exit (`Esc`, `:wq!`)

---

## 4. Start and Enable Kibana Service

```bash
systemctl daemon-reload
systemctl enable kibana.service
systemctl start kibana.service
systemctl status kibana.service
```

---

## 5. Generate Enrollment Token

Navigate to the Elasticsearch binary directory:

```bash
cd /usr/share/elasticsearch/bin
```

Generate the token:

```bash
./elasticsearch-create-enrollment-token --scope kibana
```

Copy the generated token for later use.

---

## 6. Access Kibana Web Interface

Open a browser and go to:

```
http://<your_public_IP>:5601
```

If `Connection Timed Out` occurs:

Allow the necessary port in the firewall:

```bash
ufw allow 5601
```

Modify `SOC-Simulation` cloud firewall rules to allow ports `1-65535` from your IP.

---

## 7. Enter Enrollment Token and Login

Paste the copied enrollment token in the web interface.

**Generate verification code in Terminal:**

Navigate to the Kibana binary directory:

```bash
cd /usr/share/kibana/bin
./kibana-verification-code
```

Enter the displayed verification code.

**Login:**

Use `elastic` as the username and retrieve the password from the installation log or reset it:

```bash
cd /usr/share/elasticsearch/bin
./elasticsearch-reset-password -u elastic
```

---

## 8. Configure Encryption Keys

Navigate to the Kibana binary directory:

```bash
cd /usr/share/kibana/bin
```

**Generate encryption keys:**

```bash
./kibana-encryption-keys generate
```

Copy the generated keys and store them.

**Add them to the Kibana keystore (one by one):**

```bash
./kibana-keystore add xpack.encryptedSavedObjects.encryptionKey
./kibana-keystore add xpack.reporting.encryptionKey
./kibana-keystore add xpack.security.encryptionKey
```

**Restart Kibana:**

```bash
systemctl restart kibana
```

Login again to confirm settings.

---

*→ Next: [Day 05 — Windows Server Setup](./day-05-windows-server-cloud.md)*
