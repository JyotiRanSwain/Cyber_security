## 🌐 Networking for Security – Complete Guide (DevOps + Cybersecurity)
### 🎯 Why Networking Matters in Security

Every cyber-attack travels over the network.
If you understand networking deeply, you can:

Detect attacks early

Block malicious traffic

Secure cloud & on-prem systems

Pass interviews confidently

### 🧠 1️⃣ TCP/IP Model (Security View)
| Layer | Name           | What happens here     | Security relevance |
| ----- | -------------- | --------------------- | ------------------ |
| 4     | Application    | HTTP, HTTPS, DNS, SSH | XSS, SQLi, SSRF    |
| 3     | Transport      | TCP, UDP              | Port scanning, DoS |
| 2     | Internet       | IP, ICMP              | IP spoofing        |
| 1     | Network Access | Ethernet              | ARP poisoning      |

🔐 Security Rule:
Attacks can occur at every layer, not just the application.

## 🔌 2️⃣ Ports & Protocols
### What is a Port?
A port identifies which service is running on a machine.
| Port | Protocol | Service | Risk           |
| ---- | -------- | ------- | -------------- |
| 22   | TCP      | SSH     | Brute force    |
| 80   | TCP      | HTTP    | Plaintext data |
| 443  | TCP      | HTTPS   | Misconfig TLS  |
| 3306 | TCP      | MySQL   | DB exposure    |
| 6379 | TCP      | Redis   | Data leak      |


### 🧪 Hands-On: List Open Ports
Linux / Kali
"""
ss -tulnp
"""
or
"""
netstat -tulnp
"""
Windows
"""
netstat -ano
"""

📌 Security Insight
If a port is open → it is attackable.

## 🌍 3️⃣ DNS (Domain Name System)
### What DNS Does
Converts:
"""
example.com → IP address
"""
#### DNS Security Risks
DNS Spoofing
DNS Cache Poisoning
Malicious redirects

### 🧪 Hands-On: DNS Testing
"""
nslookup google.com
"""

"""
dig google.com
"""
Check:
A record
TTL
Resolver IP
#### 🔐 Security Tip
Always use:
DNS over HTTPS (DoH)
Trusted resolvers

## 🌐 4️⃣ HTTP vs HTTPS
| Feature         | HTTP       | HTTPS     |
| --------------- | ---------- | --------- |
| Encryption      | ❌ No       | ✅ Yes     |
| Port            | 80         | 443       |
| Data visibility | Plain text | Encrypted |
| Security        | Unsafe     | Secure    |

### 🧪 Hands-On: Capture HTTP Traffic
"""
tcpdump -i eth0 port 80
"""

## 🔐 5️⃣ TLS / SSL (Very Important)
#### What TLS Does
Encrypts data
Verifies server identity
Prevents MITM attacks
---
## 🧪 Hands-On: Inspect TLS
"""
openssl s_client -connect google.com:443
""

Check:
Certificate issuer
Expiry date
TLS version

---
## 🔥 6️⃣ Firewalls
### Types of Firewalls
Host-based (iptables, Windows Firewall)
Network firewall
Cloud firewall (AWS Security Group)

---

### 🧪 Hands-On: Linux Firewall
"""
iptables -L
"""
Block SSH from all:
"""
iptables -A INPUT -p tcp --dport 22 -j DROP
"""
Allow SSH only from your IP:

"""
iptables -A INPUT -p tcp -s YOUR_IP --dport 22 -j ACCEPT
"""
#### 🔐 Security Rule
Default-deny is safer than allow-all.
---

## 🌐 7️⃣ NAT (Network Address Translation)
### What NAT Does
Converts private IP → public IP
Hides internal network
### Security Benefit
Internal IPs not directly exposed

Reduces attack surface

#### ⚠️ NAT ≠ Firewall
NAT hides, firewall blocks.

---

### 📡 8️⃣ Packet Analysis Tools
### tcpdump (CLI)
Capture traffic:

"""
tcpdump -i eth0
"""

Filter HTTP:
"""
tcpdump -i eth0 port 80
"""
Save to file:
"""
tcpdump -i eth0 -w capture.pcap
"""

----

### Wireshark (GUI)
#### What to Analyze
HTTP requests
DNS queries
TLS handshake
Suspicious IPs

Filters:
"""
http
dns
tcp.port == 80
ip.addr == 10.10.6.36
"""

#### 🔍 Security Use Case
Detect data leakage
Detect brute force
Investigate incidents

---

## 🧪 LAB: Full Networking Security Exercise
### 🎯 Objective
Analyze traffic to understand security risks.

### Steps
1. Run a web app (Flask / Juice Shop)
2. Capture traffic with Wireshark
3. Perform login
4. Observe:
  Credentials (HTTP vs HTTPS)
  Cookies
  Headers

### Result
HTTP → credentials visible ❌
HTTPS → encrypted ✅

---

### 📊 Common Attacks Mapping

| Attack            | Network Layer |
| ----------------- | ------------- |
| Port Scan         | Transport     |
| MITM              | Network       |
| DNS Spoofing      | Application   |
| DoS               | Transport     |
| Session Hijacking | Application   |


### ✅ Daily Practical Checklist
✔ List open ports
✔ Identify running services
✔ Capture traffic
✔ Inspect TLS
✔ Apply firewall rule
✔ Re-test connectivity
