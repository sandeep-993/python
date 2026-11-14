# File Handling

Use `pathlib.Path` for paths and a context manager (`with`) to ensure files are closed reliably.

```python
from pathlib import Path

path = Path("example.txt")
path.write_text("Hello, file!\n", encoding="utf-8")
text = path.read_text(encoding="utf-8")
print(text)
```

Common `open()` modes include `"r"` (read), `"w"` (write, replacing existing content), and `"a"` (append). Choose an encoding explicitly for text files. For structured data, Python's `json` and `csv` modules are useful.

## Practice

1. Write three lines to a file and read them back.
2. Append a new line without replacing existing content.
3. Store a dictionary as JSON, then load it back.
