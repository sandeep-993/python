# File Handling — Interview Preparation

File handling lets a program persist and retrieve data. Interview questions often focus on safe resource management, modes, paths, encoding, and handling missing or malformed data.

## Use a context manager

`with` ensures a file is closed even if an exception occurs.

```python
with open("example.txt", "w", encoding="utf-8") as file:
    file.write("Python file handling\n")
```

For text files, specify an encoding such as UTF-8 rather than relying on a platform default.

## File modes

- `r`: read; file must exist
- `w`: write; creates or truncates the file
- `a`: append; creates if needed
- `x`: create exclusively; fails if it already exists
- `b`: binary mode, for example `rb` or `wb`
- `+`: update/read-write mode, used in combinations such as `r+`

Be cautious with `w`: it replaces existing contents.

## Reading strategies

```python
with open("example.txt", encoding="utf-8") as file:
    whole_text = file.read()

with open("example.txt", encoding="utf-8") as file:
    lines = file.readlines()

with open("example.txt", encoding="utf-8") as file:
    for line in file:
        print(line.rstrip("\n"))
```

Iterating over a file is usually more memory-efficient than loading a very large file all at once.

## Paths with `pathlib`

```python
from pathlib import Path

path = Path("data") / "input.txt"
if path.exists():
    text = path.read_text(encoding="utf-8")
```

Use `Path` for clearer, cross-platform path operations. Be aware of the current working directory when using relative paths.

## Structured formats

### JSON

```python
import json

record = {"name": "Asha", "score": 91}
with open("record.json", "w", encoding="utf-8") as file:
    json.dump(record, file, indent=2)

with open("record.json", encoding="utf-8") as file:
    loaded = json.load(file)
```

JSON supports a limited set of data types; custom Python objects need explicit conversion. Invalid JSON raises `json.JSONDecodeError`.

### CSV

```python
import csv

with open("people.csv", "w", newline="", encoding="utf-8") as file:
    writer = csv.DictWriter(file, fieldnames=["name", "age"])
    writer.writeheader()
    writer.writerow({"name": "Asha", "age": 25})
```

Use the `csv` module rather than splitting lines manually, since quoted values can contain commas and other special cases.

## Errors and robust behavior

Handle expected errors such as `FileNotFoundError`, `PermissionError`, `UnicodeDecodeError`, or format parsing errors at an appropriate boundary. Do not suppress errors without reporting or recovering from them.

## Interview questions

- Why use `with open(...)`?
- What is the difference between `w` and `a`?
- Why specify an encoding?
- Why is iteration suitable for large text files?
- Why use the `csv` module instead of splitting on commas?
- What does a relative path resolve against?

## Practice

1. Write text to a file, append a second line, and read it line by line.
2. Handle a missing file without hiding unrelated errors.
3. Save a list of dictionaries as JSON and load it back.
4. Read a CSV file with `DictReader` and summarize a numeric column.
5. Explain why opening a large file with `read()` may use substantial memory.

## Interview checklist

Cover safe resource handling, modes and destructive behavior, encoding, path semantics, streaming, structured formats, and specific error handling.
