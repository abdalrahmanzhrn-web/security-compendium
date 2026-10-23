---
tags: [ "python", "oop", "inheritance", "constructor", "super" ]
aliases: [ "Calling Parent Init", "Method Overriding" ]
created: 2025-12-21
---

# 🛠️ Explicit Parent Initialization

> [!abstract] The Problem
> If a `child` class has its own `__init__`, the `parent` class's `__init__` will **not** run automatically. You have to "hand-shake" the parent to trigger its code.

## 1. Manual Parent Call
By calling `parent.__init__(self)`, you ensure that the logic inside the parent's constructor is executed before the child continues with its own tasks.

- 1. Manually trigger the parent's constructor
- 2. Then run child-specific logic
- --- Execution ---
- Output:
- parent
- is sum

```python title:explicit_init.py
import requests

class parent:
    def __init__(self):
        print("parent")

    def sum(self):
        print("is sum")

class child(parent):
    def __init__(self):

        parent.__init__(self)

        self.sum()

obj = child()
```

## Pro-Tip: Using `super()`

While `parent.__init__(self)` works, the more modern and flexible way to do this in Python 3 is using `super()`:

- Does the same thing, but cleaner!

```python
class child(parent):
    def __init__(self):
        super().__init__()
        self.sum()
```
