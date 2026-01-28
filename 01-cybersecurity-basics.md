# 🔐 Cybersecurity Basics – Foundations

This document covers the **core cybersecurity fundamentals** required for every security role, especially **DevOps, Cloud Security, and DevSecOps engineers**.

> 🎯 Goal: Understand **why security exists**, **how attacks happen**, and **how risks are identified and reduced**.

---

## 📌 1. CIA Triad (Core Security Principles)

The **CIA Triad** defines the three main goals of cybersecurity.

### 🔒 Confidentiality
Ensures that **only authorized users** can access sensitive data.

**Examples:**
- Encryption (TLS, AES)
- Access control (IAM, RBAC)
- VPN, private networks

**Hands-on Practice:**
```bash
# Generate SSH key
ssh-keygen

# Encrypt a file
openssl enc -aes-256-cbc -salt -in data.txt -out data.enc
