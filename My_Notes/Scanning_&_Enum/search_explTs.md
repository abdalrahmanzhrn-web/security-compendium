---
tags: [ "cve", "osint", "exploit-db", "metasploit", "vulnerability-analysis" ]
aliases: [ "CVE Research", "Exploit Search" ]
created: 2025-12-21
---

# 🌍 Vulnerability Research & OSINT

> [!info] Methodology
> Once you identify a service and version (from Nmap), the next step is to check if it has known vulnerabilities (CVEs) or public exploits.

## 1. External Databases (Internet)
Use these resources to find CVE numbers associated with specific software versions.

* **CVEDetails.com:**
    * **Action:** Search for the Service Name (e.g., "Apache 2.4.49").
    * **Goal:** Find specific CVE IDs (e.g., `CVE-2021-41773`).
* **Port Research:**
    * **Query:** "What is port `[number]` used for?"
    * **Goal:** Understand non-standard ports or verify service behavior.

## 2. Metasploit Search (Internal)
Once you have a Service Name or CVE ID, search inside Metasploit for a matching module.

- 1. Search by CVE ID
- 2. Advanced Search (Filter by Type and Platform)
- Syntax: search <service> type:exploit platform:<os>
- 3. Check Vulnerabilities on Target (if plugins loaded)

```bash title:MSF_Search
search cve-2017-0144

search smb type:exploit platform:windows

vulns -p <port> <target_ip>
```

## General Google Dorks

Useful for finding manual exploit code if not in Metasploit.

- `site:exploit-db.com "service name"`
    
- `"service version" exploit github`
