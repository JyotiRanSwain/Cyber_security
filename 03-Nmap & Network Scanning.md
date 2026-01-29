# Nmap & Network Scanning – Detailed Notes (Beginner to Intermediate)

These notes are written in a **clear, structured, and exam / interview‑friendly way**, with **real-world attacker + defender perspective**. Ideal for **cybersecurity learning, CEH basics, and hands‑on labs**.

---

## 1. Nmap – Network Mapper

**Nmap** is an open‑source tool used for:

* Host discovery
* Port scanning
* Service & version detection
* OS detection
* Firewall & IDS evasion

👉 Used by **security engineers, penetration testers, and attackers**.

---

## 2. `nmap -sn` (Ping Scan / Host Discovery)

```bash
nmap -sn <IP or Subnet>
```

### What it does

* Checks **which hosts are alive**
* **Does NOT scan ports**

### How it works

* Sends ICMP Echo Request (ping)
* Uses ARP requests (in local network)

### Example

```bash
nmap -sn 192.168.1.0/24
```

### Use case

* First step of reconnaissance
* Find active machines in a network

---

## 3. Metasploitable 2

**Metasploitable 2** is a deliberately vulnerable Linux machine used for **practice and learning hacking**.

### Why it is used

* Contains **old, vulnerable services**
* Perfect for:

  * Nmap scanning
  * Exploitation practice
  * Learning Metasploit

### Default credentials

```
Username: mfadmin
Password: mfadmin
```

⚠️ **Never expose Metasploitable to the internet**

---

## 4. Important Networking & Scanning Tools

### 🔹 Nmap

* Port scanning
* OS & service detection

### 🔹 fping

* Faster alternative to ping
* Used for **ping sweep**

```bash
fping -a -g 192.168.1.0/24
```

### 🔹 tcpdump

* Command‑line packet sniffer
* Captures live traffic

```bash
sudo tcpdump -i eth0
```

### 🔹 subnetcalc

* Calculates subnet details
* Helps understand CIDR ranges

```bash
subnetcalc 192.168.1.0/24
```

---

## 5. Scanning Techniques (Very Important)

Attackers use **different TCP flag combinations** to bypass firewalls.

---

## 6. SYN Scan (Half‑Open Scan)

```bash
nmap -sS <ip>
```

### How it works

* Sends SYN packet
* If SYN‑ACK → port open
* Sends RST (no full connection)

### Why it is powerful

* Fast
* Stealthy
* Not logged by many systems

👉 **Most commonly used scan by hackers**

---

## 7. ACK Scan

```bash
nmap -sA <ip>
```

### Purpose

* Detects **firewall rules**
* Does NOT detect open ports

### Result

* Tells whether port is:

  * Filtered
  * Unfiltered

👉 Used to map firewall behavior

---

## 8. XMAS Scan

```bash
nmap -sX <ip>
```

### Why called XMAS

* Sets FIN, PSH, URG flags
* Packet "lights up" like a Christmas tree 🎄

### Behavior

* Closed port → RST reply
* Open port → No reply

👉 Useful for **firewall evasion**

---

## 9. NULL Scan

```bash
nmap -sN <ip>
```

### How it works

* Sends TCP packet **with no flags**

### Response

* Closed → RST
* Open → No response

👉 Stealth scan, OS dependent

---

## 10. Host Discovery Techniques

### 🔹 Ping Sweep (Nmap)

```bash
nmap -sn 192.168.1.0/24
```

### 🔹 fping Sweep

```bash
fping -a -g 192.168.1.0/24
```

### 🔹 ARP Scan (Best for LAN)

```bash
sudo arp-scan 192.168.1.0/24
```

### Why ARP Scan is powerful

* Works even if ICMP is blocked
* Very accurate on local networks

---

## 11. Network Discovery Tools

### 🔹 ip a

```bash
ip a
```

Shows:

* IP address
* Interface details

### 🔹 Netdiscover

```bash
sudo netdiscover -r 192.168.1.0/24
```

Uses ARP to find hosts

---

## 12. Traffic Analysis with Wireshark

### ICMP Sniffing

* Filter:

```
icmp
```

### Lab Task

* Sniff ICMP Echo Requests
* Compare:

  * arp‑scan results
  * ping sweep results

👉 You will notice **ARP scan finds more hosts**

---

## 13. Banner Grabbing

**Banner grabbing** means collecting information about:

* Service name
* Version
* OS details

---

### Passive Banner Grabbing

✔ No direct interaction
✔ Hard to detect

**Tools**:

* Wireshark
* tcpdump

```bash
sudo tcpdump -i eth0
```

---

### Active Banner Grabbing

✔ Direct connection to service
✔ Easier to detect

**Tools**:

* telnet
* netcat (nc)
* curl
* nmap

```bash
nmap -sV <ip>
```

---

## 14. Why Hackers Love Banner Info

From banner info attackers can:

* Identify vulnerable versions
* Search exploits
* Choose correct attack tools

Example:

> Apache 2.4.49 → Path traversal exploit

---

## 15. Nmap Hands‑On Commands

```bash
nmap <ip>                 # Basic scan
nmap -sP <ip>             # Ping scan (old)
nmap -F <ip>              # Fast scan
nmap -p 80 <ip>           # Specific port
nmap -sS <ip>             # SYN scan
nmap -sT <ip>             # TCP connect scan
nmap -A <ip>              # Aggressive scan
nmap -O <ip>              # OS detection
nmap -sV -T4 -v <ip>      # Version + speed
```

---

## 16. Zenmap GUI

**Zenmap** is the graphical interface of Nmap.

Features:

* Visual topology
* Saved scans
* Beginner‑friendly

Good for:

* Learning
* Reports

---

## 17. Firewall Evasion Techniques

### 🔹 Packet Fragmentation

```bash
nmap -f scanme.nmap.org
```

### 🔹 Decoy Scan

```bash
nmap -D <decoy_ip>,ME <target>
```

### 🔹 Source Port Manipulation

```bash
nmap --source-port 443 scanme.nmap.org
```

👉 Tricks firewall into thinking traffic is HTTPS

---

## 18. Defender Perspective (Important)

To protect against scans:

* Disable ICMP if not required
* Use IDS/IPS
* Enable firewall logging
* Rate‑limit scans

---

## 19. Summary

✔ Nmap is the **foundation of hacking & defense**
✔ Host discovery comes first
✔ Banner grabbing reveals weaknesses
✔ ARP scan is king inside LAN
✔ Firewalls can be evaded if misconfigured

---

📌 **Next recommended labs**:

* Nmap vs Windows Firewall
* Scan Metasploitable 2 fully
* Wireshark + Nmap traffic analysis

If you want, I can:

* Convert this into **PDF / exam notes**
* Create **hands‑on lab steps**
* Map each scan to **real attacks**
