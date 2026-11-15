# Exceptions

Exceptions are errors that occur during program execution. They are used to signal abnormal situations without crashing silently.

## Basic try-except

```python
try:
    x = int("abc")
except ValueError:
    print("That is not a valid integer")
```

## finally

```python
try:
    value = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
finally:
    print("This always runs")
```

## Raising exceptions

```python
def divide(a, b):
    if b == 0:
        raise ValueError("Denominator cannot be zero")
    return a / b
```

## Common built-in exceptions

- `ValueError`
- `TypeError`
- `ZeroDivisionError`
- `FileNotFoundError`
- `IndexError`
- `KeyError`

## Interview tip

Catch specific exceptions instead of catching everything. Avoid broad `except:` unless you know exactly why.

## Practice questions

1. Read an integer from input and handle invalid input gracefully.
2. Write a function that raises `ValueError` for negative input.
3. Explain why `finally` is useful.
