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
```
