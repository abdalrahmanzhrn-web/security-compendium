This note explains how to store logic and the difference between "Global" and "Local" variables.

---
tags: [ #python, #functions, #scope ]
---

# 📦 Functions and Scope

## 1. Local vs Global Scope
Variables defined inside a function are "Local" (they die when the function ends). Variables outside are "Global".

- From IDK2.py
- This is a LOCAL variable
- To use the value from a function, you must 'return' it
- and assign it to a new variable outside.

```python
def float_holder():
    flo = 21.9
    return flo

my_val = float_holder()
print(my_val)
```

> [!tip] The Global Keyword If you want to change a variable inside a function that was created outside, you must use the `global` keyword.

```python
x = 10
def change():
    global x
    x = 20
```
