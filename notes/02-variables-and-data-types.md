# Variables and Data Types — Interview Preparation

## Names and dynamic typing

Python names refer to objects, and a name can later be bound to an object of a different type. The object has a type; the variable name is not permanently declared with one.

```python
value = 10
value = "ten"
```

Use `type(value)` to inspect a value's type and `isinstance(value, SomeType)` when checking type membership is appropriate.

## Common built-in types

- `int`: arbitrary-precision integers
- `float`: floating-point numbers; many decimal fractions are approximate in binary
- `complex`: complex values, such as `2 + 3j`
- `bool`: `True` or `False` (a subclass of `int`)
- `str`: immutable Unicode text
- `list`: mutable ordered sequence
- `tuple`: immutable ordered sequence
- `dict`: insertion-ordered key-value mapping
- `set` and `frozenset`: mutable and immutable sets of unique hashable values
- `NoneType`: the type of the singleton `None`

## Equality and identity

`==` checks value equality. `is` checks object identity (whether two names refer to the same object). Use identity for singletons such as `None`, not as a general substitute for equality.

```python
result = None
if result is None:
    print("No result")
```

## Type conversion

Constructors such as `int()`, `float()`, and `str()` convert compatible values. Conversion can raise exceptions, for example `int("hello")` raises `ValueError`.

```python
count = int("12")
price = float("3.5")
label = str(count)
```

`bool(value)` follows truthiness rules; `bool("False")` is `True` because the string is nonempty.

## Mutability

Mutable objects can be changed in place; immutable objects cannot. Common mutable types include lists, dictionaries, and sets. Integers, floats, strings, and tuples are immutable containers. A tuple can still contain a mutable object, so it is not necessarily deeply immutable.

```python
numbers = [1, 2]
alias = numbers
alias.append(3)
print(numbers)  # [1, 2, 3]

text = "cat"
text = "b" + text[1:]  # creates a new string and rebinds text
```

## Numeric details interviewers may ask

- `//` performs floor division; for negative values it rounds toward negative infinity.
- `/` returns a floating-point result for integers.
- Floating-point values can have representation error; use `decimal.Decimal` when decimal arithmetic requirements demand it.
- Python integers can grow beyond fixed machine-word ranges, limited by available memory.

## Type hints

Annotations document expected types and support static-analysis tools; Python does not generally enforce them automatically at runtime.

```python
def repeat(text: str, times: int) -> str:
    return text * times
```

## Common interview questions

1. What is the difference between equality and identity?
2. Why does a list change appear through two names that reference it?
3. Why is `bool("False")` true?
4. What is the difference between mutable and immutable objects?
5. Why can floating-point equality be surprising?

## Practice

1. Predict the output when a list is assigned to two names and mutated.
2. Demonstrate `==` and `is` with values and with `None`.
3. Convert user input to an integer and handle invalid conversion.
4. Explain why a tuple containing a list is not deeply immutable.
5. Compare `0`, `False`, `None`, and an empty string in truth-value tests.

## Interview checklist

Discuss dynamic typing, names and objects, identity versus equality, mutability, truthiness, conversion errors, and float precision.
