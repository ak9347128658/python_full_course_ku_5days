# Day 5 - Hour 1: Advanced OOP (Inheritance, Polymorphism, Encapsulation)

## Welcome to Day 5!

Welcome to the **final day**! Today we're diving deeper into OOP with advanced concepts, and tomorrow you'll build a complete project. Let's master the three pillars of OOP!

---

## The Three Pillars of OOP

1. **Encapsulation** - Hide internal details
2. **Inheritance** - Reuse code through hierarchy
3. **Polymorphism** - Use objects interchangeably

---

## Encapsulation - Data Hiding

Encapsulation protects internal data from being accessed or modified incorrectly.

### Public vs Private

```python
class BankAccount:
    def __init__(self, holder, balance):
        self.holder = holder            # Public
        self.__balance = balance        # Private (double underscore)
    
    def deposit(self, amount):
        if amount > 0:
            self.__balance += amount
            return True
        return False
    
    def get_balance(self):
        return self.__balance

account = BankAccount("Alice", 1000)
print(account.holder)                   # Alice (public - OK)
print(account.get_balance())            # 1000 (via method - OK)
print(account.__balance)                # Error! (private - can't access)
```

### Getters and Setters

Control how data is accessed and modified:

```python
class Person:
    def __init__(self, name, age):
        self.__name = name
        self.__age = age
    
    # Getter
    def get_age(self):
        return self.__age
    
    # Setter with validation
    def set_age(self, age):
        if 0 < age < 150:
            self.__age = age
        else:
            print("Invalid age!")
    
    def get_name(self):
        return self.__name

person = Person("Alice", 25)
print(person.get_age())                 # 25
person.set_age(26)
print(person.get_age())                 # 26
person.set_age(200)                     # Invalid age!
```

---

## Inheritance - Code Reuse

### Single Inheritance

```python
# Parent class
class Animal:
    def __init__(self, name):
        self.name = name
    
    def speak(self):
        print(f"{self.name} makes a sound")

# Child class
class Dog(Animal):
    def speak(self):                    # Override
        print(f"{self.name} barks: Woof!")

dog = Dog("Buddy")
dog.speak()                             # Buddy barks: Woof!
```

### Multi-level Inheritance

```python
class Animal:
    def move(self):
        print("Moving...")

class Mammal(Animal):
    def breathe(self):
        print("Breathing...")

class Dog(Mammal):
    def bark(self):
        print("Woof!")

dog = Dog()
dog.move()                              # Moving...
dog.breathe()                           # Breathing...
dog.bark()                              # Woof!
```

### Multiple Inheritance

A class can inherit from multiple parents:

```python
class Walker:
    def walk(self):
        print("Walking...")

class Swimmer:
    def swim(self):
        print("Swimming...")

class Duck(Walker, Swimmer):
    pass

duck = Duck()
duck.walk()                             # Walking...
duck.swim()                             # Swimming...
```

---

## Polymorphism - Same Interface, Different Behavior

```python
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        print("Woof!")

class Cat(Animal):
    def speak(self):
        print("Meow!")

class Cow(Animal):
    def speak(self):
        print("Moo!")

# Same function works with different types
def make_animal_speak(animal):
    animal.speak()

animals = [Dog(), Cat(), Cow()]

for animal in animals:
    make_animal_speak(animal)

# Output:
# Woof!
# Meow!
# Moo!
```

---

## Real-World OOP Example: Game Characters

```python
class Character:
    """Base character class"""
    def __init__(self, name, health, attack):
        self.__name = name
        self.__health = health
        self.__attack = attack
    
    def get_name(self):
        return self.__name
    
    def get_health(self):
        return self.__health
    
    def take_damage(self, damage):
        self.__health -= damage
        if self.__health < 0:
            self.__health = 0
    
    def is_alive(self):
        return self.__health > 0
    
    def special_attack(self):
        pass

class Warrior(Character):
    """Warrior with strong melee attack"""
    def special_attack(self):
        damage = self.attack * 1.5
        print(f"Power slash for {damage} damage!")
        return damage

class Mage(Character):
    """Mage with magical abilities"""
    def special_attack(self):
        damage = self.attack * 2
        print(f"Fireball for {damage} damage!")
        return damage

class Rogue(Character):
    """Rogue with quick strikes"""
    def special_attack(self):
        damage = self.attack * 1.3
        print(f"Backstab for {damage} damage!")
        return damage

# Create party
warrior = Warrior("Conan", 100, 20)
mage = Mage("Gandalf", 60, 15)
rogue = Rogue("Legolas", 70, 18)

party = [warrior, mage, rogue]

print("=== Attacks ===")
for char in party:
    print(f"{char.get_name()}:")
    char.special_attack()
```

---

## Method Overriding vs Method Overloading

### Method Overriding (Supported)

Different classes, same method name:

```python
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        import math
        return math.pi * self.radius ** 2
```

### Method Overloading (Not Supported in Python)

Python doesn't support traditional overloading, but you can use default arguments:

```python
class Printer:
    def print_message(self, message, times=1):
        for _ in range(times):
            print(message)

printer = Printer()
printer.print_message("Hello")           # Hello
printer.print_message("Hi", 3)           # Hi Hi Hi
```

---

## Abstract Base Classes (ABC)

Force subclasses to implement specific methods:

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):
    @abstractmethod
    def start(self):
        pass
    
    @abstractmethod
    def stop(self):
        pass

class Car(Vehicle):
    def start(self):
        print("Car starting...")
    
    def stop(self):
        print("Car stopping...")

# Can't create Vehicle directly
# vehicle = Vehicle()  # Error!

# But can create subclass
car = Car()
car.start()                             # Car starting...
```

---

## Property Decorators

Use `@property` for cleaner getter/setter syntax:

```python
class Temperature:
    def __init__(self, celsius):
        self._celsius = celsius
    
    @property
    def fahrenheit(self):
        """Get Fahrenheit value"""
        return (self._celsius * 9/5) + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        """Set Fahrenheit value"""
        self._celsius = (value - 32) * 5/9

temp = Temperature(0)
print(temp.fahrenheit)                  # 32.0

temp.fahrenheit = 212
print(temp._celsius)                    # 100
```

---

## Project 1: School Management System

```python
class Person:
    def __init__(self, name, age):
        self._name = name
        self._age = age
    
    def get_info(self):
        return f"{self._name}, Age: {self._age}"

class Student(Person):
    def __init__(self, name, age, student_id):
        super().__init__(name, age)
        self.student_id = student_id
        self.grades = []
    
    def add_grade(self, grade):
        self.grades.append(grade)
    
    def get_average(self):
        if not self.grades:
            return 0
        return sum(self.grades) / len(self.grades)
    
    def get_info(self):
        return f"Student: {super().get_info()}, Average: {self.get_average():.2f}"

class Teacher(Person):
    def __init__(self, name, age, subject):
        super().__init__(name, age)
        self.subject = subject
        self.students = []
    
    def add_student(self, student):
        self.students.append(student)
    
    def get_info(self):
        return f"Teacher: {super().get_info()}, Subject: {self.subject}"

# Create objects
student1 = Student("Alice", 16, "S001")
student1.add_grade(85)
student1.add_grade(90)

teacher = Teacher("Mr. Smith", 45, "Math")
teacher.add_student(student1)

print(student1.get_info())              # Student: Alice, Age: 16, Average: 87.50
print(teacher.get_info())               # Teacher: Mr. Smith, Age: 45, Subject: Math
```

---

## Project 2: Payment System

```python
from abc import ABC, abstractmethod

class Payment(ABC):
    @abstractmethod
    def pay(self, amount):
        pass

class CreditCard(Payment):
    def __init__(self, card_number):
        self.card_number = card_number
    
    def pay(self, amount):
        print(f"Paid ${amount} with credit card {self.card_number[-4:]}")

class PayPal(Payment):
    def __init__(self, email):
        self.email = email
    
    def pay(self, amount):
        print(f"Paid ${amount} via PayPal ({self.email})")

class Bitcoin(Payment):
    def __init__(self, wallet):
        self.wallet = wallet
    
    def pay(self, amount):
        print(f"Paid {amount} BTC from wallet {self.wallet}")

# Process payment
def process_payment(payment_method, amount):
    payment_method.pay(amount)

# Try different payment methods
card = CreditCard("1234567890123456")
paypal = PayPal("user@gmail.com")
bitcoin = Bitcoin("1A1z7agoat2YTEVHQ68GeNrAv69est9Fg")

process_payment(card, 50)               # Paid $50 with credit card ...
process_payment(paypal, 50)             # Paid $50 via PayPal ...
process_payment(bitcoin, 0.001)         # Paid 0.001 BTC from wallet ...
```

---

## Exercises

### Exercise 1: Encapsulation

Create `encapsulation.py`:

```python
class Employee:
    def __init__(self, name, salary):
        self._name = name
        self.__salary = salary
    
    def get_salary(self):
        return self.__salary
    
    def raise_salary(self, amount):
        self.__salary += amount

emp = Employee("Alice", 50000)
print(emp.get_salary())
emp.raise_salary(5000)
print(emp.get_salary())
```

### Exercise 2: Inheritance

Create `inheritance.py`:

```python
class Transport:
    def __init__(self, speed):
        self.speed = speed

class Car(Transport):
    def drive(self):
        print(f"Driving at {self.speed} km/h")

car = Car(100)
car.drive()
```

### Exercise 3: Polymorphism

Create `polymorphism.py`:

```python
class Animal:
    def speak(self):
        pass

class Dog(Animal):
    def speak(self):
        return "Woof"

class Cat(Animal):
    def speak(self):
        return "Meow"

animals = [Dog(), Cat()]
for animal in animals:
    print(animal.speak())
```

---

## Key Takeaways

✓ Encapsulation hides internal data  
✓ Inheritance reuses code through hierarchy  
✓ Polymorphism allows objects to be used interchangeably  
✓ Use `super()` to call parent methods  
✓ Abstract classes force implementation  
✓ Private attributes use `__` prefix  

---

## Quick Reference

```python
# Encapsulation
class Account:
    def __init__(self, balance):
        self.__balance = balance
    
    def get_balance(self):
        return self.__balance

# Inheritance
class Dog(Animal):
    def speak(self):
        super().speak()
        print("Woof")

# Polymorphism
for animal in animals:
    animal.speak()
```

---

## Homework

1. ✓ Create a class with encapsulation
2. ✓ Create inheritance with 3 levels
3. ✓ Create 3 classes that use polymorphism
4. ✓ Create abstract base class with 2 implementations

Next hour: **Iterators, Generators, Decorators!**
