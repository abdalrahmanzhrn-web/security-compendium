---
tags: [ "python", "kali", "linux", "scripting", "basics" ]
aliases: [ "Run Python Script", "Python Hello World" ]
created: 2025-12-21
---

# 🐍 Basic Python Script Execution (Kali Linux)

> [!info] Workflow
> 1. Create file (`nano`) -> 2. Write code -> 3. Execute (`python3`).

## 1. Create the File
Use a text editor like `nano` to create your script file.

```bash title:Terminal
nano file.py
```

- ^ The line above is called the "Shebang".
- It tells Linux exactly which interpreter to use (Python 3) if you run the file directly.

```python
#!/usr/bin/python3

print("hi chito")
```

- Syntax: python3 <filename>
- Output:
- hi chito

```bash
python3 file.py
```
