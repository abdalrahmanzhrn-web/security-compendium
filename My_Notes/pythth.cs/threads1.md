---
tags: [ "python", "threading", "concurrency", "optimization", "scripting" ]
aliases: [ "Multi-Threading", "Python Threads" ]
created: 2025-12-21
---

# 🧵 Multi-Threading (Concurrency)

> [!info] Why use this?
> **Speed.** Instead of waiting for one task to finish before starting the next (Sequential), you run multiple tasks at the exact same time (Parallel/Concurrent).
> * **Example:** Cracking 4 passwords at once instead of 1.

## 1. The Setup
You define a function that you want to run multiple times simultaneously.

- os.getpid() gets the "Process ID".
- Since threads live INSIDE a process, this ID will be the SAME for all of them.
- 2. Define the Threads
- 'target' tells the thread which function to run.
- Defined but not started below
- 3. Start the Threads
- The moment you hit .start(), the code runs in the background.

```python title:threading_example.py
#!/usr/bin/python3
import threading
import time
import os

def test():

    print(f"PID: {os.getpid()} | Time: {time.ctime()}")

thread1 = threading.Thread(target=test)
thread2 = threading.Thread(target=test)
thread3 = threading.Thread(target=test)
thread4 = threading.Thread(target=test)

thread1.start()
thread2.start()
thread3.start()
```

## 2. Output Analysis

When you run this, you will see three lines appear almost instantly.

PID: 1337 | Time: Sun Dec 21 07:45:00 2025
PID: 1337 | Time: Sun Dec 21 07:45:00 2025
PID: 1337 | Time: Sun Dec 21 07:45:00 2025
