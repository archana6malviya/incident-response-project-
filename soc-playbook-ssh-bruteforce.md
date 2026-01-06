# 🛡️ SOC Playbook – SSH Brute-Force Attack Response

## 📌 Playbook Overview
This playbook provides **standard operating procedures (SOPs)** for detecting, investigating, responding to, and closing **SSH brute-force attacks** in a Security Operations Center (SOC).

It is designed for **Tier 1 / Tier 2 SOC Analysts** to ensure fast, consistent, and effective incident handling.

---

## 🔖 Playbook Details
- **Playbook Name:** SSH Brute-Force Attack Response
- **Incident Type:** Unauthorized Access Attempt
- **Severity Level:** Medium
- **SOC Level:** L1 / L2
- **Last Updated:** <Add Date>

---

## 🚨 Trigger Conditions
Initiate this playbook when **any** of the following conditions are met:

- More than **5 failed SSH login attempts** from a single IP within **5 minutes**
- Repeated login failures for multiple user accounts
- SIEM alert indicating SSH authentication failures

---

## 🔍 Detection Sources
- Linux Authentication Logs (`/var/log/auth.log`)
- SIEM Alerts (Splunk / ELK)
- Firewall logs
- IDS/IPS alerts (if available)

---

## 🧪 Investigation Steps

### Step 1: Validate the Alert
- Confirm the alert is related to SSH authentication failures
- Verify timestamp, hostname, and affected service

---

### Step 2: Analyze Logs
```bash
sudo grep "Failed password" /var/log/auth.log

Confirm:

Repeated failures

Same source IP

Same or multiple usernames

Step 3: Identify Indicators of Compromise (IOCs)

sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}'

Collect:

Source IP address

Target username(s)

Time range of the activity

Step 4: Check for Successful Logins
sudo grep "Accepted password" /var/log/auth.log


✅ If no successful login → continue response
❌ If successful login found → escalate severity

⚠️ Impact Assessment

Determine:

Was access gained? (Yes / No)

Any privilege escalation?

Any suspicious post-login activity?

Any internal systems affected?

🛠️ Response & Containment Actions
Immediate Actions

Block malicious IP address using firewall:

sudo ufw deny from <MALICIOUS_IP>


Monitor logs for continued attempts

Additional Hardening (If Required)

Enable account lockout policy

Disable password-based SSH login

Enable SSH key-based authentication

🚀 Escalation Criteria

Escalate to SOC Tier 2 / Incident Response Team if:

Successful SSH login is detected

Multiple hosts are targeted

Internal IP addresses are involved

Privileged accounts are targeted

🧹 Recovery Steps

Reset affected user credentials (if compromised)

Review system logs for anomalies

Apply security patches

Implement additional monitoring rules

✅ Closure Criteria

Close the incident when:

No further malicious activity observed for 24 hours

Malicious IPs are blocked

System integrity is confirmed

Incident report is completed

📄 Documentation & Evidence

Ensure the following are documented:

Incident Report ID

Source IP addresses

Log screenshots

Actions taken

Lessons learned

📚 Lessons Learned & Improvements

Deploy fail2ban

Restrict SSH access using firewall rules

Monitor SSH logs via SIEM

Apply rate limiting

🧠 MITRE ATT&CK Mapping

Tactic: Credential Access

Technique: Brute Force (T1110)

👤 Playbook Owner

SOC Analyst: Archana Malviya

📝 Notes

This playbook can be reused and adapted for:

FTP brute-force

RDP brute-force

Web login brute-force


---

### ✅ This playbook shows recruiters that you understand:
✔ SOC workflows  
✔ Escalation logic  
✔ Real incident handling  
✔ Professional documentation  

---

### Next (recommended)
👉 I can now:
1️⃣ Review your **incident-report.md**  
2️⃣ Convert this playbook into **Splunk alert + playbook**  
3️⃣ Create **SOC interview questions** from THIS playbook  

Just tell me 👍
