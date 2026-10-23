---
tags: [ "python", "oop", "methods", "automation" ]
aliases: [ "Internal Method Calls", "Self Reference" ]
created: 2025-12-21
---

# 🔗 Internal Class Logic (Self-Calling)

> [!info] The `self` Keyword
> Think of `self` as a pointer. Inside a class, you can't just call `sum()`; the computer won't know where it is. You must use `self.sum()` to say "run the sum function that belongs to **this** specific object."

## 1. Auto-Triggering Functions
In this pattern, the `__init__` method acts as a "Launchpad."

- 1. Runs first when 'obj = new()' is called
- 2. Immediately tells the object to look for its own 'sum' method
- 3. Executes the logic
- --- Execution ---
- Output:
- Hello
- 146

```python title:internal_call.py
class new():
    def __init__(self):

        print("Hello")

        self.sum()

    def sum(self):

        print(56 + 90)

obj = new()
```

## 📝 Why use this?

In a cyber-scripting context (like an **exploit** or **scanner**):

- `__init__` might set the target IP and port.

- `self.check_connection()` is called within `__init__` to make sure the target is alive before the script even starts the main attack.
