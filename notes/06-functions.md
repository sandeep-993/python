# Functions — Interview Preparation

Functions package behavior into reusable units. A well-designed function has a clear purpose, explicit inputs, a useful return value, and limited side effects.

## Defining and calling functions

```python
def add(left, right):
    """Return the sum of two values."""
    return left + right

answer = add(2, 3)
```

A function without an explicit `return` returns `None`. `print()` displays a value; it does not return that value to the caller.

## Parameters and argument kinds

Python supports positional-only, positional-or-keyword, keyword-only, and variable-length parameters. Keyword-only parameters follow `*` or `*args`.

```python
def connect(host, /, port=8000, *, timeout=5):
    return host, port, timeout

connect("localhost", timeout=2)
```

Use keyword arguments when they make calls more readable. Default values are evaluated once, when the function is defined.

## Mutable default argument pitfall

Do not use a mutable object such as `[]` as a default when each call should get a fresh object.

```python
def collect(value, items=None):
    if items is None:
        items = []
    items.append(value)
    return items
```

## `*args` and `**kwargs`

`*args` collects extra positional arguments into a tuple. `**kwargs` collects extra keyword arguments into a dictionary.

```python
def describe(*args, **kwargs):
    return args, kwargs
```

They can also unpack an iterable or mapping in a call: `function(*values, **options)`.

## Scope and name lookup

Python uses the LEGB lookup rule: Local, Enclosing, Global, Built-in. Assigning to a name inside a function usually makes it local unless declared `global` or `nonlocal`. Prefer parameters and return values over global mutable state.

```python
factor = 3

def scale(number):
    return number * factor
```

## Functions are objects

Functions can be assigned to names, passed as arguments, and returned from other functions. This enables callbacks, closures, and decorators.

```python
def apply(operation, value):
    return operation(value)

print(apply(abs, -4))
```

A `lambda` creates a small anonymous expression function. Use `def` when behavior needs a name, documentation, or multiple steps.

## Recursion

A recursive function calls itself and needs a base case. Python has a recursion limit, so an iterative solution is often preferable for deep input.

```python
def factorial(number):
    if number < 0:
        raise ValueError("number must be non-negative")
    if number <= 1:
        return 1
    return number * factorial(number - 1)
```

For large values, this recursive version can hit the recursion limit; discuss an iterative alternative when relevant.

## Generator functions

A function containing `yield` returns a generator and suspends/resumes execution as values are requested. See the [iterators and generators notes](11-iterators-generators-decorators.md).

## Type hints and docstrings

Annotations communicate intended types and are useful to editors and static checkers; they are not automatic runtime validation.

```python
def greet(name: str) -> str:
    """Return a greeting for name."""
    return f"Hello, {name}!"
```

## Interview discussion points

- Difference between a parameter and an argument.
- Difference between `return` and `print`.
- Mutable default arguments and the `None` sentinel pattern.
- Positional versus keyword-only parameters.
- LEGB scope and closure behavior.
- Recursion tradeoffs and base cases.
- Pure functions versus side effects.

## Practice

1. Write a function that returns the second-largest distinct number and define behavior for insufficient input.
2. Write a function with a keyword-only option.
3. Demonstrate the mutable-default pitfall, then fix it.
4. Implement factorial iteratively and recursively; compare their constraints.
5. Write a higher-order function that accepts another function.

## Interview checklist

State assumptions, validate input when appropriate, keep behavior focused, test edge cases, and explain time and space complexity.
