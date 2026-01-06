# 🚨 Incident Response & SOC Playbook

## 📌 Project Overview
This project demonstrates **end-to-end Incident Response handling** performed by a SOC Analyst.  
It covers **incident detection, investigation, documentation, and response playbook creation** using real Linux security logs.

The goal of this project is to simulate **real-world SOC operations** and showcase practical cybersecurity skills required for an **Entry-Level SOC Analyst** role.

---

## 🎯 Objectives
- Detect a security incident from system logs
- Investigate Indicators of Compromise (IOCs)
- Perform log-based threat analysis
- Document findings in a professional Incident Report
- Create a reusable SOC Playbook for future incidents

---

## 🛠 Tools & Technologies Used
- **Operating System:** Ubuntu Linux
- **Logs Analyzed:** `/var/log/auth.log`
- **Services:** OpenSSH
- **Commands:** grep, awk, sort, uniq
- **Documentation:** Markdown (.md)
- **Version Control:** GitHub

---

## 🔥 Incident Scenario
- **Incident Type:** SSH Brute-Force Attack
- **Severity Level:** Medium
- **Attack Source:** External IP Address
- **Attack Pattern:** Multiple failed SSH login attempts

---

## 🧪 Hands-On Investigation Steps
1. Enabled and monitored SSH service
2. Simulated brute-force login attempts
3. Verified log generation in auth logs
4. Extracted failed login events
5. Identified malicious IP addresses
6. Counted repeated attack attempts
7. Assessed impact and confirmed no successful compromise

---

## 🔍 Sample Investigation Commands
```bash
sudo grep "Failed password" /var/log/auth.log
sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}'
sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr
