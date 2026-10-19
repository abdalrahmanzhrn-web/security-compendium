---
tags: [ "python", "basics", "strings", "formatting" ]
aliases: [ "String Methods", "Text Alignment" ]
---

# 🧵 String Manipulation

## 1. Alignment and Padding
Used to create clean tables or columns in the terminal.
* `.rjust(n)`: Right-aligns the string in a field of width `n`.
* `.ljust(n)`: Left-aligns the string.

- From 99.py
- Adds spaces to the left
- Adds spaces between them

```python
print("Mussolini".rjust(20))
print("Mussolini".ljust(15) + "Hitler")
```

2. Find and Replace

- From 99.py
- .replace("old", "new")

```python
print("Good Morning".replace("Morning", "Afternoon"))
```

## 3. Joining and Case Conversion

Useful for turning lists (like a list of found usernames) into a single string for a report.

- From 88.py
- Join with a space and lowercase everything
- Join with custom symbols and uppercase

```python
mix_Cases = ("A Song of Ice and Fire", "AAA", "KKK")

result_join = " ".join(mix_Cases).lower()

print(" ,,! ".join(mix_Cases).upper())
```
