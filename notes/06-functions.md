# Functions

Functions are reusable blocks of code that perform a specific task. They make programs easier to read, test, and maintain.

## Function definition

```python
def greet(name):
    print(f"Hello, {name}!")


greet("Asha")
```

## Return values

```python
def add(a, b):
    return a + b

result = add(2, 3)
print(result)
```

## Parameters and arguments

```python
def power(base, exponent=2):
    return base ** exponent

print(power(3))
print(power(3, 3))
```

## Scope

```python
x = 10

def demo():
    x = 20
    print(x)

demo()
print(x)
```

`x` inside the function is local to that function unless you use `global` deliberately. In general, avoid using globals and instead pass values as parameters.

## `*args` and `**kwargs`

```python
def show(*args, **kwargs):
    print(args)
    print(kwargs)

show(1, 2, 3, name="Asha", city="Pune")
```

## Recursion

```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n - 1)

print(factorial(5))
```

## Common interview questions

- What is the difference between parameters and arguments?
- How do default arguments work?
- What is variable scope?
- How do you write a recursive function?
- Why is `global` usually avoided?

## Practice questions

1. Write a function to calculate the square of a number.
2. Write a function to check if a number is even.
3. Write a function to reverse a list using recursion.
4. Write a function that accepts arbitrary arguments and prints them.

## Interview tip

A good answer is not just syntax; explain how the function organizes logic and whether it returns a value or acts on side effects.
