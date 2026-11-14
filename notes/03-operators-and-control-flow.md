# Operators and Control Flow

## Operators

- Arithmetic: `+`, `-`, `*`, `/`, `//`, `%`, `**`
- Comparison: `==`, `!=`, `<`, `<=`, `>`, `>=`
- Logical: `and`, `or`, `not`
- Assignment: `=`, `+=`, `-=`, and related forms

Use `==` to compare values; `=` assigns a value.

## Conditions

```python
score = 82
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
else:
    grade = "Keep practicing"
```

## Loops

Use `for` to iterate over items or a `range`, and `while` to repeat while a condition remains true. `break` exits a loop; `continue` skips to its next iteration.

```python
for number in range(1, 4):
    print(number)
```

## Practice

1. Check whether a number is positive, negative, or zero.
2. Print the numbers from 1 through 20, but skip multiples of 3.
3. Compute the sum of numbers from 1 to 100 using a loop.
