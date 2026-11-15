# Operators and Control Flow

## Arithmetic operators

```python
print(5 + 3)
print(10 - 2)
print(4 * 6)
print(10 / 3)
print(10 // 3)
print(10 % 3)
print(2 ** 3)
```

- `/` gives a float
- `//` is floor division
- `%` is modulus
- `**` is exponentiation

## Comparison operators

```python
print(5 > 3)
print(5 == 5)
print(3 != 4)
```

## Logical operators

```python
print(True and False)
print(True or False)
print(not True)
```

## If, elif, else

```python
marks = 76
if marks >= 90:
    grade = "A"
elif marks >= 75:
    grade = "B"
else:
    grade = "C"
print(grade)
```

## Loops

### For loop

```python
for i in range(1, 6):
    print(i)
```

### While loop

```python
count = 1
while count <= 5:
    print(count)
    count += 1
```

## Break and continue

```python
for i in range(1, 10):
    if i == 5:
        break
    print(i)
```

```python
for i in range(1, 6):
    if i == 3:
        continue
    print(i)
```

## Interview patterns

- Use `if` to test conditions.
- Use loops for repeated tasks.
- Use `break` to stop early.
- Use `continue` to skip items.

## Practice questions

1. Check whether a number is positive, negative, or zero.
2. Print even numbers from 1 to 20.
3. Find the sum of numbers from 1 to 100.
4. Write a program to print the multiplication table of 5.
