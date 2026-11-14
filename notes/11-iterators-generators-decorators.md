# Iterators, Generators, and Decorators

## Iterators and generators

An iterator produces items one at a time. A generator function uses `yield` to produce values lazily, which can avoid building a complete collection in memory.

```python
def count_up_to(limit):
    number = 1
    while number <= limit:
        yield number
        number += 1
```

Use `next()` to request an iterator's next item; iteration ends with `StopIteration`.

## Decorators

A decorator wraps a function to add behavior. The `@decorator_name` syntax applies a decorator when defining a function. Learn to read and use decorators before writing complex ones.

## Practice

1. Write a generator that yields even numbers up to a limit.
2. Iterate through a generator with a `for` loop.
3. Write a simple decorator that prints a message before calling a function.
