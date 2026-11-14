# Functions

Functions package reusable behavior. Define one with `def`; use `return` to send a result back to the caller.

```python
def add(first, second):
    return first + second

result = add(2, 3)
```

## Parameters and arguments

Python supports positional and keyword arguments, default parameter values, and variable-length arguments using `*args` and `**kwargs`. Avoid mutable default values such as `items=[]`; use `None` and create a new list inside the function instead.

## Scope

Names created inside a function are generally local to it. Prefer passing values in and returning results rather than relying on global state.

## Practice

1. Write a function that returns whether a number is even.
2. Write a function that returns the largest value in a list.
3. Write a function with a default greeting name and call it with positional and keyword arguments.
