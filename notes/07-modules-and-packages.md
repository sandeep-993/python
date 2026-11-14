# Modules and Packages

A module is a Python file that can be imported. A package organizes modules in a directory.

```python
import math
print(math.sqrt(25))
```

You can import a module, selected names (`from math import sqrt`), or give a module an alias (`import math as m`). Prefer explicit imports and avoid wildcard imports.

## Script entry point

The `__name__` variable is `"__main__"` when a file is run directly. This pattern separates reusable definitions from script behavior:

```python
def main():
    print("Running the program")

if __name__ == "__main__":
    main()
```

## Practice

1. Create a module with a function and import it from another file.
2. Use `math` to calculate a square root.
3. Add a `main()` function and the script entry-point guard to a practice script.
