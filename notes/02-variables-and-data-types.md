# Variables and Data Types

## Variables

Variables are labels pointing to values stored in memory.

```python
count = 10
name = "Python"
```

### Naming rules

- names can include letters, digits, and underscores
- must not start with a digit
- should use `snake_case` for readability

## Built-in data types

### 1. Integer (`int`)

```python
age = 30
```

### 2. Float (`float`)

```python
price = 12.5
```

### 3. String (`str`)

```python
name = "Alice"
```

### 4. Boolean (`bool`)

```python
is_active = True
```

### 5. None

```python
result = None
```

`None` means “no value”. It is different from `0`, `False`, and `""`.

## Type conversion

```python
print(int("5"))
print(float("3.14"))
print(str(100))
print(bool(0))
```

## Mutable vs immutable

- Mutable: list, dict, set
- Immutable: int, float, str, tuple

```python
name = "Alice"
# name[0] = "B" -> TypeError
```

## Common interview questions

- What is the difference between `==` and `=`?
- Why is `None` different from `0` or `False`?
- What are mutable vs immutable types?
- Why does `str` not allow item assignment?

## Example challenge

```python
x = 10
y = x
x = 20
print(y)  # output: 10
```

Numbers are immutable; reassigning `x` creates a new value.

## Practice questions

1. Convert a string to int and multiply by 3.
2. Write a program to check if a variable is empty or None.
3. Explain the difference between mutable and immutable types.
4. Write a program to store a person’s name, age, and city in separate variables.
