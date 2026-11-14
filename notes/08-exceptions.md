# Exceptions

Exceptions report errors or unusual conditions during execution. Handle only errors you can meaningfully recover from.

```python
try:
    quantity = int(input("Quantity: "))
except ValueError:
    print("Please enter a whole number.")
else:
    print(f"Quantity: {quantity}")
finally:
    print("Finished")
```

`else` runs when the `try` block succeeds; `finally` runs whether an exception occurred or not. Use `raise` to signal an error deliberately. Catch specific exception types rather than using a bare `except`.

## Practice

1. Safely convert user input to a number and handle invalid input.
2. Write a function that raises `ValueError` for an invalid argument.
3. Explain when `finally` is useful, even if an exception occurs.
