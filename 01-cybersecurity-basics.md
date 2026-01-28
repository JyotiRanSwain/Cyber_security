# 🔐 Cybersecurity Basics – Detailed Guide (Phase 1)

This guide covers the **core foundations of cybersecurity** every DevOps & Cloud Engineer must know.
It focuses on **concepts + hands-on labs + real-world mapping**.

---

## 📌 1️⃣ CIA Triad (Confidentiality, Integrity, Availability)

The **CIA Triad** is the foundation of cybersecurity.  
Every security control must support **at least one** of these pillars.

### 🔹 CIA Triad Overview

| Principle | Meaning | Examples / Practice |
|--------|--------|--------------------|
| **Confidentiality** | Only authorized users can access data | - Encrypt sensitive data (AES, TLS)<br>- Restrict access using IAM & RBAC<br>- Test unauthorized access |
| **Integrity** | Data must not be altered without authorization | - File hash verification (MD5 / SHA256)<br>- Git version control<br>- Detect file tampering |
| **Availability** | Systems must be accessible when needed | - Monitor uptime (Prometheus, CloudWatch)<br>- Use redundancy & failover<br>- DoS simulation (lab only) |

---

### 🧪 Hands‑On Exercises (CIA Triad)

#### ✅ Confidentiality
```bash
# Create a file
echo "secret-data" > data.txt

# Encrypt the file
openssl enc -aes-256-cbc -salt -in data.txt -out data.enc

---
### 🔹 Threat vs Vulnerability vs Risk
| Term              | Meaning                               | Example                  |
| ----------------- | ------------------------------------- | ------------------------ |
| **Threat**        | A potential attacker or harmful event | Hacker, malware          |
| **Vulnerability** | A weakness in a system                | Weak password, open port |
| **Risk**          | Probability + impact of exploitation  | Data breach              |


🔍 Real Example

Threat: External attacker
Vulnerability: SSH allows password login
Risk: Server compromise

🧪 Hands-on Practice

Step 1: Find vulnerabilities
```bash
nmap -sV target_ip

Step 2: Identify threat
Internet-facing service
No firewall restriction

Step 3: Assess risk
High likelihood + high impact = High Risk
✔ Document findings in a markdown file.

### OWASP Top 10 (Web Application Security)
The OWASP Top 10 lists the most critical web application security risks.

🔥 Most Important OWASP Risks
| ID  | Risk                      | Description                             |
| --- | ------------------------- | --------------------------------------- |
| A01 | Broken Access Control     | Unauthorized access to resources        |
| A02 | Cryptographic Failures    | Weak or missing encryption              |
| A03 | Injection                 | SQL, OS, LDAP injection                 |
| A05 | Security Misconfiguration | Default configs, open ports             |
| A06 | Vulnerable Components     | Outdated libraries                      |
| A07 | Auth Failures             | Weak authentication                     |
| A10 | SSRF                      | Server fetches attacker-controlled URLs |


🧪 OWASP Hands-on Labs
Setup Vulnerable App
DVWA or OWASP Juice Shop
Run using Docker:

```bash
docker run -d -p 3000:3000 bkimminich/juice-shop
