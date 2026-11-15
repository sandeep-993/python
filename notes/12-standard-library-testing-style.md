# Standard Library, Testing, and Style — Interview Preparation

## Useful standard-library modules

- `collections`: `Counter`, `defaultdict`, and `deque`
- `itertools`: efficient iterator-building tools such as `chain`, `islice`, and `combinations`
- `functools`: `lru_cache`, `partial`, and `wraps`
- `pathlib`: object-oriented file paths
- `datetime`: dates, times, and timedeltas
- `json` and `csv`: common data formats
- `heapq`: heap-based priority queues
- `re`: regular expressions
- `statistics`: basic statistical functions

Use a library tool when it makes the code clearer, but understand its behavior well enough to explain it.

## Testing fundamentals

A test checks behavior against an expectation. Good tests cover normal behavior, boundaries, empty inputs, invalid inputs, and regressions. Unit tests should be focused and repeatable.

### `unittest` example

```python
import unittest

def add(left, right):
    return left + right

class AddTests(unittest.TestCase):
    def test_adds_integers(self):
        self.assertEqual(add(2, 3), 5)

if __name__ == "__main__":
    unittest.main()
```

Run the file with `python filename.py`, or use test discovery for a larger test suite. `pytest` is a popular third-party test runner; it is not part of the Python standard library.

## What to test in an interview solution

For a function that processes a sequence, consider:

- empty input and one-element input
- duplicates and already-sorted/reversed input
- negative or zero values if allowed
- missing result or invalid input
- larger input and complexity constraints

Do not add tests mechanically; relate them to the problem's contract and constraints.

## Type hints

```python
def average(values: list[float]) -> float:
    if not values:
        raise ValueError("values cannot be empty")
    return sum(values) / len(values)
```

Type hints document interfaces and help static analysis. They do not automatically validate runtime values. For reusable APIs, `typing` offers types such as `Iterable`, `Sequence`, `Mapping`, `Callable`, and `Optional` (or `T | None` in modern Python).

## Style and readability

PEP 8 is the commonly used Python style guide. Important habits:

- use four spaces for indentation
- use `snake_case` for functions and variables, `CapWords` for classes
- choose descriptive names
- keep functions focused
- use blank lines to separate logical units
- write docstrings for public behavior when useful
- avoid unnecessary cleverness and deeply nested logic

Formatting and linting tools can automate style checks, but they do not replace sound design.

## Debugging and code review

Read tracebacks from the bottom upward to locate the exception and failing line, then inspect the call path. Reproduce the smallest failing case. A good review checks correctness, edge cases, readability, complexity, and unintended mutation.

## Interview questions

- What is a unit test, and what should it cover?
- How are `unittest` and `pytest` related or different?
- Are type hints enforced by Python at runtime?
- When would you use `Counter`, `deque`, or `lru_cache`?
- How do you approach a bug from a traceback?

## Practice

1. Write unit tests for a function that handles empty and non-empty input.
2. Use `Counter` to find the most common words in text.
3. Add type hints and a docstring to a small utility function.
4. Use `pathlib` to build a path and test whether it exists.
5. Given a failing test, reduce it to a minimal reproducible example.

## Interview checklist

Explain the purpose of tests, meaningful edge cases, runtime versus static type checking, standard-library choices, and readable style.
