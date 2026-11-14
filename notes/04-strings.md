# Strings

Strings are immutable sequences of text. Use single or double quotes to create them.

## Indexing and slicing

```python
word = "Python"
print(word[0])    # P
print(word[1:4])  # yth
print(word[-1])   # n
```

The slice end is exclusive. Negative indices count from the end.

## Useful methods and formatting

Methods such as `.lower()`, `.upper()`, `.strip()`, `.split()`, and `.replace()` return string values. They do not mutate the original string.

Use f-strings to insert values:

```python
name = "Sam"
print(f"Hello, {name}!")
```

## Practice

1. Ask for a sentence and print it in lowercase.
2. Count the words in a sentence using `.split()`.
3. Format a product name and price into a readable sentence with an f-string.
