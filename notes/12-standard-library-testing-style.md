# Standard Library, Testing, and Style

## Standard library

Python provides many useful modules.

```python
import math
import random
import datetime
```

Examples:

- `math` for mathematical functions
- `random` for randomness
- `datetime` for dates and times
- `json` for JSON handling
- `collections` for specialized containers

## Testing

Testing helps verify behavior before deployment. The standard library has `unittest`.

```python
import unittest

class TestExample(unittest.TestCase):
    def test_add(self):
        self.assertEqual(2 + 2, 4)
```

## Type hints

```python
def add(a: int, b: int) -> int:
    return a + b
```

Type hints help readability and static analysis, but Python does not enforce them by default.

## PEP 8

PEP 8 is Python's style guide. Follow it for readable code:

- use 4 spaces for indentation
- add blank lines between functions
- keep function names in lowercase with underscores
- use descriptive names

## Practice questions

1. Use `math.sqrt()` to calculate a square root.
2. Write a small `unittest` case for a function.
3. Add type hints to a function and explain their benefit.
