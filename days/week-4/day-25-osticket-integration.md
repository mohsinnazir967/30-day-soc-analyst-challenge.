# Day 25: Integrating osTicket into Your Tech Stack

**Week:** 4 | **Phase:** SIEM-Ticketing Integration
**← [Back to README](../../README.md) | [← Day 24](./day-24-osticket-setup.md)**

---

## 1. Introduction

**Goal:** Successfully integrate osTicket into your tech stack and confirm the integration by sending a test alert.

---

## 2. Setting Up API Key in osTicket

**Access osTicket Admin Panel:**
- Click on `Admin` at the top right corner.
- Select `Manage` then `API`.

**Add New API Key:**
- Click **Add New API Key**.
- Enter the private IP address of your `Challenge-ELK` server (if in the same VPC) or the public IP address (if not).
- Enable the `Can Create Tickets` service.
- Add internal notes (e.g., `Challenge - 30 day SOC Elastic Connector`).
- Click `Add Key` and copy the generated API key.

---

## 3. Configuring Elastic Connector

**Enable Free 30-Day Trial:**
- Go to `Stack Management` under the hamburger icon.
- Select `Manage License` and start the 30-day trial.

**Create Connector:**
- Go to `Connectors` under `Alerts and Insights`.
- Click on `Create Connector`.
- Choose `Web Hook` and name it `OS Ticket`.
- Set the request type to `POST`.
- Enter the URL: `http://<OS_Ticket_IP>/osticket/upload/api/tickets.xml`
- Select `None` for authentication.
- Add an HTTP header with key `x-api-key` and value as the copied API key.
- Click `Save and Test`.

---

## 4. Creating Action Body

**Get XML Payload Example from osTicket GitHub and customize:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ticket alert="true" autorespond="true" source="API">
    <name>Angry User</name>
    <email>api@osticket.com</email>
    <subject>Testing API Haji</subject>
    <phone>318-555-8634X123</phone>
    <message type="text/plain"><![CDATA[Message content here]]></message>
</ticket>
```

Paste the XML payload into the connector action body and customize the subject.

---

## 5. Troubleshooting Connection Issues

1. **Check Network Connection** — If you encounter a timeout error, it indicates a network connection issue.
2. **Verify IP Configuration** — Ensure the osTicket server has the correct private IP address. Update the network adapter settings if necessary to set IPv4 address to the Challenge-OSticket Private VPC address.
3. **Update Connector Configuration** — Change the connector URL to use the private `Challenge-OSticket` server IP address. Save and rerun the test.

---

## 6. Confirming Integration

1. Go to the agent panel in osTicket.
2. Verify that the test alert has created a ticket.
3. Ensure the ticket details match the expected results.

---

## 7. Integrated Alert Flow

```
Kibana Alert Fires
      │
      ▼
osTicket API (Web Hook)
      │
      ▼
Ticket Created Automatically
      │
      ▼
SOC Analyst Assigned → Investigate → Resolve
```

---

*→ Next: [Day 26 — Investigating SSH Brute Force Alert](./day-26-investigating-ssh-alert.md)*
