# Operators and Control Flow — Interview Preparation

## Arithmetic and precedence

Python supports `+`, `-`, `*`, `/`, `//`, `%`, and `**`. Parentheses make intended grouping explicit. Exponentiation binds more tightly than unary minus: `-2 ** 2` is `-(2 ** 2)`.

```python
print(7 / 2)   # 3.5
print(7 // 2)  # 3
print(-7 // 2) # -4: floor division rounds down
print(7 % 2)   # 1
print(2 ** 3)  # 8
```

The `%` result follows Python's modulo rules, so it has the sign of the divisor. Do not assume integer division truncates toward zero for negative values.

## Comparisons and chained comparisons

Comparisons include `==`, `!=`, `<`, `<=`, `>`, and `>=`. Python supports readable chaining:

```python
if 0 <= score <= 100:
    print("valid score")
```

Avoid comparing values of incompatible types; ordering comparisons may raise `TypeError`.

## Boolean operators and short-circuiting

`and` and `or` short-circuit: the second operand is evaluated only if needed. They return one of their operands, not necessarily a `bool`.

```python
name = user_name or "Guest"
result = items and items[0]  # may be [] or the first item
```

Use `not` for logical negation. Be careful when relying on truthy/falsy values if `0`, `None`, and empty values have different meanings.

## Conditional statements

```python
if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
else:
    grade = "Keep practicing"
```

Conditions are evaluated top to bottom; only the first matching branch runs.

## Loops

Use `for` to iterate over an iterable. `range(stop)` excludes `stop`; `range(start, stop, step)` can specify bounds and stride.

```python
for index, value in enumerate(["a", "b", "c"]):
    print(index, value)
```

Use `while` when repetition depends on a condition, and ensure the loop can make progress toward termination.

## Loop control and loop `else`

- `break` exits the nearest loop.
- `continue` skips to the next iteration.
- `pass` is a placeholder statement.
- A loop's `else` suite runs if the loop finishes normally, but not if it exits with `break`.

```python
for number in range(2, 10):
    if number == 5:
        break
else:
    print("No break occurred")
```

The loop `else` is less common; use it only when it makes the no-break condition clearer.

## Useful iteration tools

```python
for left, right in zip([1, 2], ["a", "b"]):
    print(left, right)

for value in reversed([1, 2, 3]):
    print(value)
```

`zip()` stops at the shortest iterable by default. In supported Python versions, `zip(..., strict=True)` can check equal lengths.

## Common interview patterns

- Accumulate a total with a loop or `sum()`.
- Track a best-so-far value, such as a minimum or maximum.
- Use `enumerate()` when both index and value are needed.
- Use an early `return` or `break` when the result is known.
- Avoid off-by-one errors by checking `range`'s exclusive endpoint.

## Example: find a maximum without `max()`

```python
def largest(values):
    if not values:
        raise ValueError("values must not be empty")
    best = values[0]
    for value in values[1:]:
        if value > best:
            best = value
    return best
```

This takes O(n) time and O(1) extra space.

## Common pitfalls

- Infinite `while` loops caused by a condition that never changes.
- Assuming `range(1, 5)` includes 5.
- Using `and`/`or` without considering that they return operands.
- Modifying a collection while iterating over it; often build a new collection instead.
- Misunderstanding negative floor division.

## Practice

1. Determine whether an integer is within a specified inclusive range.
2. Write a loop that finds the first matching item and uses `else` to report no match.
3. Print a multiplication table using nested loops.
4. Find the sum and maximum of a non-empty list in one pass.
5. Explain the output of `-7 // 2`, `bool("0")`, and `0 or "fallback"`.

## Interview checklist

Explain operator precedence, floor division, short-circuit behavior, iteration boundaries, loop termination, and the time/space cost of a loop.
