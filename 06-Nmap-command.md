# 🧭 Nmap Notes – Explained Clearly (Beginner → Pro)

---

## 1️⃣ Input & Target Selection

### `nmap -iL list.txt`

**Why**
Scan multiple targets listed in a file.

**Helps us**
Bulk scanning (IPs, domains, subnets).

**Example**

```bash
nmap -iL targets.txt
```

**Output**
Scan results for *every host* in `targets.txt`.

---

### `nmap -iR 12`

**Why**
Scan random IPs on the internet.

**Helps us**
Research, honeypot discovery, internet-wide sampling.

**Example**

```bash
nmap -iR 12
```

**Output**
12 random IPs scanned.

⚠️ **Not recommended** on corporate networks.

---

### `nmap 192.168.44.254 --exclude 192.168.44.1`

**Why**
Exclude specific hosts from scan.

**Helps us**
Avoid scanning routers, firewalls, or sensitive systems.

**Example Output**

```
Skipping host 192.168.44.1
```

---

## 2️⃣ Aggressive Scan

### `nmap -A`

**What is aggressive scan?**

`-A` enables **multiple features at once**:

✔ OS detection
✔ Version detection
✔ Script scanning (NSE)
✔ Traceroute

**Why**
Quick *full reconnaissance*.

**Example**

```bash
nmap -A 183.60.25.250 -Pn
```

**Output Includes**

* Open ports
* Service versions
* OS guess
* Traceroute hops

⚠️ **Very noisy** – easily detected by IDS/IPS.

---

## 3️⃣ Host Discovery (Ping Scans)

### `nmap -Pn <ip>`

**Why**
Skip host discovery (don’t ping).

**Helps us**
Scan hosts that **block ping**.

**Output**

```
Host is up (assumed)
```

---

### `nmap -Sn <ip>`

**Why**
Only check if host is alive (no port scan).

**Helps us**
Network inventory.

---

### Ping Techniques (Used internally or manually)

| Option | Why Used            | Meaning           |
| ------ | ------------------- | ----------------- |
| `-PS`  | Firewall evasion    | TCP SYN ping      |
| `-PA`  | Bypass stateless FW | TCP ACK ping      |
| `-PU`  | UDP allowed env     | UDP ping          |
| `-PY`  | SCTP networks       | SCTP INIT         |
| `-PE`  | Classic ping        | ICMP Echo         |
| `-PP`  | Timestamp           | ICMP Timestamp    |
| `-PM`  | Mask discovery      | ICMP Address Mask |
| `-PO`  | Protocol-based      | IP Protocol ping  |
| `-PR`  | Local LAN           | ARP ping          |

---

### Example

```bash
nmap -PS80,443 203.194.110.56
```

**Output**

```
Host is up (0.021s latency)
```

---

## 4️⃣ DNS & Traceroute

### `-R`

Force reverse DNS lookup.

### `-n`

Disable DNS lookup (faster scans).

### `--system-dns`

Use OS DNS resolver.

### `--dns-servers 8.8.8.8`

Custom DNS.

---

### `nmap --traceroute sheyians.com`

**Why**
Network path analysis.

**Output**

```
Hop 1 → Router
Hop 5 → ISP
Hop 9 → Target
```

---

## 5️⃣ Port Scanning Techniques

---

### TCP SYN Scan – `-sS`

**Why**
Stealth scan (half-open).

**Helps us**
Fast & quiet port discovery.

```bash
nmap -sS <target>
```

**Output**

```
22/tcp open ssh
```

---

### TCP Connect Scan – `-sT`

**Why**
Used when SYN scan not allowed.

**Helps us**
Works without root access.

---

### UDP Scan – `-sU`

**Why**
Find DNS, SNMP, NTP, etc.

**Output**

```
53/udp open domain
```

⚠️ Slow scan.

---

### NULL / FIN / Xmas Scans

| Command | Purpose    |
| ------- | ---------- |
| `-sN`   | NULL flags |
| `-sF`   | FIN only   |
| `-sX`   | Xmas flags |

**Why**
Firewall evasion & OS fingerprinting.

**Output**

```
open|filtered
```

---

### ACK Scan – `-sA`

**Why**
Firewall rule testing.

**Helps us**
Find **filtered vs unfiltered** ports.

---

### IP Protocol Scan – `-sO`

**Why**
Discover supported IP protocols.

**Output**

```
1 open icmp
6 open tcp
17 open udp
```

---

## 6️⃣ Port Selection

### `-F`

Fast scan (top 100 ports).

### `-p 22,80`

Specific ports.

### `-p 1-1000`

Port range.

### `--top-ports 30`

Most common ports.

### `-r`

Scan ports sequentially (not random).

---

### Port States

| State    | Meaning           |                  |
| -------- | ----------------- | ---------------- |
| open     | Service running   |                  |
| closed   | No service        |                  |
| filtered | Firewall blocking |                  |
| open     | filtered          | Cannot determine |

---

## 7️⃣ Service & Version Detection

### `-sV`

**Why**
Detect service & version.

```bash
nmap -sV <target>
```

**Output**

```
80/tcp open http Apache httpd 2.4.41
```

---

### Version Intensity

| Option                    | Purpose          |
| ------------------------- | ---------------- |
| `--version-light`         | Fast             |
| `--version-all`           | Very detailed    |
| `--version-intensity 0-9` | Control accuracy |

---

### Banner Grabbing vs Active Probing

* **Banner grabbing** → Reads service greeting
* **Active probing** → Sends crafted requests

⚠️ May cause **false positives**.

---

## 8️⃣ OS Detection

### `nmap -O <target>`

**Why**
Identify operating system.

**Output**

```
Running: Linux 5.x
```

---

### Advanced OS Options

| Option           | Use                 |
| ---------------- | ------------------- |
| `--osscan-limit` | Only likely targets |
| `--osscan-guess` | Aggressive guessing |
| `--fuzzy`        | Similar OS match    |

---

### Combo Scan (Real-world Recon)

```bash
nmap -sS -O -sV -A --reason <target>
```

**This gives**
✔ Open ports
✔ Services
✔ Versions
✔ OS
✔ Scan reason
✔ Scripts

---

## 9️⃣ TCP Flags Meaning (Very Important)

| Flag | Meaning          |
| ---- | ---------------- |
| SYN  | Start connection |
| ACK  | Acknowledge      |
| PSH  | Push data        |
| URG  | Urgent           |
| RST  | Reset            |
| FIN  | Finish           |

---

## 🔐 Why DevOps & Security Engineers Use Nmap

✅ Attack surface discovery
✅ Firewall validation
✅ Cloud security audits
✅ Compliance checks
✅ Pentesting labs
✅ Incident response

