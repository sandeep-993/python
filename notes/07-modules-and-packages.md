# Modules and Packages

A module is a Python file containing Python code. A package is a directory containing modules and an `__init__.py` file (in older package layouts). Python modules help organize code and reuse functionality.

## Importing modules

```python
import math
print(math.sqrt(25))
```

```python
from math import sqrt
print(sqrt(25))
```

## Aliasing

```python
import math as m
print(m.pi)
```

## Creating your own module

Suppose you create `helpers.py`:

```python
def greet(name):
    return f"Hello, {name}!"
```

Then in another file:

```python
import helpers
print(helpers.greet("Asha"))
```

## `__name__ == "__main__"`

```python
def main():
    print("Running as script")

if __name__ == "__main__":
    main()
```

This pattern is commonly used to separate reusable code from script execution logic.

## Important interview points

- Use `import` for clarity.
- Use explicit imports rather than wildcard imports.
- Keep modules focused on a single responsibility.
- Avoid hidden dependencies between files.

## Practice questions

1. Create a module with a function and import it into another file.
2. Use `math` to calculate the area of a circle.
3. Write a script with `main()` and guard it with `if __name__ == "__main__"`.
