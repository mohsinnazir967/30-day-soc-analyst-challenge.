# Day 24: Setting Up and Configuring osTicket

**Week:** 4 | **Phase:** Ticketing Platform Setup
**← [Back to README](../../README.md) | [← Day 23](./day-23-ticketing-systems.md)**

---

## 1. Introduction

**Goal:** Successfully set up and configure osTicket, a ticketing system for the challenge.

---

## 2. Deploying the Server

1. **Log in to Vultr** → Click `Deploy` → **Deploy New Server**.
2. Choose `Cloud Compute` with a shared CPU.
3. Select `Singapore` as the location.
4. Choose `Windows Standard 2022` as the operating system.
5. Select `Cloud Regular Compute` plan: 55 GB, 1 CPU, 2 GB memory.
6. Disable `auto backup` and `IPv6`.
7. Enable `Virtual Private Cloud`.
8. Set the hostname to `Challenge-OSticket`.
9. Click `Deploy Now`.

**Access the Server:**
- After setup, select **View Console**.
- RDP into the machine:

```bash
xfreerdp /v:<Challenge-OSticket-IP> /u:Administrator
```

---

## 3. Setting Up the Firewall

- Go to **Settings** > **Firewall**.
- Use the `SOC Simulation` firewall — restricts access to the web server hosting the ticketing system.

---

## 4. Installing XAMPP

1. Search for `XAMPP` and go to the [Apache Friends website](https://www.apachefriends.org/).
2. Download version 8.2.2 (or the latest available version).
3. Open the installer and follow the setup wizard.
4. Note the installation directory (default: `C:\xampp`).
5. Complete the installation and open the XAMPP control panel.

---

## 5. Configuring XAMPP

1. Go to `C:\xampp` and find the `properties` configuration file.
2. Change `apache_domainname` to your `Challenge-OSticket` public IP address.
3. Save the changes.

**Create Firewall Rules:**
- Open **Windows Defender Firewall with Advanced Security**.
- Create new inbound rules for ports `80` and `443`.
- Allow TCP connections on these ports.

---

## 6. Starting XAMPP Services

1. Open the XAMPP control panel.
2. Start the **Apache** and **MySQL** services.
3. Access phpMyAdmin at: [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/)

---

## 7. Configuring phpMyAdmin

**Authorize Public IP Address:**

- Go to phpMyAdmin → **User Accounts**.
- Modify the `root` account (hostname: `localhost`):
  - Change hostname to `Challenge-OSticket` public IP address.
  - Set the password to `Winter2024!`.
- Modify the `pma` account (hostname: `localhost`):
  - Change hostname to `Challenge-OSticket` public IP address.
  - Set the password to `Winter2024!`.

**Edit phpMyAdmin Configuration File:**
- Go to the `phpMyAdmin` directory and find `config.inc.php`.
- Make a backup of the file.
- Change the server host to your `Challenge-OSticket` public IP address and password to `Winter2024!`.
- Change the `pma` user password to `Winter2024!` under **User for advanced features**.

---

## 8. Installing osTicket

1. Go to [osticket.com/download](https://osticket.com/download/) and download the self-hosted version.
2. Extract the downloaded osTicket files, then extract again the sub-folder `osTicket-v1.18.2`.
3. Create a new directory called `osticket` under the `htdocs` directory in XAMPP.
4. Copy the extracted files into the `osticket` directory.
5. Open a browser and navigate to: `http://<Challenge-OSticket-IP>/osticket/upload`
6. Follow the setup instructions.
7. Rename `ost-sampleconfig.php` to `ost-config.php` in `C:\xampp\htdocs\osticket\upload\include`.

---

## 9. Setting Up osTicket

**Basic Installation:**
- Enter the help desk name, admin username, and password.
- Create a new database in phpMyAdmin named `challenge-db`.

**Database Configuration:**
- Use the root username and public IP address for the MySQL host.
- Enter the password `Winter2024!`.

**Complete Installation:**
- Ensure the database is created and privileges are set.
- Complete the osTicket setup.

---

## 10. Finalizing osTicket Setup

**Configure File Permissions:**

Navigate to `C:\xampp\htdocs\osticket\upload\include` and run:

```powershell
icacls ./ost-config.php /reset
```

**Access osTicket URLs:**

| URL | Purpose |
|-----|---------|
| `http://Challenge-OSticket-IP/osticket/upload/` | Customer portal |
| `http://Challenge-OSticket-IP/osticket/upload/scp` | Staff control panel |

**Log in to osTicket** using the staff control panel URL with the username and password created during setup.

---

## 11. Exploring osTicket

**Admin Panel:**
- Access the admin panel to configure settings.
- Change the name and title if desired.
- Create new agent accounts for additional users.

**Managing Tickets:**
- Use the admin panel to manage and track tickets.
- Assign and transfer tickets as needed.

---

*→ Next: [Day 25 — osTicket Integration](./day-25-osticket-integration.md)*
