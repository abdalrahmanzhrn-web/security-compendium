---
tags: [ "ftp", "apache", "smb", "tomcat", "cve", "vulnerability-analysis", "mindset" ]
aliases: [ "Service Exploitation Logic", "Version Analysis" ]
created: 2025-12-21
---

# 🧠 Service Analysis & Attack Logic

> [!example] The Hacker Mindset
> Scanning is useless if you don't know what the results *mean*. This note maps specific service versions to their likely vulnerabilities.

## 1. FTP (Port 21)
First, try the low-hanging fruit (Anonymous login) before moving to brute force.

- 1. Manual Check (Anonymous Login)
- User: anonymous
- Pass: anonymous
- 2. Brute Force (Hydra)
- Syntax: hydra -l <user> -P <passlist> ftp://<IP>

```bash title:FTP_Workflow
ftp 10.10.10.1

hydra -l admin -P /usr/share/wordlists/rockyou.txt ftp://10.10.10.1
```

| **Service / Version** | **Threat Indicator** | **Likely Attack Vector**                                                    |
| --------------------- | -------------------- | --------------------------------------------------------------------------- |
| **Apache 2.2.x**      | Old AF.              | Likely running PHP 5 in CGI mode. Check for **PHP CGI Argument Injection**. |
| **SMB v1**            | Legacy Protocol.     | Highly vulnerable. Check **EternalBlue (MS17-010)** or **MS08-067**.        |
| **AJP (Port 8009)**   | Tomcat Connector.    | **Ghostcat (CVE-2020-1938)** (File Read/RCE) if config is default.          |
Known CVEs for specific legacy versions found in the wild (or CTFs).

**A. Apache HTTPD 2.2.8**

- **Vuln:** PHP CGI Argument Injection

- **CVE:** `CVE-2012-1823`

- **MSF Note:** When exploiting, you may need to set `LPORT 4480` to avoid conflicts.

**B. Apache Tomcat / Coyote 1.1**

- **Vuln:** Application Server Exploit

- **Target:** Often vulnerable to the **Axis2 Deployer** exploit.

- **Action:** Check `/axis2/services` endpoint.
