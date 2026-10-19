---
tags: [ "python", "logic", "loops", "random" ]
---

# 🧠 Control Flow & Randomization

## 1. Conditional Logic (If/Elif/Else)
Python uses indentation to define what code belongs to which logic block.

- Combined from 44.py, 33.py, 22.py
- Nested Logic (The GPA Check)

```python
score = int(input("Enter score:"))

if score >= 90:
    print("Grade: A")
elif score >= 80:
    print("Grade: B")
else:
    print("Grade: F")

if gpa >= 3.7:
    if app_instit == "yes":
        print("Qualifies for Loan")
```

---

## 2. Random Generation

Essential for simulations or generating random ports/IDs.

- From 55.py and IDk.py
- Generate a random integer between two numbers (inclusive)
- Example: Calculating MPG with random tank sizes

```python
import random

val = random.randint(1, 10)

gallons = random.randint(10, 25)
miles = random.randint(200, 400)
print(f"Miles per gallon: {miles // gallons}")
```

---

## 3. Looping and Counting

- From 66.py and 77.py
- Loop through every character
- Manual Counter (Len simulation)
- Increment

```python
FF = "Hello World"

for letter in FF:
    print(letter)

counter = 0
for char in "Cyber":
    counter += 1
```
