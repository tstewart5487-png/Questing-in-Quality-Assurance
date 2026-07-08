# Loops, Functions, and Assert

## `continue` vs `break`

- The `continue` keyword is used together with a nested `if` statement in order to skip an iteration.
- The `break` statement interrupts the execution of the loop entirely — in other words, exiting the loop.

## `reversed()`

During technical interviews, you may be asked questions about doing a reverse. The `reversed()` function is the easiest way to reverse an object. (Don't forget to convert it to a list when using this function.)

## `enumerate()`

The `enumerate()` function is especially helpful for automation testers when they need to iterate over a list of items and keep track of their indices. This function allows you to know the index of each item as you go through the list.

## Functions

When needed, we can create our own functions in Python, which comes in handy when dealing with automation testing. For example, imagine you need to run 10 tests for a web application and each test requires authentication — instead of writing the code for each test, we can simply use a function.

- `def` is a keyword that allows you to define a function.

**Basic structure of `def`:**

The code that the function should execute starts on the next line — this is the body of a function in Python. The body is written with a four-space indentation before it. That's how you indicate where the function begins and ends:

```python
def hello():
    print("Hello!")  # this is the body of the function
```

Functions execute the code within their scope from top to bottom. Once finished, the code continues to run from the point where it was initially called.

### Parameters and Arguments

Sometimes a function can have more than one parameter. In a function call, arguments are passed according to the order in which they are listed: the first argument is passed as the first parameter, the second argument as the second parameter, and so on.

### Return Values

A function can return a value using a `return` statement. Syntactically, we put the value to be returned after the `return` keyword, inside the function body. We can then use this value elsewhere in the code — this ability is very helpful.

## `assert`

In Python, `assert` is used to test if a condition is true or false. If false, an error is raised — which is very helpful for debugging purposes and ensuring that code is working correctly. Specifically, it raises an `AssertionError` and stops the program.

Automation testers use `assert` to verify that their code functions as expected and to validate test results. They can check if specific conditions are met in their code and promptly identify when something goes wrong.

## Common Built-in Functions Reference

Python ships with a set of built-in functions that are always available without needing an import. Below are the ones most relevant for everyday scripting and QA/testing work, summarized in plain terms.

| Function | What it does |
|---|---|
| `abs(x)` | Returns the absolute (positive) value of a number |
| `all(iterable)` | Returns `True` if every item in the iterable is truthy |
| `any(iterable)` | Returns `True` if at least one item in the iterable is truthy |
| `bool(x)` | Converts a value to `True` or `False` |
| `dict()` | Creates a new dictionary |
| `divmod(a, b)` | Returns a tuple of `(a // b, a % b)` — quotient and remainder together |
| `enumerate(iterable, start=0)` | Loops over an iterable while also tracking each item's index |
| `filter(function, iterable)` | Builds an iterator of only the items where `function` returns true |
| `float(x)` | Converts a value to a floating-point number |
| `format(value, spec)` | Formats a value as a string according to a format spec |
| `getattr(obj, name)` | Retrieves an attribute from an object by name (as a string) |
| `hasattr(obj, name)` | Returns `True`/`False` for whether an object has a given attribute |
| `hash(obj)` | Returns the hash value of an object (used internally for dict/set lookups) |
| `help()` | Opens Python's built-in interactive help system |
| `id(obj)` | Returns a unique integer identifying an object in memory |
| `input(prompt)` | Reads a line of text typed by the user |
| `int(x)` | Converts a value to an integer |
| `isinstance(obj, type)` | Checks whether an object is an instance of a given type |
| `issubclass(cls, type)` | Checks whether a class is a subclass of another |
| `iter(obj)` | Returns an iterator for an iterable object |
| `len(obj)` | Returns the number of items in a sequence or collection |
| `list(iterable)` | Creates a new list |
| `map(function, iterable)` | Applies a function to every item in an iterable, returning the results |
| `max(iterable)` | Returns the largest item in an iterable (or of several arguments) |
| `min(iterable)` | Returns the smallest item in an iterable (or of several arguments) |
| `next(iterator)` | Retrieves the next item from an iterator |
| `open(file, mode)` | Opens a file and returns a file object for reading/writing |
| `ord(char)` | Returns the Unicode code point of a single character |
| `chr(codepoint)` | The inverse of `ord()` — converts a code point back to its character |
| `pow(base, exp)` | Raises `base` to the power of `exp` (same as `base ** exp`) |
| `print(*objects)` | Prints values to the console |
| `range(start, stop, step)` | Generates a sequence of numbers, commonly used in loops |
| `repr(obj)` | Returns a printable, developer-facing string representation of an object |
| `reversed(seq)` | Returns a reverse iterator over a sequence |
| `round(number, ndigits)` | Rounds a number to the given number of decimal places |
| `set(iterable)` | Creates a new set (unordered collection of unique items) |
| `slice(start, stop, step)` | Creates a slice object representing a range of indices — the same thing used behind the scenes when you write `list[start:stop:step]` |
| `sorted(iterable)` | Returns a new sorted list from the items of an iterable |
| `str(obj)` | Converts a value to its string representation |
| `sum(iterable)` | Adds up all the items in an iterable |
| `tuple(iterable)` | Creates a new tuple |
| `type(obj)` | Returns the type/class of an object |
| `vars(obj)` | Returns an object's attributes as a dictionary |
| `zip(*iterables)` | Combines multiple iterables into tuples, pairing up items by position |

For the complete, authoritative list of all built-in functions, see the [official Python documentation](https://docs.python.org/3/library/functions.html).

### Additional / Advanced Built-in Functions

These are used less often day-to-day but are worth knowing about.

| Function | What it does |
|---|---|
| `aiter(x)` | Returns an async iterator for an async-iterable object (used with `async for`) |
| `anext(x)` | The async version of `next()` — gets the next item from an async iterator |
| `ascii(obj)` | Like `repr()`, but escapes any non-ASCII characters in the result |
| `bin(x)` | Converts an integer to a binary string (prefixed with `0b`) |
| `breakpoint()` | Drops you into the debugger at that point in the code |
| `bytearray(source)` | Creates a mutable sequence of bytes |
| `bytes(source)` | Creates an immutable sequence of bytes |
| `callable(obj)` | Returns `True` if the object can be called (like a function) |
| `classmethod` | A decorator that turns a method into one bound to the class rather than an instance |
| `compile(source, filename, mode)` | Compiles source code into a code object that can be run with `exec()` or `eval()` |
| `complex(real, imag)` | Creates a complex number |
| `delattr(obj, name)` | Deletes a named attribute from an object |
| `dir(obj)` | Lists the names/attributes available on an object (or the current scope if no argument is given) |
| `eval(source)` | Evaluates a single Python expression given as a string and returns the result |
| `exec(source)` | Executes a string (or compiled object) of Python statements |
| `frozenset(iterable)` | Creates an immutable version of a set |
| `globals()` | Returns a dictionary representing the current global namespace |
| `hex(x)` | Converts an integer to a hexadecimal string (prefixed with `0x`) |
| `locals()` | Returns a dictionary representing the current local namespace |
| `memoryview(obj)` | Creates a memory view object for accessing an object's internal data without copying it |
| `object()` | Creates a new, featureless base object — the parent class of every Python class |
| `oct(x)` | Converts an integer to an octal string (prefixed with `0o`) |
| `property()` | Creates a managed attribute (getter/setter/deleter) on a class |
| `setattr(obj, name, value)` | Sets a named attribute on an object to a given value |
| `staticmethod` | A decorator that turns a method into one that doesn't receive `self` or the class automatically |
| `super()` | Gives access to methods from a parent class, useful in class inheritance |
| `__import__(name)` | The low-level function behind Python's `import` statement (rarely used directly) |