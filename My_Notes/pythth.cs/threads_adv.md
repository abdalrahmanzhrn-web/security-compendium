---
tags: [ "python", "threading", "automation", "scalability", "coding-patterns" ]
aliases: [ "Dynamic Threading", "Thread Loops" ]
created: 2025-12-21
---

# 🧵 Advanced Threading (Scalable Loops)

> [!info] The Upgrade
> Instead of manually creating variables (`t1`, `t2`...), we use a **List** and a **Loop**. This allows us to spawn 10, 50, or 1000 threads just by changing one number.

## 1. The Setup (Dynamic List)
We create an empty list `threads = []` to hold our workers, then use a loop to fill it.

- Change this to 50 to go faster!
- 1. Creation Loop
- Create the thread objects and add them to the list
- 2. Execution Loop

```python title:thread_adv.py
import threading

def loop1():
    for i in range(1000):
        print(i)

if __name__ == "__main__":
    threads = []
    threadnum = 10

    for i in range(threadnum):
        thread = threading.Thread(target=loop1)
        threads.append(thread)

    for i in threads:
        i.start()
        i.join()
```

- Loop A: START everyone first (Don't wait!)
- Loop B: Then WAIT for everyone

```python
    for i in threads:
        i.start()

    for i in threads:
        i.join()
```
