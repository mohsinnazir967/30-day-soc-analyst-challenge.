# Day 26: Investigating an SSH Brute Force Alert

**Week:** 4 | **Phase:** Incident Investigation
**← [Back to README](../../README.md) | [← Day 25](./day-25-osticket-integration.md)**

---

## 1. Introduction

**Goal:** Learn how to investigate an SSH Brute Force alert and identify key indicators.

---

## 2. Accessing Alerts

1. Click on the hamburger icon and select **Alerts** under the security tab.
2. Review the list of alerts and select the first one for investigation.
3. Expand the alert by clicking on **View Details**.
4. Review the description and details of the alert.

---

## 3. Investigative Methodology

### Question 1: Is the IP Known for Brute Force Activity?

- Use tools like **AbuseIPDB** and **GreyNoise** to check the reputation of the IP address.
- *Example: An IP reported 1,816 times with 100% confidence of abuse is highly suspicious.*

### Question 2: Were Any Other Users Affected by This IP?

- Search for the IP address in Kibana's Discover tab.
- Check for distinct users targeted by the IP.
- *Example: Users root, oracle, guest, and test were targeted.*

### Question 3: Were Any Logins Successful?

- Search for successful login attempts using keywords like `accepted`.
- Ensure correct capitalization in queries.
- *Example: No successful logins found within the last 30 days.*

### Question 4: What Activity Occurred After Successful Logins?

- If there were successful logins, investigate subsequent activities.
- Look for signs of malicious behavior: downloading scripts, running discovery commands, or executing malicious files.

---

## 4. Closing the Alert

**Document Findings:**
- In a real-world environment, document your findings in the ticketing system.
- Add notes and follow the process for closing the alert.

**Modify Rules for Ticketing System Integration:**
- Click on `Rules` in the left menu.
- Select the SSH Brute Force attempt rule and click on **Edit Rule Settings**.
- Under actions, select `Web Hook` and configure it to push alerts to the ticketing system.

---

## 5. Configuring Ticketing System Integration

1. **Set Action Frequency** — Choose `For each alert` or `Summary of alerts per rule run`.
2. **Customize Ticket Body** — Use the test example provided by osTicket. Remove unnecessary fields like IP and attachments. Add relevant variables such as rule name and message content.
3. **Save Changes and Test** — Save the changes and run a test. Verify ticket creation in osTicket.

---

## 6. Reviewing and Closing Tickets

1. **Review Ticket Details** — Check the subject and comments for relevant information. Ensure the rule name and investigation details are included.
2. **Assign and Document** — Assign the ticket to yourself or another analyst. Document findings and actions taken in the ticket.
3. **Resolve and Close Ticket** — Provide a reason for closing the ticket. Select `Resolved` and post a reply to close the ticket.

---

*→ Next: [Day 27 — Investigating RDP Brute Force Alert](./day-27-investigating-rdp-alert.md)*
