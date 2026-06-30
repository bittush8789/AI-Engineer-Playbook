# Object-Oriented Programming (OOP) in Python

## What is OOP?

Object-Oriented Programming (OOP) is a programming paradigm that organizes code using **Objects** and **Classes**.

Instead of writing everything as functions, OOP models real-world entities such as:

- Employee
- Customer
- Vehicle
- Insurance Policy
- Claim
- User

as objects with:

```text
Attributes (Data)
+
Methods (Behavior)
```

---

# Why OOP?

## Without OOP

```python
employee_name = "Bittu"
employee_age = 25

print(employee_name)
```

Difficult to manage when applications grow.

---

## With OOP

```python
employee = Employee("Bittu", 25)
```

Cleaner and scalable.

---

# Benefits of OOP

- Code Reusability
- Better Organization
- Easier Maintenance
- Scalability
- Real-World Modeling
- Modularity

---

# OOP Terminologies

```text
Class
Object
Constructor
Attributes
Methods
Inheritance
Polymorphism
Encapsulation
Abstraction
```

---

# 1. Class

## Theory

A Class is a blueprint or template for creating objects.

Think of a class as a design.

Example:

```text
Car Blueprint
```

From one blueprint, many cars can be created.

---

## Syntax

```python
class ClassName:
    pass
```

---

## Example

```python
class Employee:
    pass
```

---

# 2. Object

## Theory

An Object is an instance of a class.

Example:

```text
Class = Employee

Object = Bittu
```

---

## Example

```python
class Employee:
    pass

emp1 = Employee()

print(emp1)
```

---

# 3. Constructor (__init__)

## Theory

A constructor initializes object attributes when an object is created.

Python constructor:

```python
__init__()
```

runs automatically.

---

## Example

```python
class Employee:

    def __init__(self):
        print("Object Created")

emp = Employee()
```

### Output

```text
Object Created
```

---

# Constructor with Parameters

```python
class Employee:

    def __init__(self, name, age):
        self.name = name
        self.age = age

emp = Employee("Bittu", 25)

print(emp.name)
print(emp.age)
```

### Output

```text
Bittu
25
```

---

# 4. Attributes

## Theory

Attributes are variables belonging to an object.

---

## Example

```python
class Employee:

    def __init__(self, name, age):
        self.name = name
        self.age = age

emp = Employee("Bittu", 25)

print(emp.name)
```

---

## Output

```text
Bittu
```

---

# 5. Methods

## Theory

Methods are functions inside a class.

They define object behavior.

---

## Example

```python
class Employee:

    def __init__(self, name):
        self.name = name

    def display(self):
        print("Employee Name:", self.name)

emp = Employee("Bittu")

emp.display()
```

### Output

```text
Employee Name: Bittu
```

---

# Understanding self

## Theory

`self` refers to the current object.

It allows access to object attributes and methods.

---

## Example

```python
class Student:

    def __init__(self, name):
        self.name = name

student = Student("Rahul")

print(student.name)
```

---

# OOP Pillars

There are four major pillars:

```text
Encapsulation
Inheritance
Polymorphism
Abstraction
```

---

# 6. Encapsulation

## Theory

Encapsulation means wrapping data and methods together into a single unit.

It also restricts direct access to sensitive data.

---

## Example

```python
class BankAccount:

    def __init__(self):
        self.balance = 1000

account = BankAccount()

print(account.balance)
```

---

# Protected Variable

```python
class Employee:

    def __init__(self):
        self._salary = 50000
```

Convention:

```text
_single_underscore
```

means protected.

---

# Private Variable

```python
class Employee:

    def __init__(self):
        self.__salary = 50000
```

Double underscore:

```text
__salary
```

means private.

---

## Example

```python
class Employee:

    def __init__(self):
        self.__salary = 50000

emp = Employee()

# print(emp.__salary)
```

Output:

```text
AttributeError
```

---

# Getter and Setter

```python
class Employee:

    def __init__(self):
        self.__salary = 50000

    def get_salary(self):
        return self.__salary

emp = Employee()

print(emp.get_salary())
```

### Output

```text
50000
```

---

# 7. Inheritance

## Theory

Inheritance allows one class to acquire properties of another class.

Promotes code reuse.

---

## Parent Class

```python
class Animal:

    def sound(self):
        print("Animal Sound")
```

---

## Child Class

```python
class Dog(Animal):

    def bark(self):
        print("Bark")
```

---

## Example

```python
class Animal:

    def sound(self):
        print("Animal Sound")

class Dog(Animal):

    def bark(self):
        print("Bark")

dog = Dog()

dog.sound()
dog.bark()
```

### Output

```text
Animal Sound
Bark
```

---

# Types of Inheritance

## Single Inheritance

```text
Animal
   │
   ▼
Dog
```

---

## Multilevel Inheritance

```text
Animal
   │
   ▼
Dog
   │
   ▼
Puppy
```

---

## Multiple Inheritance

```text
Father
Mother
   │
   ▼
Child
```

---

# 8. Polymorphism

## Theory

Polymorphism means:

```text
One Interface
Multiple Forms
```

Same method behaves differently.

---

## Example

```python
class Dog:

    def sound(self):
        print("Bark")

class Cat:

    def sound(self):
        print("Meow")

animals = [Dog(), Cat()]

for animal in animals:
    animal.sound()
```

### Output

```text
Bark
Meow
```

---

# Method Overriding

## Theory

Child class replaces parent class method.

---

## Example

```python
class Animal:

    def sound(self):
        print("Animal Sound")

class Dog(Animal):

    def sound(self):
        print("Bark")

dog = Dog()

dog.sound()
```

### Output

```text
Bark
```

---

# 9. Abstraction

## Theory

Abstraction hides implementation details and shows only essential features.

Example:

```text
Car Driver

Uses:
Start()
Stop()

Doesn't need engine details.
```

---

## Example

```python
from abc import ABC, abstractmethod

class Vehicle(ABC):

    @abstractmethod
    def start(self):
        pass

class Car(Vehicle):

    def start(self):
        print("Car Started")

car = Car()

car.start()
```

### Output

```text
Car Started
```

---

# Real AI Example

## Claim Object

```python
class Claim:

    def __init__(self, claim_id, amount):
        self.claim_id = claim_id
        self.amount = amount

    def predict_severity(self):

        if self.amount > 25000:
            return "High"

        return "Low"

claim = Claim(101, 50000)

print(claim.predict_severity())
```

### Output

```text
High
```

---

# Real Insurance Example

```python
class Policy:

    def __init__(self, policy_no, premium):
        self.policy_no = policy_no
        self.premium = premium

    def display(self):
        print(
            self.policy_no,
            self.premium
        )

policy = Policy(
    "POL123",
    5000
)

policy.display()
```

### Output

```text
POL123 5000
```

---

# OOP Interview Questions

### Q1. What is OOP?

```text
A programming paradigm based on objects and classes.
```

---

### Q2. What are the four pillars of OOP?

```text
Encapsulation
Inheritance
Polymorphism
Abstraction
```

---

### Q3. What is a Class?

```text
Blueprint for creating objects.
```

---

### Q4. What is an Object?

```text
Instance of a class.
```

---

### Q5. What is Inheritance?

```text
Mechanism to reuse code from another class.
```

---

### Q6. Difference between Overloading and Overriding?

```text
Overloading:
Same method name,
different parameters.

Overriding:
Child replaces parent method.
```

---

# Learning Path

```text
Class
   ↓
Object
   ↓
Constructor
   ↓
Attributes
   ↓
Methods
   ↓
Encapsulation
   ↓
Inheritance
   ↓
Polymorphism
   ↓
Abstraction
   ↓
Design Patterns
   ↓
Production AI Applications
```

# OOP Topics Most Important for AI Engineers

```text
Class
Object
Constructor
Methods
Inheritance
Polymorphism
Encapsulation
Abstraction
Composition
Dependency Injection
```

These OOP concepts are heavily used in:

```text
FastAPI
LangChain
LangGraph
CrewAI
AutoGen
PyTorch
TensorFlow
MLOps Platforms
AI Agent Systems
```