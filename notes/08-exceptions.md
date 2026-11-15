# Exceptions — Interview Preparation

Exceptions represent errors or exceptional conditions during execution. Handling them well makes failure behavior explicit and recoverable.

## Exception flow

When an exception is raised, Python searches outward for a matching handler. If none is found, the program terminates that operation and displays a traceback.

```python
try:
    quantity = int("not a number")
except ValueError as error:
    print(f"Invalid quantity: {error}")
```

Catch the specific exception you expect and can handle. A broad `except Exception` can hide programming errors if used without care; avoid a bare `except` in ordinary application logic.

## `else` and `finally`

- `else` runs when the `try` suite completes without an exception.
- `finally` runs during cleanup whether or not an exception occurred.

```python
try:
    value = int("42")
except ValueError:
    print("Invalid number")
else:
    print(value * 2)
finally:
    print("Conversion attempt finished")
```

Context managers such as `with open(...)` are often the clearest way to ensure resources are released.

## Raising exceptions

Use `raise` to report invalid input or a violated contract.

```python
def percentage(value, total):
    if total <= 0:
        raise ValueError("total must be positive")
    return value / total * 100
```

Choose a meaningful built-in exception type. `ValueError` is often appropriate when a value has the right type but is unacceptable; `TypeError` often indicates the wrong type of operand.

## Re-raising and exception chaining

Use `raise` alone inside an `except` block to re-raise the current exception. `raise NewError(...) from error` preserves the original cause while exposing a domain-specific error.

```python
try:
    amount = int(raw_text)
except ValueError as error:
    raise ValueError("amount must be a whole number") from error
```

## Custom exceptions

Create a custom exception when callers need to distinguish a domain-specific failure.

```python
class InsufficientFundsError(Exception):
    """Raised when a withdrawal exceeds the available balance."""
```

Custom exceptions usually inherit from `Exception`, not directly from `BaseException`.

## Common exceptions

- `ValueError`: correct type, invalid value
- `TypeError`: inappropriate type or operation
- `KeyError`: missing mapping key
- `IndexError`: sequence index outside valid range
- `FileNotFoundError`: requested file does not exist
- `ZeroDivisionError`: division by zero
- `StopIteration`: iterator is exhausted (normally handled by iteration machinery)

## EAFP and validation

Python often favors EAFP (“easier to ask forgiveness than permission”): attempt an operation and handle a specific expected exception. Use direct validation when it makes the contract clearer. Avoid duplicate checks that introduce race conditions, especially with files and external resources.

## Common pitfalls

- Catching an exception and silently ignoring it.
- Catching an overly broad exception and masking a bug.
- Putting too much code inside `try`, making it unclear which operation failed.
- Using exceptions for ordinary control flow when a simple condition is clearer.
- Raising a generic exception without a useful message or type.

## Interview questions

1. Explain the difference between `except`, `else`, and `finally`.
2. When would you define a custom exception?
3. How does exception chaining help debugging?
4. Why is catching every exception usually a bad idea?
5. What is the difference between `ValueError` and `TypeError`?

## Practice

1. Parse an integer from user input and retry or report invalid input.
2. Validate a withdrawal and raise a custom exception for insufficient funds.
3. Wrap a low-level conversion error in a domain-specific error using `raise ... from ...`.
4. Use a context manager to guarantee a file is closed after an error.

## Interview checklist

Discuss precise exception types, cleanup, propagation, exception chaining, and the difference between expected invalid input and programming defects.
