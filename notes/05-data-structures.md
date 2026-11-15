# Python Data Structures — Interview Preparation

This guide covers Python's built-in data structures, their behavior and typical costs, how to choose between them, and common interview patterns. Complexity figures are typical average-case costs for CPython; hash-table operations can degrade in unusual collision cases, and list append is amortized O(1).

## 1. Choosing a data structure

| Need | Good starting choice | Why |
|---|---|---|
| Ordered, editable sequence | `list` | Indexing, slicing, iteration, append |
| Fixed record or immutable sequence | `tuple` | Compact, immutable container; can be a dict key if its contents are hashable |
| Uniqueness or fast membership | `set` | Unique hashable elements; average O(1) membership |
| Lookup by key or counting | `dict` | Key-value mapping; average O(1) lookup and update |
| FIFO queue or deque | `collections.deque` | Efficient operations at both ends |
| Priority queue | `heapq` | Efficient access to the smallest item |

Before selecting a structure, clarify ordering requirements, whether duplicates matter, which operations are frequent, and whether values must be mutable.

## 2. Lists

A list is an ordered, mutable sequence. It allows duplicates and can contain values of different types, although using a consistent type is often clearer.

```python
values = [10, 20, 20, 30]
values[0] = 5
values.append(40)
print(values)  # [5, 20, 20, 30, 40]
```

### Common operations

```python
items = [3, 1, 2]
items.append(4)          # add one item at the end
items.extend([5, 6])    # add each item from an iterable
items.insert(1, 99)     # insert at an index
items.remove(99)        # remove first equal value; ValueError if absent
last = items.pop()      # remove and return last item
first = items.pop(0)    # remove first item; shifts remaining items
items.sort()            # sort this list in place
copy_sorted = sorted(items)  # create a new sorted list
```

`append(x)` adds `x` as one element. `extend(iterable)` adds each element from the iterable. `sort()` changes the list and returns `None`; `sorted()` returns a new list.

### List complexity

| Operation | Typical complexity |
|---|---:|
| Index access or assignment | O(1) |
| Append at end | Amortized O(1) |
| Pop from end | O(1) |
| Search with `in`, `index`, or `count` | O(n) |
| Insert or delete near the beginning/middle | O(n) |
| Slice of length k | O(k) |
| Sort | O(n log n) |

Use a list for indexed sequences and stacks. Avoid repeatedly using `pop(0)` for a queue; it shifts elements.

### Aliasing and copying

Assignment does not copy a list; both names refer to the same object.

```python
original = [1, 2]
alias = original
alias.append(3)
print(original)  # [1, 2, 3]
```

A shallow copy creates a new outer list, but nested objects are still shared:

```python
shallow = original.copy()
```

For nested structures, use `copy.deepcopy()` only when a recursive independent copy is actually needed.

### The mutable default argument pitfall

Default argument values are created once when the function is defined, not afresh for every call.

```python
def add_item(item, items=None):
    if items is None:
        items = []
    items.append(item)
    return items
```

## 3. Tuples

A tuple is an ordered, immutable sequence. Immutability prevents changing the tuple's membership or positions, though an object stored inside a tuple may itself be mutable.

```python
point = (4, 7)
x, y = point  # unpacking
single = (5,) # one-item tuple needs a comma
```

A tuple can be used as a dictionary key or set member only if all of its elements are hashable.

```python
locations = {(2, 3): "A"}  # valid: tuple contains hashable integers
# invalid_key = ([2, 3],)   # cannot be hashed because it contains a list
```

Use tuples for fixed records, coordinates, and multiple return values. For named fields, consider a `dataclass` or `NamedTuple` when it improves readability.

## 4. Dictionaries

A dictionary maps unique, hashable keys to values. Dictionaries preserve insertion order in modern Python (language guarantee since Python 3.7).

```python
person = {"name": "Mina", "age": 28}
person["city"] = "Pune"
print(person["name"])
print(person.get("country", "unknown"))
```

`mapping[key]` raises `KeyError` if the key is missing. `get(key, default)` returns a default instead. The `in` operator checks keys, not values.

```python
"name" in person       # checks keys
"Mina" in person.values()  # checks values
```

### Useful dictionary methods and idioms

```python
counts = {}
for value in ["a", "b", "a"]:
    counts[value] = counts.get(value, 0) + 1

for key, value in counts.items():
    print(key, value)
```

Other useful methods include `setdefault`, `update`, `pop`, `keys`, `values`, and `items`. In most counting/grouping problems, `collections.Counter` or `defaultdict` can make intent clearer.

### Dictionary complexity

| Operation | Typical average complexity |
|---|---:|
| Lookup, insert, update, delete by key | O(1) |
| Membership test by key | O(1) |
| Iterate over keys, values, or items | O(n) |

### Hashability

Dictionary keys must be hashable: their hash value must remain stable while they are used as keys, and equal values must have equal hashes. Common hashable types include integers, strings, and suitable tuples. Lists, sets, and dictionaries are unhashable.

## 5. Sets

A set stores unique hashable elements. Sets are useful for deduplication and fast membership checks. They do not provide positional indexing and should not be used when a particular iteration order is part of the required behavior.

```python
values = {1, 2, 2, 3}
print(values)  # contains 1, 2, 3
values.add(4)
values.discard(99)  # no error if absent
```

`remove(x)` raises `KeyError` when `x` is absent; `discard(x)` does not.

### Set operations

```python
left = {1, 2, 3}
right = {3, 4}

print(left | right)  # union: {1, 2, 3, 4}
print(left & right)  # intersection: {3}
print(left - right)  # difference: {1, 2}
print(left ^ right)  # symmetric difference: {1, 2, 4}
```

Typical membership, add, and remove operations are O(1) average case. Iterating over a set is O(n). Converting a list to a set removes duplicates but does not preserve the list's ordering requirement.

To remove duplicates while preserving first occurrence order:

```python
def unique_in_order(values):
    seen = set()
    result = []
    for value in values:
        if value not in seen:
            seen.add(value)
            result.append(value)
    return result
```

This works when the values are hashable.

## 6. Strings as sequences

Strings are immutable sequences of Unicode code points. They support indexing, slicing, iteration, and membership checks, but they are not a general-purpose mutable collection.

```python
text = "python"
print(text[0])       # p
print(text[1:4])     # yth
print("th" in text) # True
```

Repeated concatenation in a loop can do unnecessary copying. For many pieces, collect them and use `separator.join(parts)`.

```python
parts = ["core", "python", "interview"]
result = " ".join(parts)
```

For string-specific problems, consider normalization rules explicitly: case sensitivity, whitespace, punctuation, and Unicode handling can affect correctness.

## 7. Comprehensions

Comprehensions build a collection from an iterable, optionally filtering elements.

```python
squares = [number * number for number in range(6)]
even_squares = [number * number for number in range(6) if number % 2 == 0]
square_by_number = {number: number * number for number in range(6)}
unique_lengths = {len(word) for word in ["cat", "horse", "ox"]}
```

Prefer a normal loop when the comprehension becomes difficult to read or has complicated side effects. A generator expression, `(expression for item in iterable)`, produces values lazily rather than creating a full list immediately.

## 8. Useful standard-library structures

### `collections.Counter`

Counts hashable values and supports convenient frequency operations.

```python
from collections import Counter

frequency = Counter("banana")
print(frequency["a"])       # 3
print(frequency.most_common(1))
```

### `collections.defaultdict`

Creates a default value the first time a missing key is accessed. Useful for grouping.

```python
from collections import defaultdict

groups = defaultdict(list)
for name, team in [("Ari", "red"), ("Bo", "blue"), ("Cy", "red")]:
    groups[team].append(name)
```

### `collections.deque`

A double-ended queue supports efficient append and removal at either end. Use it for FIFO queues and breadth-first search.

```python
from collections import deque

queue = deque(["first", "second"])
queue.append("third")
next_item = queue.popleft()
```

Append and pop operations at either end are O(1). A list is usually better for random indexing; deque indexing in the middle is not its strength.

### `heapq`

`heapq` provides a min-heap using a regular list. The smallest item is at index 0.

```python
import heapq

heap = [7, 2, 5]
heapq.heapify(heap)       # O(n)
heapq.heappush(heap, 1)   # O(log n)
smallest = heapq.heappop(heap)  # O(log n)
```

For a max-heap pattern, Python versions before 3.14 commonly store negated numeric priorities, or use an appropriate wrapper for nonnumeric priorities. Verify the Python version and API available in the interview environment.

## 9. Common interview patterns

### Frequency counting

Use a dictionary or `Counter` to count items in O(n) average time.

```python
from collections import Counter

def most_common_item(items):
    if not items:
        return None
    return Counter(items).most_common(1)[0][0]
```

Clarify how ties should be handled if the problem specifies a particular tie-breaking rule.

### Membership with a set

Use a set to avoid repeated linear searches.

```python
def contains_duplicate(values):
    return len(values) != len(set(values))
```

This assumes values are hashable and uses O(n) additional space.

### Two-sum with a dictionary

Store values already seen and their indices. This achieves O(n) average time and O(n) extra space.

```python
def two_sum(numbers, target):
    seen = {}
    for index, number in enumerate(numbers):
        complement = target - number
        if complement in seen:
            return [seen[complement], index]
        seen[number] = index
    return None
```

This returns the first pair encountered and assumes the problem allows returning `None` when no pair exists. State any assumptions about duplicate use and output format.

### Stack

A list can serve as a last-in, first-out stack: `append()` pushes and `pop()` pops, both typically O(1) at the end.

```python
stack = []
stack.append("open")
stack.append("close")
top = stack.pop()
```

A common application is matching parentheses. Push opening symbols; for each closing symbol, check and remove the matching opener. At the end, the stack should be empty.

### Queue and breadth-first search

Use `deque`, not `list.pop(0)`, for an efficient FIFO queue. A queue is commonly used in level-order traversal and breadth-first search.

### Sorting and grouping

Sorting can simplify problems involving order, intervals, or adjacent duplicates. Grouping by a key is often a dictionary-of-lists pattern using `defaultdict(list)`.

## 10. Complexity cheat sheet

| Structure / operation | Typical time |
|---|---:|
| List index read/write | O(1) |
| List search | O(n) |
| List append / end pop | Amortized O(1) / O(1) |
| List insert/delete at front or middle | O(n) |
| List sort | O(n log n) |
| Tuple index | O(1) |
| Dict lookup/insert/delete | O(1) average |
| Set membership/add/remove | O(1) average |
| Deque append/pop at either end | O(1) |
| Heap push/pop | O(log n) |
| Heapify a list | O(n) |

Big-O describes how work grows with input size; it does not describe exact runtime. Mention auxiliary space as well as time when analyzing an interview solution.

## 11. Common pitfalls

- **Confusing mutation with return values:** `list.sort()` mutates and returns `None`; use `sorted(list)` for a new list.
- **Assuming copies are deep:** slicing and `.copy()` make shallow copies.
- **Using a list as a queue:** `pop(0)` costs O(n); prefer `deque.popleft()`.
- **Overlooking unhashable values:** lists and dictionaries cannot be set members or dictionary keys.
- **Using `dict[key]` for an optional key:** it raises `KeyError`; consider `.get()` or explicit membership.
- **Assuming sets are ordered:** do not depend on set iteration order.
- **Using `set()` when output order matters:** a set discards ordering and duplicates.
- **Ignoring empty input and duplicates:** test these edge cases deliberately.
- **Overstating complexity:** hash-table operations are average O(1), not an unconditional guarantee; list append is amortized O(1).

## 12. Interview problem set

Try to solve these before looking up an approach. For each, state assumptions, explain the chosen structure, analyze time and auxiliary space, and test edge cases.

1. Remove duplicates from a list while preserving order.
2. Return the first repeated value in a sequence.
3. Count the frequency of each word in a sentence.
4. Return the two indices whose values add to a target.
5. Group words that are anagrams of each other.
6. Find the intersection of two collections, including whether duplicates should be preserved.
7. Check whether brackets are balanced using a stack.
8. Implement a queue using two stacks.
9. Find the k largest values in a large input using a heap.
10. Merge overlapping intervals after sorting them.
11. Return the first non-repeating character while preserving original order.
12. Find the longest consecutive sequence of integers using a set.

## 13. How to present a solution in an interview

1. Restate the task and clarify edge cases and output format.
2. Start with a straightforward approach and its complexity.
3. Identify the operation that dominates the cost, such as repeated searching.
4. Select a structure that improves that operation (for example, a set or dictionary for average O(1) membership).
5. Explain the algorithm before coding.
6. Walk through a normal example and an edge case, such as empty input or duplicates.
7. State time complexity and additional space complexity accurately.

## Quick revision checklist

- Can you explain list, tuple, set, and dictionary differences?
- Do you know which types are mutable and which are hashable?
- Can you distinguish `append`, `extend`, `sort`, and `sorted`?
- Do you know why `deque` is preferred to `list.pop(0)` for queues?
- Can you use a dictionary for frequency counting and Two Sum?
- Can you explain average-case versus amortized complexity?
- Do you test empty input, duplicates, and missing keys?
