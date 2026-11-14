# Standard Library, Testing, and Style

## Standard library

Explore useful modules including `pathlib` (paths), `collections` (specialized containers), `datetime` (dates and times), `itertools` (iterator tools), and `json` (JSON data).

## Testing

Start with small functions and tests that check expected behavior. Python's built-in `unittest` is available without installing packages. Test normal cases, boundary cases, and invalid input.

```python
import unittest

def double(value):
    return value * 2

class DoubleTests(unittest.TestCase):
    def test_integer(self):
        self.assertEqual(double(4), 8)
```

## Readability and type hints

Use descriptive names, consistent formatting, and short focused functions. PEP 8 is the common Python style guide. Type hints can document expected inputs and outputs:

```python
def greet(name: str) -> str:
    return f"Hello, {name}!"
```

Type hints help readers and tools; Python does not enforce them automatically at runtime.

## Practice

1. Use `pathlib` to list files in a directory.
2. Write tests for a function you created in an earlier topic.
3. Add type hints and a docstring to one practice function.
