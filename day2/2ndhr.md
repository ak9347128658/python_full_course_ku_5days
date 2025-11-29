# Day 2 - Hour 2: Loops (For and While)

## Welcome to Hour 2!

Yesterday you learned to make decisions. Today you'll learn to **repeat code** - the power of loops! Loops are one of the most important programming concepts. They save you from writing the same code over and over.

Imagine you need to print numbers 1 to 1000. Would you write `print(1)` 1000 times? No! You use a loop.

---

## What is a Loop?

A **loop** is code that repeats multiple times. Each repetition is called an **iteration**.

```python
# Without loop - repetitive and terrible
print(1)
print(2)
print(3)
print(4)
print(5)

# With loop - elegant and powerful
for i in range(1, 6):
    print(i)
```

---

## The `for` Loop

The `for` loop iterates over a sequence (list, range, string, etc.).

### Syntax

```python
for variable in sequence:
    # Code here runs for each item in sequence
    print(variable)
```

### Example 1: Counting with `range()`

```python
for i in range(5):
    print(i)

# Output:
# 0
# 1
# 2
# 3
# 4
```

**Important**: `range(5)` means 0, 1, 2, 3, 4 (ends at 4, not 5!)

### Example 2: Counting from Start to End

```python
for i in range(1, 6):
    print(i)

# Output:
# 1
# 2
# 3
# 4
# 5
```

`range(1, 6)` means start at 1, end before 6.

### Example 3: Counting with Steps

```python
for i in range(0, 10, 2):
    print(i)

# Output:
# 0
# 2
# 4
# 6
# 8
```

`range(start, end, step)` - each iteration adds `step` to the variable.

### Example 4: Counting Backwards

```python
for i in range(5, 0, -1):
    print(i)

# Output:
# 5
# 4
# 3
# 2
# 1
```

### Example 5: Looping Through a List

```python
fruits = ["apple", "banana", "orange"]

for fruit in fruits:
    print(fruit)

# Output:
# apple
# banana
# orange
```

### Example 6: Looping Through a String

```python
word = "Python"

for letter in word:
    print(letter)

# Output:
# P
# y
# t
# h
# o
# n
```

---

## The `while` Loop

A `while` loop repeats as long as a condition is True.

### Syntax

```python
while condition:
    # Code runs while condition is True
    print("Still looping!")
```

### Example 1: Simple While Loop

```python
count = 0

while count < 5:
    print(count)
    count += 1

# Output:
# 0
# 1
# 2
# 3
# 4
```

**Important**: You must change the variable inside the loop, or it runs forever!

### Example 2: Input Validation

```python
age = -1

while age < 0:
    age = int(input("Enter your age (must be 0 or more): "))

print(f"Your age is {age}")
```

This keeps asking for input until the user enters a valid age.

### Example 3: Countdown

```python
countdown = 10

while countdown > 0:
    print(countdown)
    countdown -= 1

print("Blastoff!")

# Output:
# 10
# 9
# 8
# ...
# 1
# Blastoff!
```

### Example 4: Password Check

```python
password = "secret123"
guess = ""

while guess != password:
    guess = input("Enter password: ")

print("Access granted!")
```

---

## `for` vs `while` - When to Use Each?

### Use `for` when you know how many times to loop:

```python
# Loop exactly 5 times
for i in range(5):
    print(i)

# Loop through a known list
for fruit in ["apple", "banana", "orange"]:
    print(fruit)
```

### Use `while` when you loop based on a condition:

```python
# Loop until user enters valid input
while True:
    age = int(input("Age: "))
    if age >= 0:
        break

# Loop while something is true
while user_still_playing:
    # Play game
    user_choice = input("Continue? (yes/no): ")
    if user_choice == "no":
        user_still_playing = False
```

---

## Loop Patterns and Techniques

### Pattern 1: Accumulator (Adding Values)

```python
total = 0

for i in range(1, 6):
    total += i
    print(f"Sum so far: {total}")

# Output:
# Sum so far: 1
# Sum so far: 3
# Sum so far: 6
# Sum so far: 10
# Sum so far: 15
```

### Pattern 2: Counter

```python
count = 0

for i in range(10):
    if i % 2 == 0:
        count += 1

print(f"Even numbers: {count}")
# Output: Even numbers: 5
```

### Pattern 3: Building a String

```python
message = ""

for letter in "Python":
    message += letter
    print(message)

# Output:
# P
# Py
# Pyt
# Pyth
# Pytho
# Python
```

---

## Real-World Examples

### Example 1: Multiplication Table

```python
number = 7

print(f"Multiplication table for {number}:")

for i in range(1, 11):
    result = number * i
    print(f"{number} x {i} = {result}")

# Output:
# Multiplication table for 7:
# 7 x 1 = 7
# 7 x 2 = 14
# ...
# 7 x 10 = 70
```

### Example 2: Calculate Average

```python
total = 0
count = 0

for score in [85, 90, 78, 92, 88]:
    total += score
    count += 1

average = total / count
print(f"Average score: {average:.2f}")
# Output: Average score: 86.60
```

### Example 3: Find Largest Number

```python
numbers = [45, 23, 89, 12, 76, 34]
largest = numbers[0]

for num in numbers:
    if num > largest:
        largest = num

print(f"Largest number: {largest}")
# Output: Largest number: 89
```

### Example 4: Print Patterns

```python
# Triangle
for i in range(1, 6):
    print("*" * i)

# Output:
# *
# **
# ***
# ****
# *****

# Square
for i in range(5):
    print("*" * 5)

# Output:
# *****
# *****
# *****
# *****
# *****
```

---

## Project 1: Number Guessing Game with Loop

```python
import random

secret = random.randint(1, 100)
guess = 0
attempts = 0

print("=== NUMBER GUESSING GAME ===")
print("Guess a number between 1 and 100\n")

while guess != secret:
    guess = int(input("Your guess: "))
    attempts += 1
    
    if guess < secret:
        print("Too low!")
    elif guess > secret:
        print("Too high!")
    else:
        print(f"Correct! You guessed in {attempts} attempts!")
```

---

## Project 2: Simple Bank Account

```python
balance = 1000
pin = "1234"

pin_input = input("Enter PIN: ")

if pin_input == pin:
    while True:
        print(f"\nBalance: ${balance}")
        choice = input("1. Withdraw 2. Deposit 3. Exit: ")
        
        if choice == "1":
            amount = float(input("Withdraw amount: $"))
            if amount <= balance:
                balance -= amount
                print(f"Withdrawn: ${amount}")
            else:
                print("Insufficient funds")
        
        elif choice == "2":
            amount = float(input("Deposit amount: $"))
            balance += amount
            print(f"Deposited: ${amount}")
        
        elif choice == "3":
            print("Thank you!")
            break
else:
    print("Wrong PIN!")
```

---

## Exercises

### Exercise 1: Print 1-20

Create `loop1.py`:

```python
# Print numbers 1 to 20
for i in range(1, 21):
    print(i)
```

### Exercise 2: Even Numbers

Create `loop2.py`:

```python
# Print even numbers from 0 to 20
for i in range(0, 21, 2):
    print(i)
```

### Exercise 3: Sum of Numbers

Create `loop3.py`:

```python
# Calculate sum of 1 to 100
total = 0
for i in range(1, 101):
    total += i

print(f"Sum of 1 to 100: {total}")
```

### Exercise 4: Factorial

Create `loop4.py`:

```python
# Calculate factorial of 5 (5! = 5 * 4 * 3 * 2 * 1)
number = 5
factorial = 1

for i in range(1, number + 1):
    factorial *= i

print(f"{number}! = {factorial}")
```

### Exercise 5: Times Table

Create `loop5.py`:

```python
# Print times table for any number (using user input)
num = int(input("Enter a number: "))

for i in range(1, 11):
    print(f"{num} x {i} = {num * i}")
```

---

## Common Mistakes

```python
# ✗ WRONG - Infinite loop (missing increment)
count = 0
while count < 5:
    print(count)
    # count never increases!

# ✓ CORRECT
count = 0
while count < 5:
    print(count)
    count += 1

# ✗ WRONG - Off-by-one error
for i in range(5):
    print(i)  # Prints 0-4, not 1-5

# ✓ CORRECT - If you want 1-5
for i in range(1, 6):
    print(i)

# ✗ WRONG - Indentation error
for i in range(3):
print(i)  # IndentationError!

# ✓ CORRECT
for i in range(3):
    print(i)
```

---

## Key Takeaways

✓ `for` loops iterate a known number of times or through sequences  
✓ `while` loops run while a condition is True  
✓ `range(n)` creates numbers 0 to n-1  
✓ `range(start, end, step)` creates custom sequences  
✓ Use accumulator pattern to sum values  
✓ Always increment `while` loop variables to avoid infinite loops  
✓ Use `for` when you know iterations, `while` for conditions  

---

## Quick Reference

```python
# For loop with range
for i in range(5):          # 0 to 4
    print(i)

for i in range(1, 6):       # 1 to 5
    print(i)

for i in range(0, 10, 2):   # 0, 2, 4, 6, 8
    print(i)

# For loop with sequence
for item in [1, 2, 3]:
    print(item)

# While loop
count = 0
while count < 5:
    print(count)
    count += 1

# Accumulator pattern
total = 0
for i in range(1, 6):
    total += i
```

---

## Homework

1. ✓ Print multiplication tables for 1-10
2. ✓ Calculate sum and average of 10 numbers
3. ✓ Create a star pyramid pattern
4. ✓ Create a guessing game where user has 5 attempts

Next hour: **Loop Control & Patterns!**
