# Day 2 - Hour 1: Conditional Statements (If/Else)

## Welcome to Day 2!

Welcome back! Yesterday you learned the fundamentals. Today we're adding **decision-making** to your programs. This is where code gets intelligent!

Think about your own decisions: "If it's raining, take an umbrella, else enjoy the sunshine." Programs work the same way - they make decisions based on conditions.

---

## What are Conditional Statements?

A **conditional statement** is a piece of code that runs only if a certain condition is true. It allows your program to make decisions.

Without conditionals, your program always does the same thing. With conditionals, your program can behave differently based on circumstances.

```python
# Without condition - always says same thing
print("You are allowed entry")

# With condition - different behavior based on age
age = 20
if age >= 18:
    print("You are allowed entry")
else:
    print("You must be 18 or older")
```

---

## The `if` Statement

The simplest conditional is `if`.

### Syntax

```python
if condition:
    # Code here runs if condition is True
    print("Condition was true!")
```

**Important:** Remember the colon `:` and indentation!

### Simple Example

```python
age = 20

if age >= 18:
    print("You are an adult")

# Output: You are an adult
```

### Example 2: No Output if False

```python
age = 15

if age >= 18:
    print("You are an adult")

# No output because condition is False
```

---

## The `else` Statement

`else` runs when the `if` condition is false.

### Syntax

```python
if condition:
    # Runs if condition is True
else:
    # Runs if condition is False
```

### Example

```python
age = 15

if age >= 18:
    print("You are an adult")
else:
    print("You are a teenager")

# Output: You are a teenager
```

### Example 2

```python
score = 45

if score >= 60:
    print("You passed!")
else:
    print("You failed. Try again.")

# Output: You failed. Try again.
```

---

## The `elif` Statement

`elif` means "else if" - it lets you check multiple conditions.

### Syntax

```python
if condition1:
    # Runs if condition1 is True
elif condition2:
    # Runs if condition1 is False and condition2 is True
elif condition3:
    # Runs if condition1 and condition2 are False and condition3 is True
else:
    # Runs if all conditions are False
```

### Example: Grade Calculator

```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Score: {score}, Grade: {grade}")
# Output: Score: 85, Grade: B
```

### Example 2: Login System

```python
username = "admin"
password = "secure123"

user_input = "admin"
pass_input = "secure123"

if user_input == username and pass_input == password:
    print("Login successful!")
elif user_input != username:
    print("Invalid username")
else:
    print("Invalid password")

# Output: Login successful!
```

---

## Nested Conditions

You can put `if` statements inside `if` statements!

### Example

```python
age = 25
has_license = True

if age >= 18:
    if has_license:
        print("You can drive")
    else:
        print("You need a license to drive")
else:
    print("Too young to drive")

# Output: You can drive
```

### Example 2: E-Commerce Checkout

```python
cart_total = 150
is_member = True
has_discount_code = True

if cart_total > 0:
    if is_member:
        if has_discount_code:
            discount = cart_total * 0.1
            final_price = cart_total - discount
            print(f"Member + discount: ${final_price}")
        else:
            member_discount = cart_total * 0.05
            final_price = cart_total - member_discount
            print(f"Member discount: ${final_price}")
    else:
        print(f"Total: ${cart_total}")
else:
    print("Cart is empty")

# Output: Member + discount: $135.0
```

---

## Conditions with Logical Operators

You already know `and`, `or`, `not`. Let's use them in conditions!

### Using `and`

```python
age = 25
has_license = True

if age >= 18 and has_license:
    print("You can drive")
else:
    print("You cannot drive")

# Output: You can drive
```

### Using `or`

```python
day = "Saturday"

if day == "Saturday" or day == "Sunday":
    print("It's the weekend!")
else:
    print("It's a weekday")

# Output: It's the weekend!
```

### Using `not`

```python
is_raining = False

if not is_raining:
    print("Go outside!")
else:
    print("Stay inside")

# Output: Go outside!
```

### Complex Conditions

```python
age = 25
income = 50000
credit_score = 720

# Can apply for loan if: age >= 21 AND (income > 30000 OR credit_score > 700)
if age >= 21 and (income > 30000 or credit_score > 700):
    print("Loan approved!")
else:
    print("Loan denied")

# Output: Loan approved!
```

---

## Common Conditional Patterns

### Pattern 1: Checking Ranges

```python
temperature = 22

if temperature < 0:
    status = "Freezing"
elif temperature < 10:
    status = "Cold"
elif temperature < 20:
    status = "Cool"
elif temperature < 30:
    status = "Warm"
else:
    status = "Hot"

print(f"Temperature: {temperature}°C - {status}")
# Output: Temperature: 22°C - Warm
```

### Pattern 2: Checking Multiple Conditions

```python
username = "john_doe"
password = "secret123"
is_account_active = True

if username == "john_doe":
    if password == "secret123":
        if is_account_active:
            print("Welcome!")
        else:
            print("Account suspended")
    else:
        print("Wrong password")
else:
    print("Username not found")

# Output: Welcome!
```

### Pattern 3: Checking String Contains

```python
email = "john@example.com"

if "@" in email and "." in email:
    print("Valid email format")
else:
    print("Invalid email")

# Output: Valid email format
```

---

## Ternary Operator (Conditional Expression)

Quick one-line if/else:

```python
age = 20
status = "adult" if age >= 18 else "teenager"
print(status)
# Output: adult
```

Equivalent to:
```python
if age >= 18:
    status = "adult"
else:
    status = "teenager"
```

### More Examples

```python
score = 85
result = "Pass" if score >= 60 else "Fail"
print(result)
# Output: Pass

max_num = 10 if 10 > 5 else 5
print(max_num)
# Output: 10
```

---

## Project 1: Simple ATM System

```python
print("=== ATM SYSTEM ===\n")

# Simulate stored PIN and balance
stored_pin = "1234"
balance = 1000

# Get user input
pin_input = input("Enter PIN: ")

if pin_input == stored_pin:
    print("PIN correct!\n")
    
    operation = input("What would you like to do?\n1. Check balance\n2. Withdraw\n3. Deposit\nChoice (1-3): ")
    
    if operation == "1":
        print(f"Your balance: ${balance}")
    
    elif operation == "2":
        amount = float(input("Amount to withdraw: $"))
        if amount <= balance:
            balance -= amount
            print(f"Withdrawn: ${amount}")
            print(f"New balance: ${balance}")
        else:
            print("Insufficient funds")
    
    elif operation == "3":
        amount = float(input("Amount to deposit: $"))
        balance += amount
        print(f"Deposited: ${amount}")
        print(f"New balance: ${balance}")
    
    else:
        print("Invalid choice")
else:
    print("PIN incorrect! Access denied.")
```

---

## Project 2: Number Guessing Game

```python
print("=== NUMBER GUESSING GAME ===\n")

secret_number = 7
guess = int(input("Guess a number between 1 and 10: "))

if guess == secret_number:
    print("Correct! You won!")
elif guess < secret_number:
    print(f"Wrong! The number is higher than {guess}")
else:
    print(f"Wrong! The number is lower than {guess}")
```

---

## Exercises

### Exercise 1: Age Category

Create `age_category.py`:

```python
age = int(input("Enter your age: "))

if age < 13:
    category = "Child"
elif age < 18:
    category = "Teenager"
elif age < 65:
    category = "Adult"
else:
    category = "Senior"

print(f"You are in the {category} category")
```

### Exercise 2: Temperature Advice

Create `temperature.py`:

```python
temp = float(input("Enter temperature (°C): "))

if temp < 0:
    advice = "It's freezing! Wear heavy clothes."
elif temp < 10:
    advice = "It's cold. Wear a jacket."
elif temp < 20:
    advice = "It's cool. Bring a sweater."
elif temp < 30:
    advice = "It's warm. Light clothes are fine."
else:
    advice = "It's hot! Drink plenty of water."

print(advice)
```

### Exercise 3: Online Shopping Discount

Create `discount.py`:

```python
total = float(input("Enter purchase amount: $"))
is_member = input("Are you a member? (yes/no): ").lower()

if total >= 100:
    if is_member == "yes":
        discount = total * 0.2  # 20% for members
    else:
        discount = total * 0.1  # 10% for non-members
elif total >= 50:
    if is_member == "yes":
        discount = total * 0.1  # 10% for members
    else:
        discount = total * 0.05  # 5% for non-members
else:
    discount = 0

final_price = total - discount
print(f"Discount: ${discount:.2f}")
print(f"Final price: ${final_price:.2f}")
```

---

## Common Mistakes

```python
# ✗ WRONG - Missing colon
if age >= 18
    print("Adult")

# ✓ CORRECT
if age >= 18:
    print("Adult")

# ✗ WRONG - Wrong indentation
if age >= 18:
print("Adult")

# ✓ CORRECT
if age >= 18:
    print("Adult")

# ✗ WRONG - Using = instead of ==
if age = 18:
    print("You are 18")

# ✓ CORRECT
if age == 18:
    print("You are 18")

# ✗ WRONG - Unreachable code
if age >= 18:
    print("Adult")
elif age >= 10:
    print("Not a teen")  # Never runs because first condition covers it

# ✓ CORRECT
if age >= 18:
    print("Adult")
elif age >= 13:
    print("Teenager")
else:
    print("Child")
```

---

## Key Takeaways

✓ `if` runs code only if condition is True  
✓ `else` provides alternative code if condition is False  
✓ `elif` checks multiple conditions in sequence  
✓ Always use `:` after condition and proper indentation  
✓ Use `and`, `or`, `not` for complex conditions  
✓ Nested conditions let you check multiple levels  
✓ Ternary operator: `value_if_true if condition else value_if_false`  

---

## Quick Reference

```python
# Simple if
if condition:
    print("Condition is true")

# If/else
if condition:
    print("True")
else:
    print("False")

# If/elif/else
if condition1:
    print("Condition 1 true")
elif condition2:
    print("Condition 2 true")
else:
    print("All false")

# Ternary operator
result = "yes" if condition else "no"
```

---

## Homework

1. ✓ Create a program that checks if a number is positive, negative, or zero
2. ✓ Create a restaurant menu selector with if/elif/else
3. ✓ Create a simple calculator that takes two numbers and an operation (add/subtract/multiply/divide)
4. ✓ Create a password strength checker

Next hour: **Loops! (For and While)**
