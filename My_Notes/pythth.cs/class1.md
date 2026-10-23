---
tags: [ "python", "oop", "constructor", "destructor", "memory-management" ]
aliases: [ "Object Lifecycle", "Init and Del" ]
created: 2025-12-21
---

# 🔄 Object Lifecycle: Constructor vs. Destructor

## 1. The Magic Methods
In Python, "Dunder" (Double Underline) methods like `__init__` and `__del__` are called automatically by the interpreter.

* **`__init__` (The Constructor):** Runs when the object is **created**.
* **`__del__` (The Destructor):** Runs when the object is **deleted** or the script finishes.

## 2. Implementation

- Triggered by: obj = new()
- Triggered when: The script ends OR 'del obj' is called
- 1. Object is created -> Prints "Hello"
- 2. Script reaches the end -> Object is destroyed -> Prints "Bye"

```python title:lifecycle.py
import requests

class new():
    def __init__(self):

        print("Hello")

    def __del__(self):

        print("Bye")

obj = new()
```

## 📝 Cyber Use Case: Cleanup

In exploitation or networking scripts, we use these to ensure we don't leave "ghost" connections open:

- **`__init__`**: Open a socket or a database connection.

- **`__del__`**: Safely close the socket or file handles so the target system doesn't stay locked or alerted.
