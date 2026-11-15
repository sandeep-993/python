# File Handling

Files store data outside of memory. Python gives easy tools for reading and writing text and structured data.

## Opening a file

```python
with open("sample.txt", "w") as file:
    file.write("Hello, Python!\n")
```

## Reading a file

```python
with open("sample.txt", "r") as file:
    content = file.read()
    print(content)
```

## File modes

- `"r"` read
- `"w"` write
- `"a"` append
- `"rb"` read binary
- `"wb"` write binary

## `pathlib`

```python
from pathlib import Path

path = Path("sample.txt")
path.write_text("Python file handling\n", encoding="utf-8")
print(path.read_text(encoding="utf-8"))
```

## Reading JSON

```python
import json

data = {"name": "Asha", "age": 25}
with open("data.json", "w") as file:
    json.dump(data, file)
```

```python
with open("data.json", "r") as file:
    loaded = json.load(file)
print(loaded)
```

## Interview points

- Always prefer `with open(...)` to ensure file closure.
- Use explicit encoding when working with text files.
- Handle missing files with exceptions.

## Practice questions

1. Write a list of names to a file and read it back.
2. Append a line to an existing file without overwriting it.
3. Read a JSON file and print the values.
