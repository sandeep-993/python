# Iterators, Generators, and Decorators — Interview Preparation

## Iterable versus iterator

An iterable can provide an iterator, usually through `iter(obj)`. An iterator produces values with `next()` and remembers its current state. When exhausted, it raises `StopIteration`.

```python
values = [10, 20]
iterator = iter(values)
print(next(iterator))  # 10
print(next(iterator))  # 20
```

A list is iterable but is not itself an iterator. A `for` loop obtains an iterator and handles exhaustion automatically.

## Iterator protocol

An iterator implements `__iter__()` returning itself and `__next__()` returning the next value or raising `StopIteration`. Most application code should use existing iterables or generators rather than implementing this protocol manually.

## Generator functions

A function containing `yield` creates a generator. Its execution pauses at each `yield` and resumes when the next value is requested.

```python
def countdown(start):
    while start > 0:
        yield start
        start -= 1

for value in countdown(3):
    print(value)
```

Generators are lazy: they can process a stream without storing every result at once. They are usually single-use; once exhausted, they do not restart automatically.

## Generator expressions

```python
squares = (number * number for number in range(1_000_000))
first_three = [next(squares) for _ in range(3)]
```

A generator expression avoids building a full list up front. It is useful when values are consumed once; a list is better when repeated access or reuse is required.

## `yield from`

`yield from iterable` delegates iteration to another iterable or generator and can simplify generator composition.

## Decorators

A decorator is a callable that takes a function (or class) and returns a replacement, often a wrapper. `@decorator` is equivalent to rebinding the function through the decorator.

```python
from functools import wraps

def announce(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print(f"Calling {func.__name__}")
        return func(*args, **kwargs)
    return wrapper

@announce
def greet(name):
    return f"Hello, {name}"
```

`functools.wraps` preserves useful metadata such as the original function's name and docstring. A wrapper should normally accept `*args, **kwargs` and return the wrapped function's result.

## Decorators with arguments

A decorator that accepts configuration usually has an outer function returning the actual decorator, which then returns a wrapper. This is a closure: the wrapper remembers values from its enclosing scope.

## Common interview questions

- What is the difference between an iterable and an iterator?
- How does a generator differ from returning a list?
- What happens when a generator is exhausted?
- What does `yield` do to function execution?
- What is a decorator, and why use `functools.wraps`?
- What does `*args, **kwargs` preserve in a wrapper?

## Performance and pitfalls

- Laziness can reduce memory, but it does not make every computation faster.
- A generator can be exhausted; create a new generator if another pass is needed.
- Do not use a generator when the data must be indexed or traversed repeatedly.
- Decorators can affect debugging and signatures; preserve metadata and behavior.
- A decorator wrapper should return the wrapped function's return value.

## Practice

1. Write a generator that yields even numbers up to a limit.
2. Write a generator that reads and transforms items one at a time.
3. Create a timing or logging decorator that accepts any function arguments and returns its result.
4. Add a configurable decorator that repeats a function a specified number of times.
5. Explain the memory difference between a list comprehension and a generator expression.

## Interview checklist

Be prepared to explain lazy evaluation, iterator state, exhaustion, generator memory behavior, closures, wrapper signatures, and metadata preservation.
