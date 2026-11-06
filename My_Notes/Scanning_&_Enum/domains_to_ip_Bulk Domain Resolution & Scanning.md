---
tags: [ "dns", "recon", "masscan", "dig", "scripting", "active-recon" ]
aliases: [ "Bulk DNS Resolution", "Domain to IP" ]
created: 2025-12-21
---

# 🌐 Bulk Domain Resolution & Scanning

> [!info] Workflow Goal
> Convert a list of domain names (`domains.txt`) into IP addresses, then immediately scan those IPs for open ports.

## 1. Basic Resolution (Dig)
Best for smaller lists or when accuracy is prioritized over speed.

- Syntax: dig -f <domain_list> +short >> <output_file>
- -p80 : Scan Port 80
- -iL  : Input List (the text file of IPs)

```bash title:Dig_Loop
dig -f domains.txt +short >> ip_address.txt

masscan -p80 -iL ip_address.txt
nmap -iL sybdomains.txt -o result.txt
```

hostname:targetcompany.com -port:80,443

**platacard.mx**

hostname:platacard.mx -port:80,443

hostname:platacard.mx

```bash
dig platacard.mx +short
```
