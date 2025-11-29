# Day 5 - Hour 2: Iterators, Generators, Decorators

## Welcome to Hour 2!

We're diving into three advanced Python features:
1. **Iterators** - Objects that return values one at a time
2. **Generators** - Functions that yield values lazily
3. **Decorators** - Functions that modify other functions

These are "Pythonic" ways to write elegant code!

---

## Iterators

An **iterator** is an object that returns values one at a time using `__iter__()` and `__next__()`.

### How Iterators Work

```python
# Manually using iterators
numbers = [1, 2, 3]
iterator = iter(numbers)

print(next(iterator))           # 1
print(next(iterator))           # 2
print(next(iterator))           # 3
print(next(iterator))           # StopIteration error
```

### Creating Custom Iterator

```python
class CountUp:
    """Iterator that counts up to a number"""
    def __init__(self, max):
        self.max = max
        self.current = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.current < self.max:
            self.current += 1
            return self.current
        else:
            raise StopIteration

# Use custom iterator
counter = CountUp(3)
print(next(counter))            # 1
print(next(counter))            # 2
print(next(counter))            # 3

# Use in for loop (automatic)
for num in CountUp(3):
    print(num)                  # 1, 2, 3
```

---

## Generators

A **generator** is a function that yields values one at a time. Much simpler than creating a class!

### Generator with `yield`

```python
def count_up(max):
    """Generator function"""
    current = 0
    while current < max:
        current += 1
        yield current        # Return value and pause

# Use generator
for num in count_up(3):
    print(num)               # 1, 2, 3

# Get values manually
gen = count_up(3)
print(next(gen))             # 1
print(next(gen))             # 2
print(next(gen))             # 3
```

### Generators Save Memory

```python
# With list - stores all values in memory
def get_numbers_list(n):
    result = []
    for i in range(n):
        result.append(i)
    return result

numbers = get_numbers_list(1000000)  # Creates huge list

# With generator - generates on demand
def get_numbers_generator(n):
    for i in range(n):
        yield i              # Doesn't create list

numbers = get_numbers_generator(1000000)  # Doesn't store all values
```

### Real Generator Examples

```python
# Read file line by line
def read_file(filename):
    with open(filename, 'r') as file:
        for line in file:
            yield line.strip()

# Use it
for line in read_file('data.txt'):
    print(line)

# Generate Fibonacci numbers
def fibonacci(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b

for num in fibonacci(5):
    print(num)               # 0, 1, 1, 2, 3

# Generate infinite sequence
def infinite_counter():
    count = 0
    while True:
        yield count
        count += 1

counter = infinite_counter()
print(next(counter))         # 0
print(next(counter))         # 1
print(next(counter))         # 2
```

---

## Decorators

A **decorator** is a function that modifies another function or class.

### Simple Decorator

```python
def my_decorator(func):
    def wrapper():
        print("Before function")
        func()
        print("After function")
    return wrapper

@my_decorator
def say_hello():
    print("Hello!")

say_hello()

# Output:
# Before function
# Hello!
# After function
```

### Decorator with Arguments

```python
def my_decorator(func):
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@my_decorator
def add(a, b):
    return a + b

result = add(5, 3)
print(result)                # Result: 8

# Output:
# Calling add
# Result: 8
```

### Practical Decorator: Timing Function

```python
import time

def timer(func):
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f"{func.__name__} took {end - start:.2f} seconds")
        return result
    return wrapper

@timer
def slow_function():
    time.sleep(1)
    print("Done!")

slow_function()

# Output:
# Done!
# slow_function took 1.00 seconds
```

### Practical Decorator: Validation

```python
def validate_positive(func):
    def wrapper(*args, **kwargs):
        for arg in args:
            if isinstance(arg, (int, float)) and arg < 0:
                print("Error: Arguments must be positive!")
                return None
        return func(*args, **kwargs)
    return wrapper

@validate_positive
def divide(a, b):
    return a / b

print(divide(10, 2))         # 5.0
print(divide(-10, 2))        # Error: Arguments must be positive!
```

### Practical Decorator: Logging

```python
def log_calls(func):
    def wrapper(*args, **kwargs):
        print(f"Calling: {func.__name__}")
        print(f"Args: {args}")
        print(f"Kwargs: {kwargs}")
        result = func(*args, **kwargs)
        print(f"Result: {result}")
        return result
    return wrapper

@log_calls
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

greet("Alice", greeting="Hi")
```

---

## Stacking Decorators

Use multiple decorators:

```python
def decorator1(func):
    def wrapper():
        print("Decorator 1 - Before")
        func()
        print("Decorator 1 - After")
    return wrapper

def decorator2(func):
    def wrapper():
        print("Decorator 2 - Before")
        func()
        print("Decorator 2 - After")
    return wrapper

@decorator1
@decorator2
def say_hello():
    print("Hello!")

say_hello()

# Output:
# Decorator 1 - Before
# Decorator 2 - Before
# Hello!
# Decorator 2 - After
# Decorator 1 - After
```

---

## Built-in Decorators

### `@property` - Make methods look like attributes

```python
class Circle:
    def __init__(self, radius):
        self._radius = radius
    
    @property
    def area(self):
        return 3.14 * self._radius ** 2

circle = Circle(5)
print(circle.area)              # 78.5 (looks like attribute)
```

### `@staticmethod` - Method that doesn't use instance

```python
class MathUtils:
    @staticmethod
    def add(a, b):
        return a + b

result = MathUtils.add(5, 3)
print(result)                   # 8 (no self needed)
```

### `@classmethod` - Method that uses class

```python
class Person:
    species = "Homo sapiens"
    
    @classmethod
    def get_species(cls):
        return cls.species

print(Person.get_species())     # Homo sapiens
```

---

## Real-World Example: Request Logger

```python
import time
import json

def log_api_request(func):
    """Decorator that logs API requests"""
    def wrapper(*args, **kwargs):
        request_data = {
            "function": func.__name__,
            "timestamp": time.time(),
            "args": str(args),
            "kwargs": str(kwargs)
        }
        print(f"API Call: {json.dumps(request_data, indent=2)}")
        result = func(*args, **kwargs)
        return result
    return wrapper

@log_api_request
def fetch_user(user_id):
    return f"User {user_id} data"

@log_api_request
def create_post(content):
    return f"Post created with content: {content}"

# Use decorated functions
fetch_user(123)
create_post("Hello world")
```

---

## Project 1: Generator Pipeline

```python
def read_numbers(n):
    """Generate numbers 1 to n"""
    for i in range(1, n + 1):
        yield i

def squares(numbers):
    """Generate squares of numbers"""
    for num in numbers:
        yield num ** 2

def filter_even(numbers):
    """Filter only even numbers"""
    for num in numbers:
        if num % 2 == 0:
            yield num

# Chain generators
for num in filter_even(squares(read_numbers(10))):
    print(num)

# Output: 4, 16, 36, 64, 100
```

---

## Project 2: Performance Monitor

```python
import time

def monitor_performance(func):
    """Monitor function performance"""
    def wrapper(*args, **kwargs):
        print(f"\n📊 Monitoring: {func.__name__}")
        
        # Memory before
        import sys
        start_mem = sys.getsizeof(args)
        
        # Time execution
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        
        # Report
        elapsed = end_time - start_time
        end_mem = sys.getsizeof(result)
        
        print(f"⏱️  Elapsed: {elapsed:.4f}s")
        print(f"💾 Memory: {end_mem} bytes")
        
        return result
    return wrapper

@monitor_performance
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

fibonacci(10)
```

---

## Exercises

### Exercise 1: Simple Generator

Create `generator1.py`:

```python
def countdown(n):
    while n > 0:
        yield n
        n -= 1

for num in countdown(5):
    print(num)              # 5, 4, 3, 2, 1
```

### Exercise 2: Custom Iterator

Create `iterator.py`:

```python
class Repeater:
    def __init__(self, value, times):
        self.value = value
        self.times = times
        self.count = 0
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.count < self.times:
            self.count += 1
            return self.value
        else:
            raise StopIteration

for item in Repeater("Hi", 3):
    print(item)             # Hi, Hi, Hi
```

### Exercise 3: Simple Decorator

Create `decorator.py`:

```python
def shout(func):
    def wrapper(*args, **kwargs):
        result = func(*args, **kwargs)
        return result.upper()
    return wrapper

@shout
def greet(name):
    return f"Hello, {name}"

print(greet("Alice"))       # HELLO, ALICE
```

### Exercise 4: Generator Pipeline

Create `pipeline.py`:

```python
def numbers():
    for i in range(1, 6):
        yield i

def double(nums):
    for n in nums:
        yield n * 2

for num in double(numbers()):
    print(num)              # 2, 4, 6, 8, 10
```

---

## Key Takeaways

✓ Iterators use `__iter__()` and `__next__()`  
✓ Generators use `yield` and are memory efficient  
✓ Decorators modify functions/classes  
✓ `@property`, `@staticmethod`, `@classmethod` are built-in decorators  
✓ Chain generators for elegant data processing  
✓ Use decorators for cross-cutting concerns  

---

## Quick Reference

```python
# Generator
def gen():
    yield 1
    yield 2

for item in gen():
    print(item)

# Decorator
def decorator(func):
    def wrapper():
        print("Before")
        func()
        print("After")
    return wrapper

@decorator
def my_func():
    print("Function")

my_func()
```

---

## Homework

1. ✓ Create a custom iterator
2. ✓ Create a generator that yields Fibonacci numbers
3. ✓ Create a decorator that measures function time
4. ✓ Create a generator pipeline

Next hour: **Virtual Environments, Pip, and Final Project!**
