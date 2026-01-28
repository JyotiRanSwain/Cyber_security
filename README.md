# 🔐 60-Day Cybersecurity Learning Plan (DevOps + AWS Focus)

**Level Up Your Cybersecurity Skills as a DevOps & AWS Cloud Engineer**  

This is a **structured 60-day roadmap** to transition into **Cybersecurity**, focusing on **Cloud Security, DevSecOps, and SOC Operations** — tailored for the **2026 Indian market**.

---

## ⏱ Daily Time Required
- **Weekdays:** 1.5–2 hours  
- **Weekends:** 3–4 hours (labs + revision)

---

## 🚀 **Day 0 – Setup (Very Important)**

**Before Day 1, set up your environment:**

### ✅ **Environment Setup**
- **Install Kali Linux** (VMware / VirtualBox)
- **Install Ubuntu Server VM**
- **Create AWS Free Tier Account**
- **Install Tools:**
  - `Nmap`
  - `Burp Suite Community`
  - `Wireshark`
  - `Docker`
  - `Trivy`
  - `Git`

---

## 🧠 **Phase 1: Cybersecurity Foundations (Days 1–10)**

**Goal:** Understand **how attacks work** and **basic security concepts**.

| **Days** | **Topics** | **Hands-on Labs** |
|----------|------------|-----------------|
| 1–2      | **Cybersecurity Basics:** CIA Triad, Threat vs Vulnerability vs Risk, OWASP Top 10 | Read **OWASP Top 10 examples**, Identify risks in past projects |
| 3–4      | **Networking for Security:** TCP/IP, Ports, Protocols, DNS, HTTP/HTTPS, TLS, Firewalls, NAT | Use `netstat`, `ss`, `tcpdump`, Analyze traffic in **Wireshark** |
| 5–6      | **Linux & Windows Security:** Users, permissions, sudo, SSH hardening, Logs, Event Viewer | Create users, restrict permissions, Harden SSH |
| 7–8      | **Cryptography Basics:** Hashing vs Encryption, Symmetric vs Asymmetric, SSL/TLS | Generate SSH keys, Use `openssl` to encrypt/decrypt files |
| 9–10     | **Python for Security:** Automation, Log Parsing, Regex, Requests | Write Python scripts to **scan ports** and **parse logs** |

---

## 🛡️ **Phase 2: Offensive Security (Days 11–25)**

**Goal:** Learn **how attackers think** — strengthens your defense skills.

| **Days** | **Topics** | **Hands-on Labs** |
|----------|------------|-----------------|
| 11–13    | **Network Scanning:** Nmap, TCP/UDP scans, Service & OS detection | `nmap -sS -sV -O target_ip` |
| 14–16    | **Web App Security:** OWASP Top 10 deep dive, SQLi, XSS, CSRF | **Burp Suite proxy**, Practice on **DVWA / Juice Shop** |
| 17–19    | **Exploitation Basics:** Metasploit, Reverse shells, Payloads | Exploit vulnerable VM (**Metasploitable2**) |
| 20–22    | **Password Attacks:** Brute force, Hash cracking | Tools: **Hydra**, **John the Ripper**, Crack sample hashes |
| 23–25    | **Capture the Flag (CTF)** | Solve at least **5 beginner machines** on TryHackMe or Hack The Box |

---

## ☁️ **Phase 3: Cloud Security (AWS) (Days 26–40)**

**Goal:** Become a **Cloud Security Engineer**.

| **Days** | **Topics** | **Hands-on Labs** |
|----------|------------|-----------------|
| 26–28    | **AWS Security Fundamentals:** IAM users, roles, policies, Security Groups, NACL, Shared Responsibility Model | Create **least-privilege IAM policy**, Break & fix IAM permissions |
| 29–31    | **AWS Monitoring & Detection:** CloudTrail, GuardDuty, Security Hub, AWS Config | Enable **GuardDuty**, Trigger sample findings |
| 32–34    | **AWS Network Security:** VPC security, Private vs Public subnets, Bastion host | Lock EC2 access to **Bastion only** |
| 35–37    | **Cloud Security Auditing:** Tools: Prowler, ScoutSuite | Scan AWS account, Fix critical findings |
| 38–40    | **AWS WAF & Shield** | Protect **ALB** using WAF, Block SQL injection patterns |

---

## 🔁 **Phase 4: DevSecOps (Days 41–55)**

**Goal:** Merge **DevOps & Security** for high-paying roles.

| **Days** | **Topics** | **Hands-on Labs** |
|----------|------------|-----------------|
| 41–43    | **CI/CD Security:** Shift Left Security, SAST vs DAST | Tools: SonarQube, OWASP ZAP – Add **SAST scan** in pipeline |
| 44–46    | **Container Security** | Tools: Trivy, Docker Bench – Scan Docker images, Fix CVEs |
| 47–49    | **Infrastructure as Code Security** | Tools: Checkov, Terrascan – Scan Terraform code, Fix misconfigs |
| 50–52    | **Runtime Security** | Tools: Falco, Sysdig – Detect container anomalies |
| 53–55    | **Secrets & Access** | Tools: Vault, TruffleHog, GitLeaks – Detect leaked secrets in repos |

---

## 📊 **Phase 5: SOC & Incident Response (Days 56–60)**

**Goal:** Understand **real-world security operations**.

| **Days** | **Topics** | **Hands-on Labs** |
|----------|------------|-----------------|
| 56–57    | **SIEM Basics:** Logs, alerts, correlation, SOC workflow | Tools: Splunk (Free), ELK Stack – Ingest Linux logs, Create alerts |
| 58–59    | **Incident Response:** Incident lifecycle, Forensics basics | Tools: Autopsy, Volatility |
| 60       | **Final Project** | Build a **Secure AWS App** with DevSecOps: EC2 + ALB + WAF, IAM least privilege, CI/CD security scans, GuardDuty, Container scanning. Push project to **GitHub & Resume** |

---

## 📌 **Tips for Success**
- Stick to the **daily schedule**  
- Take notes and commit labs to **GitHub**  
- Practice on **TryHackMe / Hack The Box**  
- Share your **final project** on GitHub to showcase skills  
- After 60 days, aim for **AWS Security Specialty**, **CEH**, or **OSCP**

---

### 💡 **Recommended Roles After 60 Days**
- **DevSecOps Engineer**  
- **Cloud Security Engineer (AWS)**  
- **SOC Analyst (L2)**  
- **Security Automation Engineer**

---

**Happy Learning!** 🚀
