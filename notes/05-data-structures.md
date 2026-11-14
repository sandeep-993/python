# Data Structures

## Lists

Lists are ordered and mutable. They support indexing, slicing, and methods such as `.append()`, `.extend()`, `.insert()`, `.remove()`, and `.pop()`.

## Tuples

Tuples are ordered and immutable. They are useful for fixed groups of values, such as coordinates.

## Dictionaries

Dictionaries map unique keys to values. Use `mapping[key]` when a key must exist, or `mapping.get(key)` when it may be absent.

## Sets

Sets store unique values and support membership tests and operations such as union (`|`), intersection (`&`), and difference (`-`).

## Comprehensions

```python
squares = [number ** 2 for number in range(5)]
```

A comprehension is useful for a clear, simple transformation; use a regular loop when it becomes hard to read.

## Practice

1. Remove duplicates from a list by converting it to a set.
2. Count how often each word occurs in a short sentence using a dictionary.
3. Create a list of the squares of even numbers from 0 to 20.
