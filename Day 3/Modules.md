
### 1. Investigate Circular Imports

Fix the circular import problem between `module_a.py` and `module_b.py`.

#### module_a.py:

```python
import module_b

def func_a():
    return "Function A"

print(module_b.func_b())
```

#### module_b.py:

```python
import module_a

def func_b():
    return "Function B"
```

**Task:** Resolve the circular dependency.

To resolve the circuar dependency we will import the modules at times when it is about to be used rather that importing it initially.

```python
# module_a.py
def func_a():
    return "Function A"
    # import module_b
import module_b
print(module_b.func_b())
```
```python
# module_b.py
def func_b():
    return "Function B"
    # import module_a
import module_a
print(module_a.func_a())
```

### 2. Dynamic Module Loading

Write a program that dynamically imports and executes a function from any module specified by the user.
Example:

```shell
Enter module name: math
Enter function name: sqrt
Enter argument: 25
Output: 5.0
```

```python
import importlib

def dynamic_import_and_execute():
    module_name = input("Enter module name: ")
    function_name = input("Enter function name: ")
    arg = input("Enter argument: ")
    
    try:
        module = importlib.import_module(module_name)
        if hasattr(module, function_name):
            func = getattr(module, function_name)
            result = func(float(arg))
            print(f"Output: {result}")
        else:
            print("Function not found in module.")
    except Exception as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    dynamic_import_and_execute()
```
### 3. Custom Module with Exception Handling

Create a custom module `calculator.py` that handles division by zero and invalid inputs gracefully.

```python
# calculator.py
def divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return "Cannot divide by zero."
    except Exception as e:
        return f"Error: {e}"
```

Import and use this module.


```python
import importlib
import calculator

def dynamic_import_and_execute():
    module_name = input("Enter module name: ")
    function_name = input("Enter function name: ")
    arg = input("Enter argument: ")
    
    try:
        module = importlib.import_module(module_name)
        if hasattr(module, function_name):
            func = getattr(module, function_name)
            result = func(float(arg))
            print(f"Output: {result}")
        else:
            print("Function not found in module.")
    except Exception as e:
        print(f"Error: {e}")

def test_calculator():
    print(calculator.divide(10, 2))
    print(calculator.divide(10, 0))
    print(calculator.divide(10, 'a'))

if __name__ == "__main__":
    dynamic_import_and_execute()
    test_calculator()
```
### 4. Advanced Import Strategies

Write a script that:

- Imports a module.
- Checks if a function exists.
- Executes it if available, otherwise gracefully handles the error.

```python
import importlib

def check_and_execute():
    module_name = input("Enter module name: ")
    function_name = input("Enter function name: ")
    arg = input("Enter argument: ")
    
    try:
        module = importlib.import_module(module_name)
        if hasattr(module, function_name):
            func = getattr(module, function_name)
            result = func(float(arg))
            print(f"Output: {result}")
        else:
            print(f"Function '{function_name}' not found in module '{module_name}'.")
    except Exception as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    check_and_execute()
```
### 5. Optimize Import Time

Use `time` module to measure import time for different methods (single import vs. importing everything).

```python
import time
start = time.time()
import math
end = time.time()
print(f"Import time: {end - start}")
```
```python
import importlib, time

def check_and_execute():
    try:
        module = importlib.import_module(input("Module: "))
        func = getattr(module, input("Function: "), None)
        print(f"Output: {func(float(input("Arg: ")))}" if func else "Function not found.")
    except Exception as e:
        print(f"Error: {e}")

def measure_import_time():
    for stmt in ["import math", "from math import *"]:
        start = time.time()
        exec(stmt)
        print(f"{stmt} time: {time.time() - start}")

if __name__ == "__main__":
    check_and_execute()
    measure_import_time()
```
### 6. Module Creation and Distribution

1. Create a Python package structure with `__init__.py`.
2. Write a `setup.py` to make it installable.
3. Install your package locally.
4. Import and test your package.

### 7. Investigate sys.path

Explore `sys.path` and add a custom directory to import modules from an unconventional path.

```python
import sys
sys.path.append('/custom/path/to/modules')
import mymodule
```

```python
import importlib, time, sys

def check_and_execute():
    try:
        module = importlib.import_module(input("Module: "))
        func = getattr(module, input("Function: "), None)
        print(f"Output: {func(float(input("Arg: ")))}" if func else "Function not found.")
    except Exception as e:
        print(f"Error: {e}")

def measure_import_time():
    for stmt in ["import math", "from math import *"]:
        start = time.time()
        exec(stmt)
        print(f"{stmt} time: {time.time() - start}")

def explore_sys_path():
    sys.path.append('/custom/path/to/modules')
    try:
        import mymodule
        print("Successfully imported mymodule from custom path.")
    except ImportError:
        print("Failed to import mymodule.")

if __name__ == "__main__":
    check_and_execute()
    measure_import_time()
    explore_sys_path()
```

### 8. Mocking Modules for Testing

Write a unit test for a function that imports a module. Use `unittest.mock` to mock the imported module.

```python
from unittest import mock
with mock.patch('math.sqrt', return_value=100):
    print(math.sqrt(25))  # Should print 100
```
```python
import importlib, time, sys
from unittest import mock

def check_and_execute():
    try:
        module = importlib.import_module(input("Module: "))
        func = getattr(module, input("Function: "), None)
        print(f"Output: {func(float(input("Arg: ")))}" if func else "Function not found.")
    except Exception as e:
        print(f"Error: {e}")

def measure_import_time():
    for stmt in ["import math", "from math import *"]:
        start = time.time()
        exec(stmt)
        print(f"{stmt} time: {time.time() - start}")

def explore_sys_path():
    sys.path.append('/custom/path/to/modules')
    try:
        import mymodule
        print("Successfully imported mymodule from custom path.")
    except ImportError:
        print("Failed to import mymodule.")

def test_mock_import():
    with mock.patch('math.sqrt', return_value=100):
        print(math.sqrt(25))  # Should print 100

if __name__ == "__main__":
    check_and_execute()
    measure_import_time()
    explore_sys_path()
    test_mock_import()
```
### 9. Import Side Effects

Investigate modules that run code at import time. Create a module that prints something as soon as it’s imported.

```python
print("This runs on import!")
```
```python
import importlib, time, sys, math
from unittest import mock

print("This runs on import!")

def check_and_execute():
    try:
        module, func_name = importlib.import_module(input("Module: ")), input("Function: ")
        print(f"Output: {getattr(module, func_name, lambda x: 'Function not found.')(float(input('Arg: ')))}")
    except Exception as e:
        print(f"Error: {e}")

def measure_import_time():
    for stmt in ["import math", "from math import *"]:
        start, end = time.time(), (exec(stmt), time.time())[1]
        print(f"{stmt} time: {end - start}")

def explore_sys_path():
    sys.path.append('/custom/path/to/modules')
    print("Successfully imported mymodule.") if 'mymodule' in sys.modules or __import__('mymodule') else print("Failed to import mymodule.")

def test_mock_import():
    with mock.patch('math.sqrt', return_value=100): print(math.sqrt(25))

if __name__ == "__main__":
    check_and_execute()
    measure_import_time()
    explore_sys_path()
    test_mock_import()
```
### 10. Investigate Python’s Import Caching

Explore `sys.modules` to understand how Python caches imports and how to reload modules.

```python
import sys
import mymodule
print(sys.modules['mymodule'])
```
```python
import importlib, time, sys, math
from unittest import mock

print("This runs on import!")

def check_and_execute():
    try:
        module, func_name = importlib.import_module(input("Module: ")), input("Function: ")
        print(f"Output: {getattr(module, func_name, lambda x: 'Function not found.')(float(input('Arg: ')))}")
    except Exception as e:
        print(f"Error: {e}")

def measure_import_time():
    for stmt in ["import math", "from math import *"]:
        start, end = time.time(), (exec(stmt), time.time())[1]
        print(f"{stmt} time: {end - start}")

def explore_sys_path():
    sys.path.append('/custom/path/to/modules')
    print("Successfully imported mymodule.") if 'mymodule' in sys.modules or __import__('mymodule') else print("Failed to import mymodule.")

def test_mock_import():
    with mock.patch('math.sqrt', return_value=100): print(math.sqrt(25))

def explore_sys_modules():
    import mymodule
    print(sys.modules['mymodule'])
    importlib.reload(mymodule)
    print("Module reloaded.")

if __name__ == "__main__":
    check_and_execute()
    measure_import_time()
    explore_sys_path()
    test_mock_import()
    explore_sys_modules()
```
