# Object-Oriented Programming — Interview Preparation

Object-oriented programming groups state and behavior into objects. Use classes when they make the domain and responsibilities clearer; not every small program needs a class.

## Classes, instances, and `self`

A class defines behavior and creates instances. `self` is the conventional name for the instance passed to an instance method.

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance

    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("amount must be positive")
        self.balance += amount
```

`__init__` initializes a newly created instance; `__new__` is responsible for creating it and is usually not overridden in ordinary application code.

## Instance and class attributes

Instance attributes belong to a particular object. Class attributes are shared through the class unless shadowed by an instance attribute.

```python
class Employee:
    category = "staff"  # class attribute

    def __init__(self, name):
        self.name = name  # instance attribute
```

Avoid mutable class attributes for per-instance data unless shared state is intentional.

## Instance, class, and static methods

- Instance methods receive `self` and operate on an instance.
- Class methods use `@classmethod` and receive `cls`; often used for alternate constructors.
- Static methods use `@staticmethod` and receive no implicit instance or class argument; use them for related utility behavior when appropriate.

```python
class Temperature:
    def __init__(self, celsius):
        self.celsius = celsius

    @classmethod
    def from_fahrenheit(cls, value):
        return cls((value - 32) * 5 / 9)
```

## Encapsulation and properties

Python uses conventions: a leading underscore means “internal use”; name-mangled double-underscore attributes discourage accidental subclass collisions but are not security controls. Properties allow attribute-style access with controlled behavior.

```python
class Person:
    def __init__(self, age):
        self.age = age

    @property
    def age(self):
        return self._age

    @age.setter
    def age(self, value):
        if value < 0:
            raise ValueError("age cannot be negative")
        self._age = value
```

## Inheritance and polymorphism

Inheritance models a genuine “is-a” relationship and allows a subtype to reuse or override behavior. `super()` delegates to the next implementation in the method resolution order (MRO).

```python
class Animal:
    def speak(self):
        raise NotImplementedError

class Dog(Animal):
    def speak(self):
        return "woof"
```

Polymorphism means callers can use a common interface while different objects provide their own behavior. Python also supports duck typing: behavior matters more than an explicit declared parent class.

## Composition versus inheritance

Composition means one object contains or uses another object. Prefer it when the relationship is “has-a” or when behavior can be assembled flexibly. Deep inheritance can make behavior hard to understand.

## Special methods

Special methods define interactions with language operations. Examples include `__repr__` for debugging representation, `__str__` for user-facing text, `__len__` for `len(obj)`, and `__eq__` for equality. Implement them consistently and understand the contract of the operation.

## Dataclasses

For classes primarily storing data, `dataclasses` can generate methods such as `__init__` and `__repr__`.

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: float
    y: float
```

Use `default_factory` for mutable dataclass defaults.

## Interview questions

- What are a class, an object, and an instance attribute?
- Compare instance methods, class methods, and static methods.
- Explain inheritance, overriding, polymorphism, and MRO.
- When is composition preferable to inheritance?
- What do underscore conventions mean in Python?
- What is the purpose of `super()`?

## Practice

1. Implement a `BankAccount` with validated deposit and withdrawal methods.
2. Create a base class and two subclasses that implement the same interface.
3. Model a `Library` that contains `Book` instances using composition.
4. Create a dataclass for a 2D point and add a useful method.

## Interview checklist

Explain the design tradeoff, state ownership, method dispatch, validation, and why a class is appropriate for the problem.
