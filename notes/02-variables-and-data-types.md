# Variables and Data Types

## Variables

A variable name refers to a value. Python determines the value's type at runtime.

```python
name = "Ada"
age = 36
height = 1.65
is_learning = True
```

Use descriptive `snake_case` names, such as `total_price`.

## Common built-in types

- `int`: whole numbers, such as `42`
- `float`: decimal numbers, such as `3.14`
- `str`: text, such as `"hello"`
- `bool`: `True` or `False`
- `NoneType`: the type of `None`, which represents the absence of a value

Check a value with `type(value)` and convert with constructors such as `int()`, `float()`, and `str()` when appropriate.

```python
count = int("12")
print(type(count))
```

## Practice

1. Create variables for a book's title, page count, and whether you have read it.
2. Convert the string `"25"` to an integer and add 5.
3. Try converting `"hello"` to an integer. Observe and explain the result.
