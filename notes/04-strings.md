# Strings (Interview Level)

Strings are sequences of characters. In Python, they are immutable, which means once a string is created, it cannot be changed in place.

## Why strings matter in interviews

Interview questions commonly test:

- indexing and slicing
- immutability
- string methods
- palindrome checks
- anagram checks
- counting characters
- reversing strings
- substring search
- memory and performance considerations

## 1. Creating strings

```python
name = "Python"
city = 'Delhi'
message = "Hello, world!"
empty = ""
```

Strings can be created using single quotes, double quotes, or triple quotes for multiline strings.

```python
multiline = """This is a
multiline string"""
```

## 2. String indexing

Each character in a string has an index.

```python
s = "python"
print(s[0])   # p
print(s[1])   # y
print(s[-1])  # n
print(s[-2])  # o
```

- Indexing starts from 0
- Negative indexes start from the end
- `s[-1]` is the last character

## 3. Slicing

Slicing extracts a part of a string.

```python
s = "python"
print(s[0:3])   # pyt
print(s[:3])    # pyt
print(s[3:])    # hon
print(s[::2])   # pto
print(s[::-1])  # nohtyp
```

Important rules:

- `start:end` is inclusive of start, exclusive of end
- `::2` means step size 2
- `[::-1]` reverses the string

## 4. Immutability

Strings are immutable.

```python
s = "hello"
# s[0] = 'H'   # This will raise TypeError
```

To change a string, create a new one.

```python
s = "hello"
s = "H" + s[1:]
print(s)  # Hello
```

### Interview point

This is why operations like concatenation or replacement create a new string instead of modifying the old one.

## 5. Common string methods

```python
s = "  Python Programming  "

print(s.strip())       # removes leading/trailing spaces
print(s.lower())       # lowercase
print(s.upper())       # uppercase
print(s.split())       # split into words
print(s.replace("P", "J"))
print(s.count("o"))   # count occurrences
print(s.find("Pr"))   # index of substring
print(s.startswith(" "))
print(s.endswith(" "))
```

### Important methods

- `strip()` – removes spaces/newlines at ends
- `split()` – converts into a list of words
- `join()` – joins list items into a single string
- `replace(old, new)` – replaces all occurrences
- `find(sub)` – returns index or -1 if not found
- `count(sub)` – counts occurrences
- `startswith()` / `endswith()` – checks prefix/suffix

### `join()` example

```python
words = ["Python", "is", "great"]
result = " ".join(words)
print(result)  # Python is great
```

## 6. String concatenation

```python
first = "Hello"
last = "World"
print(first + " " + last)  # Hello World
```

For many concatenations, `join()` is more efficient than repeated `+` operations.

```python
parts = ["Hello", "World", "Python"]
print(" ".join(parts))
```

## 7. String comparison

```python
print("apple" == "apple")   # True
print("apple" < "banana")  # True
print("A" < "a")            # True because uppercase ASCII values are lower
```

Comparison is lexicographic (alphabetical order based on Unicode values).

## 8. String formatting

### Old style

```python
name = "Alice"
print("Hello %s" % name)
```

### `format()`

```python
name = "Alice"
print("Hello {}".format(name))
```

### f-strings (preferred)

```python
name = "Alice"
age = 30
print(f"Hello {name}, you are {age} years old.")
```

### Interview tip

Use f-strings in modern Python because they are clearer and faster to read.

## 9. Checking membership

```python
s = "python"
print("py" in s)   # True
print("java" in s) # False
```

Useful for substring checks.

## 10. Reversing a string

```python
s = "hello"
reverse = s[::-1]
print(reverse)  # olleh
```

## 11. Palindrome check

A palindrome reads the same forward and backward.

```python
s = "racecar"
print(s == s[::-1])  # True
```

### Example function

```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")
    return s == s[::-1]

print(is_palindrome("A man a plan a canal Panama"))
```

## 12. Anagram check

Two strings are anagrams if they have the same characters in different orders.

```python
def is_anagram(s1, s2):
    return sorted(s1.lower().replace(" ", "")) == sorted(s2.lower().replace(" ", ""))

print(is_anagram("listen", "silent"))  # True
```

## 13. Frequency counting

```python
s = "banana"
count = {}
for ch in s:
    count[ch] = count.get(ch, 0) + 1
print(count)
```

This is a common interview problem: find character frequency.

## 14. Substring search

```python
s = "python programming"
print(s.find("prog"))
print(s.index("prog"))
```

- `find()` returns -1 if not found
- `index()` raises `ValueError` if not found

## 15. String methods you should know for interviews

```python
s = " hello world "

print(len(s))            # length
print(s.capitalize())   # Hello world 
print(s.title())         # Hello World 
print(s.isalpha())       # False
print(s.isdigit())       # False
print(s.isalnum())       # False
print(s.split())         # ['hello', 'world']
print("-".join(["a", "b", "c"]))
```

## 16. Common interview-style problems

### Problem 1: Reverse a string

```python
def reverse_string(s):
    return s[::-1]

print(reverse_string("python"))  # nohtyp
```

### Problem 2: Check if string is palindrome

```python
def is_palindrome(s):
    s = s.lower().replace(" ", "")
    return s == s[::-1]

print(is_palindrome("level"))  # True
```

### Problem 3: Remove spaces

```python
def remove_spaces(s):
    return "".join(s.split())

print(remove_spaces(" p y t h o n "))  # python
```

### Problem 4: Count vowels

```python
def count_vowels(s):
    vowels = "aeiou"
    return sum(1 for ch in s.lower() if ch in vowels)

print(count_vowels("hello"))  # 2
```

### Problem 5: First non-repeating character

```python
def first_non_repeating(s):
    freq = {}
    for ch in s:
        freq[ch] = freq.get(ch, 0) + 1
    for ch in s:
        if freq[ch] == 1:
            return ch
    return None

print(first_non_repeating("aabbcde"))  # c
```

## 17. Time complexity notes

- `len(s)` is O(1)
- slicing is O(k), where k is slice length
- `count`, `find`, `replace` are O(n)
- repeated concatenation in a loop can become O(n^2)

### Example:

```python
result = ""
for ch in "python":
    result += ch
```

This is less efficient than using `list` + `join()` when many pieces are added.

## 18. Best practices

- Prefer `f-strings` for formatting
- Use `join()` for combining many strings
- Use `split()` for tokenizing strings
- Avoid repeated string concatenation inside loops
- Normalize strings before comparison when case-insensitive matching is needed

```python
name = "Alice"
if name.lower() == "alice":
    print("Match")
```

## 19. Quick interview summary

You should be comfortable with:

- indexing and slicing
- immutability
- common string methods
- checking substring membership
- reversing and comparing strings
- palindrome, anagram, and frequent-character tasks
- using efficient approaches

## 20. Practice questions

1. Reverse a string without using slicing.
2. Check whether two strings are anagrams.
3. Find the longest repeated substring.
4. Count vowels and consonants in a string.
5. Remove duplicates from a string while preserving order.
6. Given a sentence, print the words in reverse order.
7. Check if a string contains only digits.
8. Find the first repeated character in a string.

## 21. Mini challenge

```python
def unique_chars(s):
    return len(set(s)) == len(s)

print(unique_chars("abcd"))  # True
print(unique_chars("abca"))  # False
```

## 22. Final interview takeaway

Strings are a core Python concept. In interviews, they often test your understanding of indexing, slicing, immutability, and efficient string manipulation. Be ready to explain both the logic and the Pythonic approach.

### Good answer style in interviews

"In Python, strings are immutable sequences of characters. Indexing and slicing are common operations, and methods like `split`, `join`, `replace`, and `find` are widely used. For performance-sensitive code, prefer `join()` over repeated concatenation and handle case normalization explicitly when comparing strings."

---

## Suggested revision exercises

```python
# 1. Reverse a string
s = "python"
print(s[::-1])

# 2. Check palindrome
s = "madam"
print(s == s[::-1])

# 3. Count vowels
sentence = "hello world"
print(sum(1 for ch in sentence.lower() if ch in 'aeiou'))

# 4. Remove spaces
text = "  python  string  "
print("".join(text.split()))
```

This file is a strong interview-level foundation for the Strings topic.
