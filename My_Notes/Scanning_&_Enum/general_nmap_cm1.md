---
tags: [ "nmap", "metasploit", "recon", "active-recon", "scanning" ]
aliases: [ "Nmap Strategies", "db_nmap usage" ]
created: 2025-12-21
---

# 🕵️ Nmap & MSF Scanning Routines

> [!tip] Integration
> Using `db_nmap` inside Metasploit automatically saves results to the backend database. All standard Nmap flags work here.

## 1. Basic & Stealth Scans
Standard discovery scans. The "Stealth" scan (`-sS`) is the default when running as root/admin.

- 1. Stealth Scan (SYN Scan) - Default
- Does not complete the 3-way handshake, harder to log.
- 2. Top Ports Scan
- Scans the 100 most common ports (fast overview).
- 3. Specific Port List
- Targeted scan for critical services.
- -sV : Probes open ports to determine service/version info
- Scanning range 1-1000

```bash title:Common_Scans
secret: nmap -Pn -sSV -O -A  177.191.19.217

db_nmap -sS <target_ip>

db_nmap --top-ports 100 10.0.2.5

db_nmap -p 21,22,80,443 10.0.2.5

db_nmap -sV -p 1-1000 10.0.2.5
```

## Database Verification

After scanning, use the `services` command to query the Metasploit database without re-scanning.

```bash title:Common_Scans
services -p 21

services --top-ports 100
```

```bash
nmap -sT -Pn -n \
  -p 21,22,23,25,53,80,110,135,139,143,443,445,993,995,1723,3306,3389,5900,8080,8443,1433,1521,5432,6379,27017,9200,9300,11211,5000,8000,9000,9090,500,4500,1701,1194,1723,3389,5800,5900,6000,6660-6669,7777,8888,9999,10000,20000,30000,2375,6443,8082,5601,8089,8500,51820,2222 \
  -T2 --max-retries 1 --min-rate 50 --max-rtt-timeout 300ms --host-timeout 15m --open \
  -oG silent_scan2.gnmap 187.234.65.44
```

```bash
tail -f silent_scan.gnmap
```

Nice And slow Nmap:

Here is your **dead‑silent, targeted scan strategy**.

---

## PORT LIST BREAKDOWN

I have separated your ports into **TCP** (services) and **UDP** (noisy, optional). **Skip UDP unless absolutely necessary** – UDP scans trigger lots of ICMP unreachable replies, which are loud.

|Type|Ports (from your list)|
|---|---|
|**TCP**|`21, 22, 23, 80, 111, 443, 541, 554, 1701, 1935, 2000, 4449, 5432, 8025, 8081, 8443, 8889, 37777, 50000`|
|**UDP**|`53, 123, 161`|

---

## SCAN COMMAND (TCP – QUIET)

Run this on **each IP** individually. It will **not** probe for open ports (we already know them). It will only grab banners and run safe version scripts on those exact ports.

```bash
nmap -sS -sV -sC -p T:21,22,23,80,111,443,541,554,1701,1935,2000,4449,5432,8025,8081,8443,8889,37777,50000 -T2 --scan-delay 1s --max-rtt-timeout 1500ms -Pn -n --open [TARGET_IP] -oA quiet_tcp_scan
```

**Flags explained (stealth focus):**

|Flag|Why it's quiet|
|---|---|
|`-sS`|SYN scan – doesn't complete the TCP handshake (stealthier than `-sT`).|
|`-Pn`|**Skips host discovery** (no ICMP echo/ping) – prevents "ping sweep" alerts.|
|`-n`|No DNS resolution – avoids DNS queries to internal DNS servers.|
|`-T2`|Polite timing – slower packets, less likely to trigger IDS.|
|`--scan-delay 1s`|Adds 1 second delay between probes – extremely slow, virtually invisible.|
|`--max-rtt-timeout 1500ms`|Drops slow/unresponsive ports quickly – no hanging probes.|
|`--open`|Only shows results – hides filtered/closed ports (cleaner output).|

---

## UDP SCAN (OPTIONAL – LOUDER)

UDP scans are inherently noisy. **Only run this if you really need SNMP (161) or DNS (53).** If you do, run it **separately and slowly**.

```bash
sudo nmap -sU -sV -p U:53,123,161 -T2 --scan-delay 2s -Pn -n [TARGET_IP] -oA quiet_udp_scan
```

_(Requires `sudo` for raw UDP packets)._

Quit port scan:

```bash
nmap -p 5432 -sV --version-light -T2 --max-rtt-timeout 1000ms -Pn -n [TARGET_IP]
```
