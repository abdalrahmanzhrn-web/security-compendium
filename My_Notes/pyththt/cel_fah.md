---
tags: [ "python", "project", "math", "logic", "basics" ]
aliases: [ "Temperature Converter" ]
created: 2025-12-21
---

# 🌡️ Project: Temperature Converter

> [!info] Logic
> This project uses the standard conversion formulas:
> * **To Fahrenheit:** $F = (C \times 9/5) + 32$
> * **To Celsius:** $C = (F - 32) \times 5/9$

## 1. The Code Implementation
This script asks the user which direction they want to convert and then performs the math.

- Formula: (C * 1.8) + 32
- Formula: (F - 32) / 1.8
- Run the project

```python title:temp_calc.py
def converter():
    print("--- Temperature Converter ---")
    print("1. Celsius to Fahrenheit")
    print("2. Fahrenheit to Celsius")

    choice = input("Choose (1 or 2): ")

    if choice == "1":
        celsius = float(input("Enter degrees in Celsius: "))

        fahrenheit = (celsius * 9/5) + 32
        print(f"{celsius}°C is equal to {fahrenheit}°F")

    elif choice == "2":
        fahrenheit = float(input("Enter degrees in Fahrenheit: "))

        celsius = (fahrenheit - 32) * 5/9
        print(f"{fahrenheit}°F is equal to {celsius}°C")

    else:
        print("Invalid choice! Please run the script again.")

if __name__ == "__main__":
    converter()
```
