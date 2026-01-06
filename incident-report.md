# 🚨 Incident Report – SSH Brute-Force Attack

## 📌 Incident Information
- **Incident ID:** IR-SSH-001  
- **Incident Type:** SSH Brute-Force Attack  
- **Severity Level:** Medium  
- **Status:** Closed  
- **Date Detected:** <Add Date>  
- **Reported By:** System Log Monitoring  
- **Analyst Name:** Archana Malviya  

---

## 📝 Executive Summary
Multiple failed SSH login attempts were detected from an external IP address targeting a Linux server.  
The activity pattern indicated a **brute-force attack** attempting unauthorized access.  
No successful login was observed, and the attack was contained by blocking the malicious IP.

---

## ⏰ Incident Timeline

| Time (IST) | Event Description |
|-----------|------------------|
| 10:30     | First failed SSH login detected |
| 10:32     | Multiple failed attempts from same IP |
| 10:35     | Brute-force attack confirmed |
| 10:37     | Malicious IP blocked |
| 10:45     | Monitoring confirmed no further attempts |

---

## 🔍 Detection Details
- **Detection Source:** Linux Authentication Logs (`/var/log/auth.log`)
- **Detection Method:** Manual log analysis
- **Alert Type:** Repeated failed SSH authentication attempts

---

## 🧪 Investigation Summary

### Logs Analyzed
- `/var/log/auth.log`

### Key Findings
- Repeated failed login attempts
- Same source IP used multiple times
- Multiple usernames targeted
- No successful authentication observed

---

## 🧾 Indicators of Compromise (IOCs)

| Indicator Type | Value |
|---------------|------|
| Source IP     | `<MALICIOUS_IP>` |
| Target Port   | 22 (SSH) |
| Attack Method | Brute-force login attempts |

---

## ⚠️ Impact Assessment
- **System Compromised:** No  
- **Data Loss:** No  
- **Service Disruption:** No  
- **User Accounts Affected:** None  

**Impact Level:** Low  
*(Attack was detected early and contained successfully)*

---

## 🔎 Root Cause Analysis
- SSH service exposed to the internet
- Password-based authentication enabled
- No rate-limiting or automated blocking configured

---

## 🛠️ Containment & Remediation Actions

### Immediate Actions Taken
- Blocked malicious IP using firewall
  
       sudo ufw deny from <MALICIOUS_IP>



### Preventive Measures Recommended

Enable SSH key-based authentication

Deploy fail2ban for automatic blocking

Restrict SSH access to trusted IPs

Monitor logs via SIEM

🚀 Escalation Decision

Escalation Required: No

Reason: No successful login or lateral movement detected


✅ Incident Closure

No further malicious activity observed for 24 hours

System integrity verified

Incident documented and closed

Closure Date: <Add Date>

📚 Lessons Learned

Continuous log monitoring is critical

Brute-force attacks are common on exposed SSH services

Automated response tools reduce response time

🧠 MITRE ATT&CK Mapping

Tactic: Credential Access

Technique: Brute Force (T1110)

🧾 Evidence Collected

Log screenshots

Command outputs

Firewall block confirmation

👤 Prepared By

Archana Malviya
Aspiring SOC Analyst | Cybersecurity Enthusiast


---

### ✅ Why this incident report is STRONG
✔ Real SOC format  
✔ Clear timeline & IOCs  
✔ Shows investigation + response  
✔ Interview & resume ready  

---

