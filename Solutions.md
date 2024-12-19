# Python Problem Solutions

## ❓ **Poblem 1: Function with Unlimited Arguments**  
**Problem:**  
You need to write a function that accepts **any number** of input arguments.  
💡 **Hint:** In Python, you can use `*args` to handle multiple arguments.

### Solution:

You can use `*args` to accept an arbitrary number of positional arguments. Here's an example:

```python
def sum_numbers(*args):
    return sum(args)

# Example usage
result = sum_numbers(1, 2, 3, 4, 5)
print(result)  # Output: 15
```

---
## ❓ **Poblem 2: Argument Validation Before Execution**  
**Problem:**  
You need a function that validates its input arguments before proceeding with the main logic.  
💡 **Hint:** Use a decorator or inline validation checks with `if` statements to ensure argument validity.

### Solution:

You can validate inputs using `if` statements or decorators. Here's an example using inline validation:

```python
def validate_input(num):
    if not isinstance(num, int):
        raise ValueError("Input must be an integer.")

def double_number(num):
    validate_input(num)
    return num * 2

# Example usage
try:
    result = double_number(5)
    print(result)  # Output: 10
except ValueError as e:
    print(e)
```

---
## ❓ **Poblem 3: Preserving Function Metadata After Wrapping**  
**Problem:**  
You’ve wrapped a function with another (like a decorator) and noticed that the original function's metadata (like its name and docstring) is lost.  
💡 **Hint:** Use `functools.wraps` to preserve the original function's metadata.

### Solution:

To preserve the original function's metadata when using a decorator, you can use `functools.wraps`. Here's an example:

```python
import functools

def decorator(func):
    @functools.wraps(func)
    def wrapper(*args, **kwargs):
        return func(*args, **kwargs)
    return wrapper

@decorator
def say_hello(name):
    """Greets the user by name."""
    return f"Hello, {name}!"

print(say_hello.__name__)  # Output: say_hello
print(say_hello.__doc__)   # Output: Greets the user by name.
```

---
## ❓ **Poblem 4: Passing Variable Arguments to Another Function**  
**Problem:**  
You want to define a wrapper function that accepts variable arguments and passes them unchanged to another function.  
💡 **Hint:** Use `*args` and `**kwargs` in the wrapper to handle arbitrary arguments and keyword arguments.

### Solution:

You can pass variable arguments to another function using `*args` and `**kwargs`. Here's an example:

```python
def wrapper_function(*args, **kwargs):
    return target_function(*args, **kwargs)

def target_function(a, b, c):
    return a + b + c

# Example usage
result = wrapper_function(1, 2, 3)
print(result)  # Output: 6
```

---
## ❓ **Poblem 5: Timing a Function's Execution**  
**Problem:**  
You want to measure the execution time of a function to see how long it takes to run.  
💡 **Hint:** Use the `time` module to capture start and end times, or a decorator for reusable timing logic.

### Solution:

You can use the `time` module to measure the execution time of a function:

```python
import time

def measure_time(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print(f"Execution Time: {end_time - start_time} seconds")
        return result
    return wrapper

@measure_time
def slow_function():
    time.sleep(2)

# Example usage
slow_function()
'''

---

## 📝 **Conclusion:**
These are common Python problems that help you master function handling, validation, metadata preservation, argument passing, and execution time measurement. By applying these concepts, you can enhance your coding efficiency and write cleaner, more reusable functions.
