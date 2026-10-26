---
tags: [ "python", "os-module", "system-admin", "recon", "linux" ]
aliases: [ "System Check", "os.system" ]
created: 2025-12-21
---

# 🖥️ System Enumeration (os.system)

> [!info] The Bridge
> `os.system()` allows your Python script to "talk" to the Linux terminal. It executes Bash commands as if you typed them yourself.

## 1. The Script
This script gathers Network, Memory, and Disk information in one go.

- 1. Network Config
- Shows IP addresses, MAC addresses, and active interfaces.
- 2. Memory Usage
- Shows RAM usage (Used vs Free).
- 3. Disk Usage
- Shows hard drive space.
- '-h' flag means "Human Readable" (GB/MB instead of bytes).

```python title:device_info.py
#!/usr/bin/python3
import os

print("--- NETWORK ---")
os.system("ifconfig")

print("\n--- MEMORY ---")
os.system("free")

print("\n--- DISK ---")
os.system("df -h")
```

## 2. Why Hackers Use This

When you land a shell on a victim machine, you often drop a "survey script" like this first. It tells you:

1. **IP:** Are we dual-homed? (Can we pivot to another network?)

2. **RAM:** Is this a tiny VM (Honey Pot) or a real server?

3. **Disk:** Is there enough space to download our loot/exfiltration tools?
