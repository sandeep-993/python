# Modules and Packages — Interview Preparation

## Module and package concepts

A module is a Python source file that can be imported. A package organizes modules under a package name. Regular packages commonly include `__init__.py`; Python also supports namespace packages without it.

Example layout:

```text
shop/
    __init__.py
    pricing.py
    inventory.py
```

## Import forms

```python
import math
from pathlib import Path
import collections as coll

print(math.sqrt(16))
print(Path("notes"))
```

Prefer imports that make the source of a name clear. Avoid `from module import *`, which can hide names and create collisions.

## Import behavior

Python finds modules using `sys.path`, which includes locations such as the script directory, configured paths, and installed packages. A module is normally initialized when first imported and cached in `sys.modules`; importing it again generally reuses the loaded module.

Be aware that local filenames such as `json.py`, `random.py`, or `collections.py` can shadow standard-library modules.

## Main guard

```python
def main():
    print("Run program behavior here")

if __name__ == "__main__":
    main()
```

The guard lets a file be run as a script without automatically executing its main routine when imported.

## Relative and absolute imports

Packages may use absolute imports such as `from shop.pricing import total` or relative imports such as `from .pricing import total`. Relative imports are intended for package code and require execution in a package context.

## Responsibilities and circular imports

Keep modules focused and avoid unnecessary import cycles. A circular import occurs when modules depend on each other during initialization; it often indicates that shared behavior should move to a third module or dependencies should be reorganized.

## Third-party packages and environments

Use a virtual environment to isolate project dependencies. A dependency list such as `requirements.txt` or project metadata helps reproduce an environment. Do not install packages into the system Python unless that is your deliberate setup.

Typical commands:

```text
python -m venv .venv
python -m pip install package_name
```

Activation commands vary by operating system and shell.

## Interview questions

- What is the difference between a module and a package?
- What does the main guard do?
- How does Python locate imports at a high level?
- What problems can wildcard imports and circular imports cause?
- Why can naming a file `json.py` cause import trouble?

## Practice

1. Create a module containing a reusable function and import it from a separate script.
2. Add a main guard and verify that importing the module does not run the main routine.
3. Create a small package with two modules and explicit imports.
4. Explain why a local file named `random.py` can break `import random`.

## Interview checklist

Be able to describe import organization, module initialization, the main guard, package layout, and dependency isolation.
