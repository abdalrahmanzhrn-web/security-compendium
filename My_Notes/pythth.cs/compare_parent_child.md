---
tags: [ "python", "oop", "inheritance", "classes", "basics" ]
aliases: [ "Class Inheritance", "Python Init" ]
created: 2025-12-21
---

# 🧬 Python OOP: Inheritance & Init

## 1. Basic Inheritance
When a `child` class inherits from a `parent`, it gains access to all the parent's functions automatically.

- 'child' inherits from 'parent'
- Even though 'child' is empty (pass), it can run sum()
- Output: parent and this is sum

```python title:basic_inheritance.py
class parent:
    def sum(self):
        print("parent and this is sum")

class child(parent):
    pass

obj = child()
obj.sum()
```

## 2. Auto-Execution with `__init__`

The `__init__` method is a "magic" function. It runs **automatically** the moment you create an object (`obj = child()`). You don't need to call the functions manually if they are inside `__init__`.

- Auto-calls sum during setup
- The moment this line runs, the prints happen!
- Output:
- parent initialized
- parent and this is sum

```python
class parent:
    def __init__(self):
        print("parent initialized")
        self.sum()

    def sum(self):
        print("parent and this is sum")

class child(parent):
    pass

obj = child()
```
