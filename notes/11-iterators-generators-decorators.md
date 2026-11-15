# Iterators, Generators, and Decorators

## Iterators

An iterator is an object that can be iterated over using `next()`.

```python
numbers = [1, 2, 3]
iter_obj = iter(numbers)
print(next(iter_obj))
print(next(iter_obj))
```

## Generators

A generator yields values one at a time. It is memory efficient for streams or large sequences.

```python
def count_up_to(n):
    i = 1
    while i <= n:
        yield i
        i += 1

for value in count_up_to(5):
    print(value)
```

## Decorators

Decorators wrap a function to add behavior.

```python
def uppercase_decorator(func):
    def wrapper():
        result = func()
        return result.upper()
    return wrapper

@uppercase_decorator
def greet():
    return "hello"

print(greet())
```

## Why interviewers ask about them

- they test knowledge of Python's iteration model
- generators highlight memory efficiency
- decorators show control over function behavior

## Practice questions

1. Write a generator that yields even numbers up to 20.
2. Create a decorator that logs the execution time of a function.
3. Explain the difference between iteration and direct indexing.
