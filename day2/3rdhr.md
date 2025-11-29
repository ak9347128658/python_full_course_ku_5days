# Day 2 - Hour 3: Loop Control & Patterns

## Welcome to Hour 3!

You've mastered basic loops! Now we're learning **loop control** - how to break out of loops, skip iterations, and handle special cases. This is where loops become truly powerful!

---

## Loop Control Statements

### `break` - Exit the Loop Immediately

The `break` statement exits the loop completely.

```python
for i in range(10):
    if i == 5:
        break
    print(i)

# Output:
# 0
# 1
# 2
# 3
# 4
```

When `i == 5`, the loop breaks and no more iterations happen.

### Real Example: Search and Stop

```python
fruits = ["apple", "banana", "orange", "grape", "mango"]
target = "orange"

for fruit in fruits:
    print(f"Checking: {fruit}")
    if fruit == target:
        print(f"Found {target}!")
        break

# Output:
# Checking: apple
# Checking: banana
# Checking: orange
# Found orange!
```

### While Loop with Break

```python
password = "secret123"

while True:
    guess = input("Enter password: ")
    if guess == password:
        print("Access granted!")
        break
    else:
        print("Wrong password, try again")
```

---

## `continue` - Skip to Next Iteration

The `continue` statement skips the current iteration and goes to the next one.

```python
for i in range(5):
    if i == 2:
        continue
    print(i)

# Output:
# 0
# 1
# 3
# 4
```

When `i == 2`, `continue` skips printing and goes to the next iteration.

### Real Example: Skip Even Numbers

```python
for i in range(1, 11):
    if i % 2 == 0:
        continue
    print(i)

# Output: (only odd numbers)
# 1
# 3
# 5
# 7
# 9
```

### Real Example: Data Filtering

```python
scores = [85, 0, 92, 0, 78, 0, 88]

print("Valid scores:")
for score in scores:
    if score == 0:
        continue
    print(score)

# Output:
# Valid scores:
# 85
# 92
# 78
# 88
```

---

## `pass` - Do Nothing

The `pass` statement is a placeholder - it does nothing. Useful when you need syntax but have no code yet.

```python
for i in range(5):
    if i == 2:
        pass  # Do nothing when i equals 2
    else:
        print(i)

# Output:
# 0
# 1
# 3
# 4
```

This is more commonly used in function/class definitions:

```python
def my_function():
    pass  # We'll implement this later

class MyClass:
    pass  # We'll implement this later
```

---

## Nested Loops

Loops inside loops! Used for multi-dimensional data.

### Simple Example

```python
for i in range(3):
    for j in range(2):
        print(f"i={i}, j={j}")

# Output:
# i=0, j=0
# i=0, j=1
# i=1, j=0
# i=1, j=1
# i=2, j=0
# i=2, j=1
```

**How it works:**
- Outer loop runs 3 times (i = 0, 1, 2)
- For each outer iteration, inner loop runs 2 times
- Total iterations: 3 × 2 = 6

### Real Example: Multiplication Table Grid

```python
print("Multiplication Table:\n")

for i in range(1, 4):
    for j in range(1, 4):
        result = i * j
        print(f"{i}×{j}={result:2}", end=" ")
    print()  # New line after each row

# Output:
# 1×1= 1 1×2= 2 1×3= 3
# 2×1= 2 2×2= 4 2×3= 6
# 3×1= 3 3×2= 6 3×3= 9
```

### Real Example: Patterns

```python
# Diamond pattern
for i in range(1, 5):
    print(" " * (4 - i) + "*" * (2 * i - 1))

for i in range(3, 0, -1):
    print(" " * (4 - i) + "*" * (2 * i - 1))

# Output:
#    *
#   ***
#  *****
# *******
#  *****
#   ***
#    *
```

### Real Example: Checkerboard

```python
for row in range(8):
    for col in range(8):
        if (row + col) % 2 == 0:
            print("□", end=" ")
        else:
            print("■", end=" ")
    print()

# Output:
# □ ■ □ ■ □ ■ □ ■
# ■ □ ■ □ ■ □ ■ □
# □ ■ □ ■ □ ■ □ ■
# ...and so on
```

---

## Loop Patterns You'll Use Constantly

### Pattern 1: Search and Accumulate

```python
numbers = [2, 5, 8, 3, 9, 1, 7]
sum_of_even = 0

for num in numbers:
    if num % 2 == 0:
        sum_of_even += num

print(f"Sum of even numbers: {sum_of_even}")
# Output: Sum of even numbers: 15 (2 + 8 + 5 = 15... wait, let me recalculate: 2+8=10)
# Actually: 2 + 8 = 10, so answer is 10
```

### Pattern 2: Find Maximum/Minimum

```python
scores = [78, 95, 83, 91, 87]
highest = scores[0]

for score in scores:
    if score > highest:
        highest = score

print(f"Highest score: {highest}")
# Output: Highest score: 95
```

### Pattern 3: Count Occurrences

```python
data = ["A", "B", "A", "C", "A", "B"]
count_a = 0

for item in data:
    if item == "A":
        count_a += 1

print(f"A appears {count_a} times")
# Output: A appears 3 times
```

### Pattern 4: Validate User Input (Loop Until Valid)

```python
while True:
    age = int(input("Enter age (0-150): "))
    if 0 <= age <= 150:
        break
    print("Invalid! Please enter between 0 and 150")

print(f"You entered {age}")
```

### Pattern 5: Process Until Condition

```python
password = "secret"
attempts = 0
max_attempts = 3

while attempts < max_attempts:
    guess = input(f"Enter password (Attempt {attempts + 1}/{max_attempts}): ")
    if guess == password:
        print("Success!")
        break
    attempts += 1
else:
    print("Too many wrong attempts. Account locked!")
```

**Note:** `else` after a loop runs if loop completes normally (not `break`).

---

## Advanced Loop Control

### `else` with Loops

The `else` block runs if the loop completes without `break`:

```python
# Loop finds item - break before else
for i in range(5):
    if i == 3:
        print("Found 3!")
        break
else:
    print("Never found target")

# Output: Found 3!

# Loop completes without break - else runs
for i in range(5):
    if i == 10:
        break
else:
    print("Loop completed normally")

# Output: Loop completed normally
```

### Real Example: Search with Else

```python
students = ["Alice", "Bob", "Charlie"]
target = "David"

for student in students:
    if student == target:
        print(f"Found {target}!")
        break
else:
    print(f"{target} not found in class")

# Output: David not found in class
```

---

## Project 1: Number Validation Game

```python
import random

secret = random.randint(1, 10)

for attempt in range(1, 4):
    guess = int(input(f"Guess {attempt}: "))
    
    if guess == secret:
        print("Correct!")
        break
    elif guess < secret:
        print("Too low!")
    else:
        print("Too high!")
else:
    print(f"Game over! Secret was {secret}")
```

---

## Project 2: Times Table Generator

```python
print("=== TIMES TABLE GENERATOR ===\n")

while True:
    num = int(input("Enter a number (0 to exit): "))
    
    if num == 0:
        print("Goodbye!")
        break
    
    print(f"\nTimes table for {num}:")
    for i in range(1, 11):
        print(f"{num} x {i} = {num * i}")
    print()
```

---

## Project 3: Prime Number Checker

```python
def is_prime(n):
    if n < 2:
        return False
    
    for i in range(2, n):
        if n % i == 0:
            return False
    
    return True

# Find primes 1-20
primes = []
for num in range(1, 21):
    if is_prime(num):
        primes.append(num)

print(f"Primes 1-20: {primes}")
# Output: Primes 1-20: [2, 3, 5, 7, 11, 13, 17, 19]
```

---

## Exercises

### Exercise 1: Break Practice

Create `break_practice.py`:

```python
# Find first number greater than 50
numbers = [10, 25, 45, 55, 65, 75]

for num in numbers:
    if num > 50:
        print(f"Found: {num}")
        break
```

### Exercise 2: Continue Practice

Create `continue_practice.py`:

```python
# Skip multiples of 3
for i in range(1, 11):
    if i % 3 == 0:
        continue
    print(i)
```

### Exercise 3: Nested Loop Pattern

Create `nested_pattern.py`:

```python
# Create pyramid
for i in range(1, 6):
    print("*" * i)
```

### Exercise 4: Input Validation

Create `validation.py`:

```python
# Keep asking until valid
while True:
    grade = int(input("Enter grade (0-100): "))
    if 0 <= grade <= 100:
        print(f"Grade recorded: {grade}")
        break
    print("Invalid! Try again")
```

### Exercise 5: Search and Count

Create `search_count.py`:

```python
# Count occurrences
text = "programming is fun and programming teaches logic"
word = "programming"
count = 0

for letter_index in range(len(text)):
    # This is simplified; real solution uses text.count() or text.split()
    pass

# Simpler:
count = text.count(word)
print(f"'{word}' appears {count} times")
```

---

## Common Mistakes

```python
# ✗ WRONG - Indentation with break
for i in range(5):
if i == 2:
    break  # Wrong indentation
print(i)

# ✓ CORRECT
for i in range(5):
    if i == 2:
        break
    print(i)

# ✗ WRONG - Using break outside loop
break  # SyntaxError!

# ✓ CORRECT
for i in range(5):
    break

# ✗ WRONG - Infinite loop without proper exit
while True:
    print("Forever!")
    # No break or exit condition

# ✓ CORRECT
while True:
    user_input = input("Continue? (yes/no): ")
    if user_input == "no":
        break
```

---

## Key Takeaways

✓ `break` exits the loop immediately  
✓ `continue` skips current iteration and goes to next  
✓ `pass` is a placeholder that does nothing  
✓ Nested loops iterate within loops  
✓ `else` after loops runs if no `break` occurred  
✓ Use these patterns: search, accumulate, count, validate  
✓ Loop control statements are essential for real programs  

---

## Quick Reference

```python
# Break out of loop
for i in range(10):
    if i == 5:
        break

# Skip iteration
for i in range(10):
    if i == 5:
        continue

# Placeholder
if condition:
    pass

# Nested loops
for i in range(3):
    for j in range(2):
        print(i, j)

# Loop with else
for i in range(5):
    if i == 3:
        break
else:
    print("Completed")
```

---

## Homework

1. ✓ Create a program using `break` to find first negative number
2. ✓ Create a program using `continue` to skip even numbers
3. ✓ Create a nested loop to print a 5x5 grid
4. ✓ Create a program with input validation using a `while` loop

Next hour: **Functions!**
