# Python Basics — Interview Preparation

## What Python is

Python is a high-level, general-purpose programming language. It is dynamically typed and commonly described as interpreted, though CPython compiles source to bytecode before execution. Python emphasizes readable syntax and indentation-defined blocks.

## Running code

Save code in a `.py` file and run it with `python filename.py` or `python3 filename.py`, depending on your environment. The interactive interpreter is useful for short experiments.

```python
print("Hello, Python!")
```

## Names, objects, and assignment

In Python, names refer to objects. Assignment binds a name; it does not necessarily copy an object.

```python
first = [1, 2]
second = first          # both names refer to the same list
second.append(3)
print(first)             # [1, 2, 3]
```

This distinction becomes important with mutable values and function arguments. Reassigning a name is different from mutating the object it refers to.

## Indentation and blocks

A colon starts a suite, and indentation marks its body. Use consistent four-space indentation.

```python
if 4 > 2:
    print("condition is true")
```

A missing colon or inconsistent indentation causes a syntax or indentation error.

## Comments and docstrings

Use `#` for a short comment about intent. A docstring documents a module, class, or function and appears as its first statement.

```python
def area(width, height):
    """Return the area of a rectangle."""
    return width * height
```

## Input and output

`input()` always returns a string. Convert it explicitly when numeric input is expected. `print()` can display multiple values and supports `sep` and `end` options.

```python
age_text = input("Age: ")
age = int(age_text)
print(f"Next year: {age + 1}")
```

In production code, anticipate invalid input and handle it appropriately.

## Truthiness

Falsy values include `False`, `None`, numeric zero, and empty collections or strings. Most other objects are truthy.

```python
items = []
if not items:
    print("No items")
```

Use explicit comparisons when the distinction matters; for example, `value is None` checks specifically for `None`.

## Script entry point

When a module is run directly, `__name__` is set to `"__main__"`. When imported, it has its module name.

```python
def main():
    print("Program starts here")

if __name__ == "__main__":
    main()
```

This keeps reusable definitions importable without running the script's main behavior.

## Interview talking points

- Python is dynamically typed; names are not declared with fixed types.
- Assignment binds names to objects; mutability affects what changes are visible through aliases.
- Indentation is part of Python's syntax.
- `input()` returns `str`; convert and validate before arithmetic.
- Use `is None` for the singleton `None`, and `==` for value equality.

## Common pitfalls

- Naming a variable `list`, `str`, or `sum` shadows a built-in.
- Assuming `input()` returns a number.
- Confusing `=` (assignment) with `==` (equality comparison).
- Assuming assignment makes a copy of a mutable object.
- Relying on side effects in code that should be importable.

## Practice

1. Read two numeric strings, convert them, and print their sum.
2. Demonstrate that two names can refer to the same list, then make an independent shallow copy.
3. Write a `main()` function and protect it with the script-entry-point guard.
4. Write a function with a docstring and call it from `main()`.

## Interview checklist

Explain names versus objects, indentation, truthiness, input conversion, and the difference between running a module and importing it.
