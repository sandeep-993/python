# Object-Oriented Programming

A class defines a type of object; an instance is one object created from that class. `__init__` initializes instance state, and `self` refers to the current instance.

```python
class Counter:
    def __init__(self, value=0):
        self.value = value

    def increment(self):
        self.value += 1
```

## Design ideas

- Keep each class focused on a clear responsibility.
- Use composition (objects containing other objects) when it makes relationships clearer.
- Inheritance is useful for a genuine "is-a" relationship; avoid deep inheritance trees.
- Special methods such as `__str__` customize how objects work with built-in operations.

## Practice

1. Create a `Book` class with a title and author.
2. Add a method that returns a readable description.
3. Create a `Library` class that stores and lists several books.
