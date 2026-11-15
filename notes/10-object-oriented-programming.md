# Object-Oriented Programming

Object-oriented programming (OOP) organizes code into classes and objects. It helps model real-world entities and encapsulate behavior.

## Class and object

```python
class Dog:
    def __init__(self, name):
        self.name = name

    def bark(self):
        return f"{self.name} says woof!"


my_dog = Dog("Bruno")
print(my_dog.bark())
```

## Attributes and methods

- attributes store state
- methods define behavior

## Inheritance

```python
class Animal:
    def speak(self):
        return "Some sound"

class Cat(Animal):
    def speak(self):
        return "Meow"
```

## Encapsulation

Encapsulation means bundling data and methods together. In Python, it is usually accomplished with conventions like `_private_var` rather than strict access control.

## Polymorphism

Different objects can respond to the same method name in different ways.

```python
class Bird:
    def sound(self):
        return "tweet"

class Dog:
    def sound(self):
        return "bark"
```

## Interview questions

- What is the difference between a class and an object?
- What is inheritance?
- What is method overriding?
- Why is OOP useful in large programs?

## Practice questions

1. Create a `Student` class with `name` and `marks` attributes.
2. Add a method to calculate the average.
3. Create a `Teacher` class that inherits from `Person`.
