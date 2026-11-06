---
tags: [ "masscan", "recon", "active-recon", "scanning", "fast-scan" ]
aliases: [ "Masscan Cheat Sheet", "High Speed Scanning" ]
created: 2025-12-21
---

# 🚀 Masscan: High-Speed Port Scanner

> [!danger] Bandwidth Warning
> Masscan has its own TCP stack and can transmit packets faster than your router can handle.
> * Always use the `--rate` flag to throttle speed.
> * Scanning `0.0.0.0/0` (The Internet) requires significant bandwidth and authorization.

## 1. Basic Scanning
Masscan syntax is similar to Nmap but limited to SYN scans.

- Single Target (Port 80)
- Subnet Scan (Port 22)

```bash title:Basic_Targets
masscan -p80 192.168.1.1

masscan -p22 192.168.1.0/24
```

## Multi-Port & CIDR Ranges

Scanning larger networks for multiple services.

Multiple Ports (HTTP, HTTPS, Proxy):

- Rate Limit (Packets Per Second)
- Example: 10,000 pps
- Output to XML (Standard format for import into other tools)
- Exclude specific IPs from a range scan
- ⚠️ THE INTERNET SCAN ⚠️
- Scans the entire IPv4 address space.
- --rate=1000000 requires 1-10 Gbit uplink.

```bash title:Basic_Targets
masscan -p80,443,8080 192.168.1.0/24

Large CIDR Range (Class B):
masscan -p80 192.168.0.0/16

masscan -p80 192.168.1.0/24 --rate=10000

masscan -p80 192.168.1.0/24 -oX results.xml

masscan -p80 192.168.0.0/16 --exclude 192.168.1.1,192.168.2.1

masscan -p80 0.0.0.0/0 --rate=1000000 --exclude 255.255.255.255
```

```bash
masscan -p1-65535 --rate=1000 --open-only -oG masscan_all2.gnmap 187.234.65.44
```
