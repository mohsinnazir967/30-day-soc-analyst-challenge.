# Day 09: Installing and Configuring Sysmon

**Week:** 1 | **Phase:** Endpoint Monitoring Setup
**← [Back to README](../../README.md) | [← Day 08](./day-08-understanding-sysmon.md)**

---

## 1. Introduction

**Goal:** Install Sysmon on the Windows Server and confirm it generates logs.

---

## 2. Connect to Windows Server

1. Use Remote Desktop to connect to `Challenge-WIN-Haji` (IP and credentials provided).
2. Open Microsoft Edge to download Sysmon.

---

## 3. Download Sysmon

- Google "Sysmon" and select the first link (learn.microsoft.com).
- Direct download link: [Download Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

---

## 4. Extract Sysmon

1. Navigate to the Downloads folder.
2. Right-click Sysmon and select "Extract All".
3. Confirm three binaries are extracted.

---

## 5. Download Configuration File

1. Google "Sysmon Olaf configuration" and select the GitHub link.
2. In the GitHub repository select [sysmonconfig.xml](https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml).
3. Download the file.
4. Save the configuration file in the Sysmon directory.

---

## 6. Open PowerShell

1. Open PowerShell as Administrator.
2. Navigate to the Sysmon directory using `cd`.

---

## 7. Install Sysmon

Run the command:

```powershell
./sysmon64.exe -accepteula -i sysmonconfig.xml
```

1. Confirm Sysmon service is running in Services.
2. Check Event Viewer for Sysmon logs:
   - Expand **Applications and Services Logs**.
   - Find **Microsoft > Windows > Sysmon > Operational** and view the log entries.

---

## 8. Verify Installation

1. Open Event Viewer.
2. Navigate to: `Applications and Services Logs > Microsoft > Windows > Sysmon > Operational`.
3. Confirm that logs are being generated.

---

*→ Next: [Day 10 — Ingesting Sysmon & Defender Logs](./day-10-ingesting-sysmon-defender-logs.md)*
