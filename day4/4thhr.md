# Day 4 - Hour 4: Object-Oriented Programming (OOP)

## Welcome to the Final Hour of Day 4!

Welcome to **Object-Oriented Programming** - one of the most important programming paradigms! OOP lets you organize code around objects, making programs cleaner, more reusable, and easier to maintain.

Think of objects like real-world things: A car is an object with properties (color, speed) and actions (drive, brake).

---

## What is OOP?

**Object-Oriented Programming** organizes code into **objects** that contain:
- **Attributes** (properties/data)
- **Methods** (functions/actions)

### Why OOP?

1. **Organization** - Code is structured around real-world concepts
2. **Reusability** - Write once, use many times
3. **Maintainability** - Easy to fix and update
4. **Scalability** - Good for large projects

---

## Classes and Objects

A **class** is a blueprint for creating objects.

### Syntax

```python
class ClassName:
    def __init__(self, parameter):
        self.attribute = parameter
    
    def method(self):
        print("Doing something")
```

### Example 1: Simple Class

```python
class Dog:
    """Blueprint for a dog"""
    
    def __init__(self, name, age):
        """Constructor - runs when object is created"""
        self.name = name
        self.age = age
    
    def bark(self):
        """Method - action the dog can do"""
        print(f"{self.name} says: Woof!")
    
    def info(self):
        """Return dog information"""
        return f"{self.name} is {self.age} years old"

# Create objects from class
dog1 = Dog("Buddy", 3)
dog2 = Dog("Max", 5)

# Use objects
print(dog1.name)                # Buddy
print(dog2.name)                # Max

dog1.bark()                     # Buddy says: Woof!
print(dog1.info())              # Buddy is 3 years old
```

---

## Understanding `self`

`self` refers to the specific object. It lets each object have its own data.

```python
class Person:
    def __init__(self, name):
        self.name = name        # self.name belongs to THIS object
    
    def greet(self):
        print(f"Hi, I'm {self.name}")

person1 = Person("Alice")
person2 = Person("Bob")

person1.greet()                 # Hi, I'm Alice
person2.greet()                 # Hi, I'm Bob

# Each has their own name!
print(person1.name)             # Alice
print(person2.name)             # Bob
```

---

## Attributes and Methods

### Attributes (Data)

```python
class Car:
    def __init__(self, brand, color):
        self.brand = brand      # Attribute
        self.color = color      # Attribute
        self.speed = 0          # Attribute
```

### Methods (Actions)

```python
class Car:
    def __init__(self, brand, color):
        self.brand = brand
        self.color = color
        self.speed = 0
    
    def accelerate(self, amount):
        """Method - increases speed"""
        self.speed += amount
        print(f"Accelerating... Speed: {self.speed}")
    
    def brake(self, amount):
        """Method - decreases speed"""
        self.speed -= amount
        print(f"Braking... Speed: {self.speed}")
    
    def info(self):
        """Method - returns information"""
        return f"{self.color} {self.brand} going {self.speed} km/h"

# Create object
car = Car("Toyota", "Red")

# Use methods
car.accelerate(30)              # Accelerating... Speed: 30
car.accelerate(20)              # Accelerating... Speed: 50
car.brake(10)                   # Braking... Speed: 40
print(car.info())               # Red Toyota going 40 km/h
```

---

## Real-World Example: Bank Account

```python
class BankAccount:
    def __init__(self, account_holder, initial_balance):
        self.holder = account_holder
        self.balance = initial_balance
    
    def deposit(self, amount):
        """Add money"""
        self.balance += amount
        print(f"Deposited ${amount}. New balance: ${self.balance}")
    
    def withdraw(self, amount):
        """Remove money"""
        if amount > self.balance:
            print("Insufficient funds!")
        else:
            self.balance -= amount
            print(f"Withdrew ${amount}. New balance: ${self.balance}")
    
    def check_balance(self):
        """View balance"""
        print(f"Balance: ${self.balance}")
    
    def info(self):
        """Account information"""
        return f"{self.holder}: ${self.balance}"

# Create accounts
account1 = BankAccount("Alice", 1000)
account2 = BankAccount("Bob", 500)

# Use methods
account1.deposit(500)           # Deposited $500. New balance: $1500
account1.withdraw(200)          # Withdrew $200. New balance: $1300
account1.check_balance()        # Balance: $1300

print(account1.info())          # Alice: $1300
print(account2.info())          # Bob: $500
```

---

## Inheritance

**Inheritance** lets a class inherit from another class, reusing code.

```python
# Parent class (Base class)
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        print(f"{self.name} makes a sound")
    
    def sleep(self):
        print(f"{self.name} is sleeping")

# Child class (inherits from Animal)
class Dog(Animal):
    def speak(self):            # Override method
        print(f"{self.name} says: Woof!")

class Cat(Animal):
    def speak(self):            # Override method
        print(f"{self.name} says: Meow!")

# Create objects
dog = Dog("Buddy")
cat = Cat("Whiskers")

dog.speak()                     # Buddy says: Woof!
dog.sleep()                     # Buddy is sleeping (inherited)

cat.speak()                     # Whiskers says: Meow!
cat.sleep()                     # Whiskers is sleeping (inherited)
```

### Using `super()` to Call Parent Method

```python
class Vehicle:
    def __init__(self, brand):
        self.brand = brand
    
    def info(self):
        return f"Vehicle: {self.brand}"

class Car(Vehicle):
    def __init__(self, brand, color):
        super().__init__(brand)  # Call parent constructor
        self.color = color
    
    def info(self):
        parent_info = super().info()  # Call parent method
        return f"{parent_info}, Color: {self.color}"

car = Car("Toyota", "Red")
print(car.info())               # Vehicle: Toyota, Color: Red
```

---

## Encapsulation (Private Attributes)

Use `__` prefix to make attributes private (hidden from outside):

```python
class BankAccount:
    def __init__(self, holder, balance):
        self.holder = holder
        self.__balance = balance    # Private attribute
    
    def deposit(self, amount):
        self.__balance += amount
    
    def get_balance(self):
        return self.__balance

account = BankAccount("Alice", 1000)
account.deposit(500)

print(account.get_balance())    # 1500
print(account.__balance)        # Error - can't access private directly
```

---

## Project 1: Student Management System

```python
class Student:
    """Student class with grades"""
    
    def __init__(self, name, student_id):
        self.name = name
        self.student_id = student_id
        self.grades = []
    
    def add_grade(self, grade):
        """Add a grade"""
        if 0 <= grade <= 100:
            self.grades.append(grade)
        else:
            print("Grade must be 0-100")
    
    def get_average(self):
        """Calculate average"""
        if not self.grades:
            return 0
        return sum(self.grades) / len(self.grades)
    
    def info(self):
        """Display student info"""
        avg = self.get_average()
        return f"{self.name} (ID: {self.student_id}) - Average: {avg:.2f}"

# Create students
s1 = Student("Alice", 101)
s2 = Student("Bob", 102)

# Add grades
s1.add_grade(85)
s1.add_grade(90)
s1.add_grade(88)

s2.add_grade(92)
s2.add_grade(95)

# Display info
print(s1.info())                # Alice (ID: 101) - Average: 87.67
print(s2.info())                # Bob (ID: 102) - Average: 93.50
```

---

## Project 2: Game Character

```python
class Character:
    """Game character"""
    
    def __init__(self, name, health, attack_power):
        self.name = name
        self.health = health
        self.attack_power = attack_power
    
    def attack(self, other):
        """Attack another character"""
        damage = self.attack_power
        other.health -= damage
        print(f"{self.name} attacks {other.name} for {damage} damage!")
        print(f"{other.name} health: {other.health}")
    
    def heal(self, amount):
        """Restore health"""
        self.health += amount
        print(f"{self.name} heals for {amount}. Health: {self.health}")
    
    def is_alive(self):
        """Check if alive"""
        return self.health > 0

# Create characters
player = Character("Knight", 100, 20)
enemy = Character("Goblin", 50, 15)

# Battle
print("--- Battle Start ---")
player.attack(enemy)            # Knight attacks Goblin for 20 damage!

if enemy.is_alive():
    enemy.attack(player)        # Goblin attacks Knight for 15 damage!

player.heal(10)                 # Knight heals for 10. Health: 95
```

---

## Exercises

### Exercise 1: Person Class

Create `person.py`:

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def introduce(self):
        return f"Hi, I'm {self.name} and I'm {self.age}"

person = Person("Alice", 25)
print(person.introduce())
```

### Exercise 2: Rectangle Class

Create `rectangle.py`:

```python
class Rectangle:
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
    def perimeter(self):
        return 2 * (self.width + self.height)

rect = Rectangle(5, 3)
print(f"Area: {rect.area()}")
print(f"Perimeter: {rect.perimeter()}")
```

### Exercise 3: Book Class

Create `book.py`:

```python
class Book:
    def __init__(self, title, author, pages):
        self.title = title
        self.author = author
        self.pages = pages
    
    def info(self):
        return f"{self.title} by {self.author} ({self.pages} pages)"

book = Book("Python 101", "John Doe", 350)
print(book.info())
```

### Exercise 4: Inheritance

Create `inheritance.py`:

```python
class Vehicle:
    def __init__(self, brand):
        self.brand = brand

class Motorcycle(Vehicle):
    def info(self):
        return f"Motorcycle: {self.brand}"

moto = Motorcycle("Harley")
print(moto.info())
```

---

## Common Mistakes

```python
# ✗ WRONG - Forgetting self
class Dog:
    def __init__(name, age):  # Missing self!
        name = name

# ✓ CORRECT
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

# ✗ WRONG - Not calling parent constructor
class Car(Vehicle):
    def __init__(self, brand, color):
        self.color = color  # Forgot super().__init__()!

# ✓ CORRECT
class Car(Vehicle):
    def __init__(self, brand, color):
        super().__init__(brand)
        self.color = color
```

---

## Key Takeaways

✓ Classes are blueprints; objects are instances  
✓ `__init__` is the constructor  
✓ `self` refers to the specific object  
✓ Attributes store data; methods perform actions  
✓ Inheritance reuses code from parent classes  
✓ Encapsulation hides data with `__` prefix  
✓ OOP makes code organized and reusable  

---

## Quick Reference

```python
# Define class
class Dog:
    def __init__(self, name):
        self.name = name
    
    def bark(self):
        print(f"{self.name} barks!")

# Create object
dog = Dog("Buddy")

# Use object
print(dog.name)
dog.bark()

# Inheritance
class Poodle(Dog):
    def bark(self):
        print(f"{self.name} barks: Yap yap!")
```

---

## Congratulations! 🎉

You've completed **Day 4 - Intermediate Python**! You now know:
- ✓ File Handling (read/write)
- ✓ Modules & Packages
- ✓ Error Handling
- ✓ Object-Oriented Programming

**Tomorrow: Advanced Python + Final Project!**
