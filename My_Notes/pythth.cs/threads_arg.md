---
tags: [ "python", "threading", "arguments", "scripting", "syntax" ]
aliases: [ "Thread Arguments", "Passing Variables to Threads" ]
created: 2025-12-21
---

# 🧵 Threading with Arguments

> [!warning] The Comma Trap
> When passing arguments to a thread, the `args` parameter **must be a tuple**.
> * **Wrong:** `args=("tabby")` -> Python thinks this is just a string in parenthesis.
> * **Right:** `args=("tabby",)` -> The comma tells Python "This is a tuple with one item."

## 1. The Code Structure
You can pass data (variables) into your threaded function using the `args` parameter.

- 1. The Function (Expects input)
- 2. The Data
- 3. Thread Definition
- 4. Execution
- Wait for it to finish

```python title:threading_args.py
import threading
import time

def test_name(name):
    print(f"Hello mister chi {name}")

yourname_is = "tabby"

thread1 = threading.Thread(target=test_name, args=(yourname_is,))

thread1.start()
thread1.join()
```

## 2. Why is this useful?

In a real cyber tool, you wouldn't pass a name like "tabby". You would pass targets:

- Real World Example:
- threading.Thread(target=scan_ip, args=("192.168.1.55",))
- threading.Thread(target=crack_file, args=("passwords.txt",))
