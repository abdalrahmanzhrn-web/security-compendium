---
tags: [ "metasploit", "setup", "database", "postgresql", "workflow" ]
aliases: [ "Start MSF", "Metasploit Setup" ]
created: 2025-12-21
---

# 🏁 Metasploit Initialization Routine

> [!warning] Database Criticality
> You must start the database **before** launching `msfconsole`. If you skip this, `db_nmap` will not work, and you cannot save your workspaces or loot.

## 1. Service Status Check
Ensure the backend database service is running on the OS level.

- 1. Check PostgreSQL (The database engine)
- 2. Check MSFDB (The Metasploit schema)
- If they are not running:
- sudo service postgresql start
- sudo msfdb init (only needed once ever)
- Start the interface
- Inside the console, check connection status:
- Syntax: db_connect <user>:<pass>@<host>/<db_name>

```bash title:Check_Services
service postgresql status

msfdb status

msfconsole

db_status

db_connect msf:msf@127.0.0.1/msf
```
