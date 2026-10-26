---
tags: [ "python", "os-module", "automation", "nmap", "scripting" ]
aliases: [ "Command Wrapper", "Python Nmap Launcher" ]
created: 2025-12-21
---

# 🐚 Executing System Commands (Wrappers)

> [!info] The Wrapper Concept
> A "Wrapper" is a script that runs another tool for you. This allows you to chain tools together (e.g., Run Nmap -> Save Output -> Run Searchsploit).

## 1. Basic Execution
The `os.system()` function takes a string and executes it exactly as if you typed it into the terminal.

- List files in current directory
- Check network interfaces

```python title:Basic_Cmd
import os

os.system("ls")

os.system("ifconfig")
```

## 2. The Nmap Wrapper (Interactive)

This script combines **User Input** with **Command Execution**.

- 1. Show current IP so you know your own interface
- 2. Get the target from the user
- 3. Construct and run the command
- The 'f' string (f"...") allows us to inject the 'target' variable directly.

```python
#!/usr/bin/python3
import os

os.system("ifconfig")

target = input("Enter a target's IP address: ")

os.system(f"nmap {target}")
```

[!danger] Security Note: Command Injection Be careful with `input()` inside `os.system()`.

- If a user types `127.0.0.1; rm -rf /`, your script will scan localhost and then **delete your file system**.

- In professional tools, we sanitize inputs to prevent this.
