- [Basic Concepts](#basic-concepts)
  - [Python Introduction](#python-introduction)
  - [Character Encoding](#character-encoding)
  - [Number Systems](#number-systems)
  - [Variable Naming Conventions](#variable-naming-conventions)
  - [Variable Declarations](#variable-declarations)
  - [String Manipulation](#string-manipulation)
  - [Printing for debugging](#printing-for-debugging)
  - [Modules \& Imports/Exports](#modules--importsexports)
- [Data Types](#data-types)
  - [Primitive Data \& Non Primitive Data](#primitive-data--non-primitive-data)
    - [The Real Meaning of “Primitive” vs “Non-Primitive”](#the-real-meaning-of-primitive-vs-non-primitive)
  - [Type Checking System](#type-checking-system)
  - [Type Conversion](#type-conversion)
  - [`Math` Operation Module](#math-operation-module)
- [Operator](#operator)
  - [Arithmetic Operators](#arithmetic-operators)
  - [Assignment Operators](#assignment-operators)
  - [Comparison Operators](#comparison-operators)
  - [Logical Operators](#logical-operators)
  - [Other Important Operators](#other-important-operators)
  - [Membership / Identity](#membership--identity)
    - [Membership Operators: `in`, `not in`](#membership-operators-in-not-in)
    - [Identity Operators `is`, `is not`](#identity-operators-is-is-not)
- [Collections \& Objects (Dictionary)](#collections--objects-dictionary)
  - [Braces Literal Syntax](#braces-literal-syntax)
  - [Dictionary (Object) Manipulation Structure Levels](#dictionary-object-manipulation-structure-levels)
    - [Natural Hierarchical Structure Levels in Different Variable Declarations {Classification}](#natural-hierarchical-structure-levels-in-different-variable-declarations-classification)
  - [String Methods](#string-methods)
  - [List Methods: append(), extend(), insert(), pop(), remove(), sort()](#list-methods-append-extend-insert-pop-remove-sort)
  - [Tuple Operations: indexing, slicing, unpacking](#tuple-operations-indexing-slicing-unpacking)
  - [Dict Methods: .keys(), .values(), .items(), .get(), .update()](#dict-methods-keys-values-items-get-update)
  - [Set Methods: .add(), .remove(), .union(), .intersection()](#set-methods-add-remove-union-intersection)
  - [Object Orientation: class, **init**, self](#object-orientation-class-init-self)
  - [Data Model Hooks: **str**, **repr**, **len**, **iter**](#data-model-hooks-str-repr-len-iter)
- [Control Flow](#control-flow)
  - [Conditionals: if/elif/else](#conditionals-ifelifelse)
  - [Loops: for, while, break, continue](#loops-for-while-break-continue)
  - [Loop Tools: enumerate(), zip(), range()](#loop-tools-enumerate-zip-range)
  - [Exception Handling: try/except/finally/else, raise](#exception-handling-tryexceptfinallyelse-raise)
- [Functions \& Scope](#functions--scope)
  - [Closures](#closures)
  - [Decorators: @decorator syntax](#decorators-decorator-syntax)
  - [Scopes: LEGB rule (Local, Enclosing, Global, Built-in)](#scopes-legb-rule-local-enclosing-global-built-in)
  - [Generators: yield, yield from](#generators-yield-yield-from)
- [Asynchronous Python](#asynchronous-python)
  - [Coroutines: async def, await](#coroutines-async-def-await)
  - [Event Loop: asyncio.run()](#event-loop-asynciorun)
  - [Tasks / Futures: asyncio.create_task, Future](#tasks--futures-asynciocreate_task-future)
  - [Async Iteration: async for, async with](#async-iteration-async-for-async-with)
- [Modules \& Imports](#modules--imports)
  - [Import Variants: import, from ... import ..., import as](#import-variants-import-from--import--import-as)
  - [Packages: **init**.py, namespace packages](#packages-initpy-namespace-packages)
  - [Built-in Modules: math, os, sys, json](#built-in-modules-math-os-sys-json)
  - [Virtual Environments: venv, pip](#virtual-environments-venv-pip)
- [Advanced Constructs](#advanced-constructs)
  - [Comprehensions: \[x\*x for x in range(5)\]](#comprehensions-xx-for-x-in-range5)
  - [Context Managers: with, custom **enter** / **exit**](#context-managers-with-custom-enter--exit)
  - [Iterators \& Iterables: iter(), next()](#iterators--iterables-iter-next)
  - [Metaclasses: class X(metaclass=...)](#metaclasses-class-xmetaclass)
  - [Typing: from typing import List, Dict, Optional](#typing-from-typing-import-list-dict-optional)
- [Error \& Debugging](#error--debugging)
  - [Exceptions: built-in (ValueError, TypeError)](#exceptions-built-in-valueerror-typeerror)
  - [Assertion: assert condition](#assertion-assert-condition)
  - [Logging: import logging](#logging-import-logging)
  - [Debugging: pdb, breakpoint()](#debugging-pdb-breakpoint)
- [Common Gotchas \& Semantics](#common-gotchas--semantics)
  - [Mutability (list vs tuple)](#mutability-list-vs-tuple)
  - [Default argument traps (def f(x=\[\]))](#default-argument-traps-def-fx)
  - [is vs ==](#is-vs-)
  - [Integer caching and interning](#integer-caching-and-interning)
  - [Late binding in closures](#late-binding-in-closures)

# Basic Concepts

## Python Introduction

Variables: Store information.

```py
message = "Hello!"
```

Functions: Block of code that runs when called.

```py
def greet():
    print("Hi!")
```

Collections: Group multiple values together.

```py
numbers = [1, 2, 3]        # list
person = {"name": "Alice"} # dictionary
```

Control Flow: Run code conditionally or repeatedly.

```py
if message == "Hello!":
    print("Greeting detected")

for num in numbers:
    print(num)
```

Print Function

```py
print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)
```

- objects: The data you want to print. The \* sign means that you can print multiple things to the terminal by passing in multiple objects (in other words, strings, variables, numbers, and so on) separated by commas.
- sep=' ': The separator between the objects. This defaults to a single space character (' ').
- end='\n': What to print at the end of the object. This defaults to a new line character ('\n').
- file=sys.stdout: Determines where to send the output. The default is the terminal, but it can be a file.
- flush=False: Determines whether to show the output data right away. The default is False, which means Python may wait before displaying the output.

```py
print('Footballers:', 'Ronaldo', 'Messi', 'Hazard', 'Kante', 'Okocha', sep=', ')
# Output: Footballers:, Ronaldo, Messi, Hazard, Kante, Okocha

print('Footballers:', end=' ')
print('Ronaldo', end=', ')
print('Messi', end=', ')
print('Hazard', end=', ')
print('Kante', end=', ')
print('Okocha', end='.')
#Output: Footballers: Ronaldo, Messi, Hazard, Kante, Okocha.
```

Here's how you can use the file argument to write the output of the print function to a separate file:

```py
with open('output.txt', 'w') as f:
  print('Hello world!', file=f)
```

This will print the text Hello world! into a file named output.txt. If the file doesn't exist, it will be automatically created. You will learn more about how working with the filesystem in future lectures.

The last argument is flush. When this is set to True, whatever you're outputting is shown immediately rather than waiting for potential delays in the program's execution:

```py
import time

print('Processing...', end=' ', flush=True)
time.sleep(2)
print('Done!')
```

In this case, the Processing… text immediately appears in the terminal, then time.sleep(2) delays the Done text from appearing for 2 seconds. This makes flush a great tool for displaying progress bars and loading text.

## Character Encoding

Two main types:

- **ASCII** (American Standard Code for Information Interchange)

https://www.ascii-code.com/

- **Unicode** (Universal Character Set)

https://symbl.cc/en/unicode-table/#cjk-unified-ideographs-extension-b

A character encoding standard used in computers to represent text.
It assigns a numeric value to each character, which is universally recognized by machines.
ASCII standard covers 128 characters including:
~ Uppercase and lowercase English letters (A-Z, a-z).
~ Numbers (0-9).
~ Common punctuation marks and symbols (!, @, #, and so on).
~ Control characters (such as newline and tab).`

```py
// Converting between characters and ASCII values
let symbol = "!";
console.log(symbol.charCodeAt(0)); // Output: 33

let char = String.fromCharCode(65);
console.log(char); // Output: A
```

## Number Systems

- **Binary**: Base-2 (0,1) with 8 digits
- **Hexadecimal**: Base-16 (0-9, A-F) with 2 digits
- **Decimal**: Base-10 (0-9) with values 0-127
- **Octal**: Base-8 (0-7) with 3 digits

Example below:

```
A in ASCII value is 65 Decimal Value / 41 Hexadecimal Value / 101 Octal Value and lastly is
01000001 Binary Value that can be convert to Decimal Value
    0   1   0   0  0   0   0   1 = A in Binary value
128	64	32	16	8	4	2	1 = each binary position formula
    0  64   0   0  0   0   0   1 = Total value is 65 Decimal Value

*Note: other types can also be convert vice versa
```

## Variable Naming Conventions

When naming variables in Python, there are some important rules you should keep in mind:

- Variable names can only start with a letter or an underscore (\_), not a number.
- Variable names can only contain alphanumeric characters (a-z, A-Z, 0-9) and underscores (\_).
- Variable names are case-sensitive — age, Age, and AGE are all considered unique.
- Variable names cannot be one of Python's reserved keywords such as if, class, or def.

If you break any of those rules, your Python program will throw a SyntaxError:

```py
    5variable_name = 5
     ^
SyntaxError: invalid syntax
```

Now let's go over some common naming conventions for variables in Python.

First, variables names should be in lowercase, with separate words separated by an underscore. This is called snake case:

```py
my_variable_name = 'freeCodeCamp'
```

Next, you should use descriptive names for variables. For example, if you want to save a user's age as a variable, user_age is better than age or an abbreviation like ua:

```py
user_age = 30
```

This way, you can easily communicate the purpose of a variable to other team members (or to your future self) in a large codebase.

Another convention is to avoid using single-letter variable names. This is very common in Python, but should be avoided because variable names with a single letter communicate no purpose or meaning:

```py
x = 56 # What do you mean by x?
```

This is different if you are in a loop or something similar, as variable names like i, j, k, and so on are common and acceptable.

In Python, comments start with a pound symbol (#), and the language ignores everything after the # symbol on that line:

```py
# This is a single-line comment
Multi-line comments can be created by using consecutive single-line comments:

# This is a
# multi-line
# comment
```

Remember the goal is to make your code as self explanatory as possible. A good rule of thumb is that if you need to add a comment to explain what a variable or function does, you might want to consider renaming it to something more descriptive.

## Variable Declarations

In Python, variables are created simply by assigning a value — there are no explicit declaration keywords like let, const, or var.

All variables in Python are dynamically typed, meaning their type is determined at runtime based on the value assigned. You can reassign variables freely, and Python automatically handles the underlying data type.

Other key declaration and definition constructs include:

- **def** – For defining functions.
- **class** – For defining classes (object-oriented structures).
- **del** – For deleting variable names or object attributes.
- **import** – For bringing in modules or specific functions.
- **global** / nonlocal – For declaring scope-related variables inside functions.

Python emphasizes readability and explicitness, so variables exist as references to objects, not fixed memory bindings.

## String Manipulation

A string is a sequence of characters surrounded by either single or double quotation marks. In some programming languages, characters surrounded by single quotes are treated differently than characters surrounded by double quotes, but in Python, they're treated equally. So, you can use either when working with strings. Here are some examples of strings:

```py
my_str_1 = 'Hello'
my_str_2 = "World"
```

If you need a multi-line string, you can use triple double quotes or single quotes:

```py
my_str_3 = """Multiline
string"""
my_str_4 = '''Another
multiline
string'''
```

If your string contains either single or double quotation marks, then you have two options:

- Use the opposite kind of quotes. That is, if your string contains single quotes, use double quotes to wrap the string, and vice versa:

  ```py
  msg = "It's a sunny day"
  quote = 'She said, "Hello World!"'
  ```

- Escape the single or double quotation mark in the string with a backslash (\). With this method, you can use either single or double quotation marks to wrap the string itself:

  ```py
  msg = 'It\'s a sunny day'
  quote = "She said, \"Hello!\""
  ```

You can also combine multiple strings together with the plus (+) operator. This process is called string concatenation. Here's how to concatenate two strings with the plus operator:

```py
my_str_1 = 'Hello'
my_str_2 = "World"

str_plus_str = my_str_1 + ' ' + my_str_2
print(str_plus_str) # Hello World
```

But note that this only works with strings. If you try to concatenate a string with a number, you'll get a TypeError:

```py
name = 'John Doe'
age = 26

name_and_age = name + age
print(name_and_age) # TypeError: can only concatenate str (not "int") to str
```

This happens because Python does not automatically convert other data types like integers into strings when you concatenate them. Python requires all elements to be strings before it can concatenate them. To fix that, you can convert the number into a string with the built-in str() function:

```py
name = 'John Doe'
age = 26

name_and_age = name + str(age)
print(name_and_age) # John Doe26
```

You can also use the augmented assignment operator for concatenation. This is represented by a plus and equals sign (+=), and performs both concatenation and assignment in one step. Here's it in action:

```py
name = 'John Doe'
age = 26

name_and_age = name  # Start with the name
name_and_age += str(age)  # Append the age as string

print(name_and_age)  # John Doe26
```

Apart from regular strings, Python also has a category of string called f-strings, which is short for formatted string literals. It allows you to handle interpolation and also do some concatenation with a compact and readable syntax.

F-strings start with f (either lowercase or uppercase) before the quotes, and allow you to embed variables or expressions inside replacement fields indicated by curly braces ({}). Here's an example:

```py
name = 'John Doe'
age = 26
name_and_age = f'My name is {name} and I am {age} years old'
print(name_and_age) # My name is John Doe and I am 26 years old

num1 = 5
num2 = 10
print(f'The sum of {num1} and {num2} is {num1 + num2}') # The sum of 5 and 10 is 15
```

Now that you've learned about string concatenation and f-strings, let's look at how you can get the length of a string and work with the individual characters in a string, a process called indexing. To get the length of a string, you can use the built-in len() function. Here's an example:

```py
my_str = 'Hello world'
print(len(my_str))  # 11
```

Now onto indexing. Each character in a string has a position called an index. The index is zero-based, meaning that the index of the first character of a string is 0, the index of the second character is 1, and so on. To access a character by its index, you use square brackets ([]) with the index of the character you want to access inside. Here are some examples:

```py
my_str = "Hello world"

print(my_str[0])  # H
print(my_str[6])  # w
```

Negative indexing is also allowed, so you can get the last character of any string with -1, the second-to-last character with -2, and so on:

```py
my_str = 'Hello world'
print(my_str[-1])  # d
print(my_str[-2]) # l
```

Now that you're familiar with indexing, let's take things a bit further with string slicing. String slicing lets you extract a portion of a string or work with only a specific part of it. Here's the basic syntax:

```py
string[start:stop]
```

If you want to extract characters from a certain index to another, you just separate the start and stop indices with a colon:

```py
my_str = 'Hello world'
print(my_str[1:4]) # ell
```

Note that the stop index is non-inclusive, so [1:4] just extracted the characters from index 1, and up to, but not including, the character at index 4.

You can also omit the start and stop indices, and Python will default to 0 or the end of the string, respectively. For example, here's what happens if you omit the start index:

```py
my_str = 'Hello world'
print(my_str[:7])  # Hello w
```

This extracts everything from index 0 up to (but not including), the character at index 7. And here's what happens if you omit the stop index:

```py
my_str = 'Hello world'
print(my_str[8:])  # rld
```

This extracts everything from the character at index 8 until the end of the string.

You can also omit both the start and stop indices, which will extract the whole string:

```py
my_str = 'Hello world'
print(my_str[:])  # Hello world
```

Apart from the start and stop indices, there's also an optional step parameter, which is used to specify the increment between each index in the slice.

Here's the syntax for that:

```py
string[start:stop:step]
```

In the example below, the slicing starts at index 0, stops before 11, and extracts every second character:

```py
my_str = 'Hello world'
print(my_str[0:11:2])  # Hlowrd
```

A helpful trick you can do with the step parameter is to reverse a string by setting step to -1, and leaving start and stop blank:

```py
my_str = 'Hello world'
print(my_str[::-1]) # dlrow olleH
```

It can also be helpful to check if a character or set of characters exist in a string before slicing it. To do that, Python provides the in operator, which returns a boolean that specifies whether the character or characters exist in the string or not.

Here are some examples:

```py
my_str = 'Hello world'

print('Hello' in my_str)  # True
print('hey' in my_str)    # False
print('hi' in my_str)    # False
print('e' in my_str)  # True
print('f' in my_str)  # False
```

## Printing for debugging

In Python, debugging and printing messages to the console are done using the built-in `print()` function.

Unlike JavaScript’s `console.log()`, `console.warn()`, and `console.error()`, Python handles output through the `print()` function and, for structured logging, the logging module.

Basic Console Output:

```py
print("This is a normal log message.")
print("This is a warning message!")  # (Normally use logging for actual warnings)
print("This is an error message!")   # (Normally use logging for actual errors)
```

Using the `logging` module (recommended for real applications):

```py
import logging

logging.basicConfig(level=logging.INFO)
logging.info("This is a log message.")
logging.warning("This is a warning message.")
logging.error("This is an error message.")
```

Result in console:

```vbnet
INFO:root:This is a log message.
WARNING:root:This is a warning message.
ERROR:root:This is an error message.
```

Python’s logging system supports configurable log levels (DEBUG, INFO, WARNING, ERROR, CRITICAL), file logging, and formatting — making it more flexible than simple print() statements.

## Modules & Imports/Exports

Python organizes reusable code into modules (individual .py files) and packages (directories containing multiple modules).

You can import functions, classes, or variables from other files, or export your own simply by defining them.

Modules allow for clean program structure, reuse, and namespace isolation.

**Importing and Exporting**

- Basic import

  ```py
  import math
  print(math.sqrt(25))
  ```

  Import specific names

  ```py
  from math import sqrt, pi
  print(sqrt(25), pi)
  ```

  Alias imports

  ```py
  import math as m
  print(m.pi)
  ```

  Wildcard import (not recommended)

  ```py
  from math import *
  print(sin(pi / 2))
  ```

  Custom module imports

  ```py
  # utils.py
  def greet(name):
      return f"Hello, {name}!"

  # main.py
  from utils import greet
  print(greet("Alice"))
  ```

**Re-exports and Package Initialization**

You can control what gets exported from a package by defining `__all__` in `__init__`.py:

```py
# mypackage/__init__.py
from .mathlib import add, subtract
__all__ = ["add", "subtract"]
```

**Dynamic Imports**

Python allows runtime (dynamic) imports using importlib — similar to JavaScript’s import():

```py
import importlib

math_module = importlib.import_module("math")
print(math_module.sqrt(16))
```

This approach is useful for conditional imports or plugin systems.

**Top-Level Await Equivalent**

Python doesn’t have “top-level await” like JavaScript, but asynchronous execution is supported through `asyncio`:

```py
import asyncio

async def fetch_data():
    await asyncio.sleep(1)
    return "Data loaded!"

async def main():
    result = await fetch_data()
    print(result)

asyncio.run(main())
```

Visualization (Module Relationship):

```scss
[ main.py ] --imports--> [ utils.py ]
             \--dynamic--> [ plugin.py ] (only if needed)
```

# Data Types

Python is a dynamically-typed language like JavaScript, meaning you don't need to explicitly declare types for variables. The language knows what data type a variable is based on what you assign to it.

Here are some examples:

```py
name = 'John Doe' # Python knows this is a string
age = 25 # Python knows this is an integer
```

This is in contrast to some statically-typed languages like C#, Java, and C++, where you have to declare types with variables, like this:

```py
string name = 'John Doe'
int age = 25
```

The dynamic-typing nature of Python makes coding really fast and more flexible, but it can lead to unexpected bugs because type errors are detected only when a program runs, not when the program compiles.

Here are the most common data types you'll use in Python:

```py
my_string_var = 'hello'
print('String:', my_string_var) # String: hello
```

Integer: A whole number without decimals, for example, 10 or -5.

```py
my_integer_var = 10
print('Integer:', my_integer_var) # Integer: 10
```

Float: A number with a decimal point, like 4.41 or -0.4.

```py
my_float_var = 4.50
print('Float:', my_float_var) # Float 4.50
```

Complex: A number with a real and imaginary part, like 6 + 7j.

```py
my_complex_var = 3 + 4j
print('Complex:', my_complex_var) # Complex: (3+4j)
```

Boolean: A true or false type, written as True or False.

```py
my_boolean_var = True
print('Boolean:', my_boolean_var) # Boolean: True
```

Set: An unordered collection of unique elements, like {4, 2, 0}.

```py
my_set_var = {7, 5, 8}
print('Set:', my_set_var) # Set: {7, 5, 8}
```

Dictionary: A collection of key-value pairs enclosed in curly braces, like {'name': 'John Doe', 'age': 28}.

```py
my_dictionary_var = {'name': 'Alice', 'age': 25}
print('Dictionary:', my_dictionary_var) # Dictionary: {'name': 'Alice', 'age': 25}
```

Tuple: An immutable ordered collection, enclosed in brackets, like (7, 8, 4).

```py
my_tuple_var = (7, 5, 8)
print('Tuple:', my_tuple_var) # Tuple: (7, 5, 8)
```

Range: A sequence of numbers, often used in loops, for example, range(5).

```py
my_range_var = range(5)
print(my_range_var) # range(0, 5)
```

List: An ordered collection of elements that supports different data types.

```py
my_list = [22, 'Hello world', 3.14, True]
print(my_list) # [22, 'Hello world', 3.14, True]
```

NoneType: A special value that represents the absence of a value.

```py
my_none_var = None
print('None:', my_none_var) # None: None
```

| Category                    | Examples                                           | Description                              |
| --------------------------- | -------------------------------------------------- | ---------------------------------------- |
| **Primitive (Built-ins)**   | `int`, `float`, `bool`, `str`, `bytes`, `NoneType` | Basic immutable value types.             |
| **Composite / Collections** | `list`, `tuple`, `dict`, `set`, `frozenset`        | Group or structure multiple values.      |
| **Special**                 | `complex`, `range`, `memoryview`                   | Less common, but part of core built-ins. |

Many other programming languages group data types broadly as either primitive or reference types. Primitive types are simple and immutable, meaning they can't be changed once declared. Reference types can hold multiple values, and are either mutable or immutable. But Python doesn't draw a hard line between those two groups. Instead, all data gets treated as objects, and some objects are immutable while others are mutable.

Immutable data types can't be modified or altered once they're declared. You can point their variables at something new, which is called reassignment, but you can't change the original object itself by adding, removing, or replacing any of its elements. Examples of immutable data types in Python are string, integer, float, boolean, tuple, and range.

Here's an example showing that, while you can reassign a different string to a variable, direct modification of a string isn't allowed because strings are immutable:

```py
greeting = 'hi'
greeting = 'hello'
print(greeting) # hello

greeting[0] = 'H' # TypeError: 'str' object does not support item assignment
```

On the other hand, you can change mutable types without giving them a new name. You can add, remove, or update items right where they live. Examples are a list and a dictionary.

Here's an example of updating an element in a list:

```py
nums = [1, 2, 3]
nums[0] = 4

print(nums) # [4, 2, 3]
```

## Primitive Data & Non Primitive Data

Python technically treats everything as an object, even integers and strings.
But for learning and classification (mirroring your ECMAScript doc), we can still divide them conceptually into two categories:

- Primitive (Immutable) Data Types

  They behave like JavaScript’s primitives:
  their values cannot be changed once created — only replaced.

  | Type       | Example              | Description                             |
  | ---------- | -------------------- | --------------------------------------- |
  | `int`      | `42`, `-10`, `0`     | Whole numbers (arbitrary precision).    |
  | `float`    | `3.14`, `-2.5`       | Decimal numbers.                        |
  | `bool`     | `True`, `False`      | Boolean logic.                          |
  | `str`      | `"Hello"`, `'World'` | Text, immutable sequence of characters. |
  | `NoneType` | `None`               | Represents “no value” (like JS `null`). |
  | `complex`  | `3+4j`               | Complex numbers (real + imaginary).     |

  All of these are immutable — if you “change” one, Python actually makes a new object behind the scenes.

- Non-Primitive (Mutable / Composite) Data Types

  These can hold multiple values, or can be modified after creation.

  | Type                  | Example                        | Description                        |
  | --------------------- | ------------------------------ | ---------------------------------- |
  | `list`                | `[1, 2, 3]`                    | Ordered, mutable collection.       |
  | `tuple`               | `(1, 2, 3)`                    | Ordered, immutable collection.     |
  | `dict`                | `{"name": "Alice", "age": 25}` | Key-value pairs (like JS objects). |
  | `set`                 | `{1, 2, 3}`                    | Unordered unique values.           |
  | `frozenset`           | `frozenset({1, 2, 3})`         | Immutable version of `set`.        |
  | `bytes` / `bytearray` | `b"abc"` / `bytearray(b"abc")` | Raw binary data.                   |

### The Real Meaning of “Primitive” vs “Non-Primitive”

Think of a primitive value as a direct box of data, like a sticky note with the number “10” written on it.
A non-primitive value is a box that points to another box, like a label that says “look over there” — it doesn’t hold the data itself, just a reference to where it lives in memory.

- Example 1 — Numbers (Primitive in both JS and Python)

  JavaScript

  ```py
  let x = 10;
  let y = x;
  y = 20;
  console.log(x); // 10
  console.log(y); // 20
  ```

  Python

  ```py
  x = 10
  y = x
  y = 20
  print(x)  # 10
  print(y)  # 20
  ```

  Why both behave the same:

  - Both numbers are primitive.
  - When you assign y = x, you copy the value, not a pointer.
  - Changing y does not affect x, because they’re separate values in memory.

  This is the same in Java, C#, C, etc.

- Example 2 — Lists / Arrays (Non-Primitive)

  JavaScript

  ```py
  let a = [1, 2, 3];
  let b = a;
  b.push(4);

  console.log(a); // [1, 2, 3, 4]
  console.log(b); // [1, 2, 3, 4]
  ```

  Python

  ```py
  a = [1, 2, 3]
  b = a
  b.append(4)

  print(a)  # [1, 2, 3, 4]
  print(b)  # [1, 2, 3, 4]
  ```

  Why both behave the same again—but differently from primitives:

  - Arrays (JS) and lists (Python) are non-primitive — stored by reference.
  - b = a doesn’t make a new copy; it makes a new label pointing to the same list in memory.
  - When you modify b, you’re really modifying the shared data both labels point to.

  If you want a separate copy, you must do it explicitly:

  - JS: let b = a.slice();
  - Python: b = a.copy() or b = a[:]

- Example 3 — Strings: a tricky “in-between” case

  JavaScript

  ```py
  let s1 = "hello";
  let s2 = s1;
  s2 = "world";

  console.log(s1); // "hello"
  console.log(s2); // "world"
  ```

  Python

  ```py
  s1 = "hello"
  s2 = s1
  s2 = "world"

  print(s1)  # "hello"
  print(s2)  # "world"
  ```

  Explanation:

  - Strings look like objects, but they’re immutable primitives.
  - When you assign or “change” them, you’re not editing the same string — you’re creating a new one.
  - So even though "hello" is an object in Python, it behaves like a primitive.

## Type Checking System

- To get the data type of a variable, you can use the type() function:

  ```py
  my_var_1 = 'Hello world'
  my_var_2 = 21

  print(type(my_var_1)) # <class 'str'>
  print(type (my_var_2)) # <class 'int'>
  ```

  And here's are all the data types covered in this lesson, along with their types in the terminal:

  ```py
  my_integer_var = 10
  print('Integer:', my_integer_var, '| Type:', type(my_integer_var))  # Integer: 10 | Type: <class 'int'>

  my_float_var = 4.50
  print('Float:', my_float_var, '| Type:', type(my_float_var))  # Float: 4.50 | Type: <class 'float'>

  my_complex_var = 3 + 4j
  print('Complex:', my_complex_var, '| Type:', type(my_complex_var))  # Complex: (3+4j) | Type: <class 'complex'>

  my_string_var = 'hello'
  print('String:', my_string_var, '| Type:', type(my_string_var))  # String: hello | Type: <class 'str'>

  my_boolean_var = True
  print('Boolean:', my_boolean_var, '| Type:', type(my_boolean_var))  # Boolean: True | Type: <class 'bool'>

  my_set_var = {7, 5, 8}
  print('Set:', my_set_var, '| Type:', type(my_set_var))  # Set: {7, 5, 8} | Type: <class 'set'>

  my_dictionary_var = {'name': 'Alice', 'age': 25}
  print('Dictionary:', my_dictionary_var, '| Type:', type(my_dictionary_var))  # Dictionary: {'name': 'Alice', 'age': 25} | Type: <class 'dict'>

  my_tuple_var = (7, 5, 8)
  print('Tuple:', my_tuple_var, '| Type:', type(my_tuple_var))  # Tuple: (7, 5, 8) | Type: <class 'tuple'>

  my_range_var = range(5)
  print('Range:', list(my_range_var), '| Type:', type(my_range_var))  # Range: [0, 1, 2, 3, 4] | Type: <class 'range'>

  my_list = [22, 'Hello world', 3.14, True]
  print('List:', list(my_list), '| Type:', type(my_list)) # List: [22, 'Hello world', 3.14, True] | Type: <class 'list'>

  my_none_var = None
  print('None:', my_none_var, '| Type:', type(my_none_var))  # None: None | Type: <class 'NoneType'>
  ```

- isinstance() takes in an object and the type you want to check it against, then returns a boolean. Here are some examples:

  ```py
  isinstance('Hello world', str) # True
  isinstance(True, bool) # True
  isinstance(42, int) # True
  isinstance('John Doe', int) # False
  ```

  Although Python is dynamically typed, you can still add type hints. These are optional signals that tell other developers what the data type of a variable or function is expected to be. Here's a quick example for variable types:

  ```py
  user_name: str = 'John Doe'
  user_age: int = 24
  ```

  Here's another example showing hints for function parameters and a return type:

  ```py
  def greet(name: str, age: int) -> str:
      return f'Hello, {name}, age {age}.'
  ```

  And here's a combination of the two:

  ```py
  def greet(name: str, age: int) -> str:
      return f'Hello, {name}, age {age}.'

  user_name: str = 'John Doe'
  user_age: int = 24

  print(greet(user_name, user_age)) # Hello, John Doe, age 24.
  ```

- id(obj) returns an integer that uniquely identifies an object during its lifetime.

  Think of it as a temporary name tag Python gives each object in memory.
  When you run:

  ```py
  x = 42
  print(id(x))
  ```

  you’ll get something like:

  ```py
  140737348041232
  ```

  That number is not random — it’s usually the memory address where the object lives (on CPython, the default Python implementation).

  So:

  - Each new object gets its own unique id.
  - When an object is destroyed (garbage-collected), that id can be reused later for something else.

  🧩 Example: Different Objects, Different IDs

  ```py
  a = 10
  b = 10
  print(id(a), id(b))
  ```

  You might expect different numbers, but both are usually the same.
  That’s because Python caches small integers (usually from -5 to 256) for efficiency.
  So a and b are actually pointing to the same preallocated object.

  Try with larger numbers:

  ```py
  x = 1000
  y = 1000
  print(id(x), id(y))
  ```

  You’ll probably see different ids — because those integers are not cached.

  🧩 Example: Lists and Mutability

  ```py
  a = [1, 2, 3]
  b = a
  print(id(a), id(b))  # same

  b.append(4)
  print(a)  # [1, 2, 3, 4]
  print(id(a), id(b))  # still same
  ```

  Both a and b point to the same object in memory.
  That’s why the list contents change for both.

  Now if you reassign:

  ```py
  b = [1, 2, 3, 4]
  print(id(a), id(b))  # different now
  ```

  You’ve created a new list; b no longer points to the same object.

  🧩 Example: Immutables Create New IDs

  ```py
  x = "hello"
  print(id(x))  # e.g. 140337

  x += " world"
  print(id(x))  # different id!
  ```

  Strings are immutable, so modifying them doesn’t alter the original object — it creates a new one.

  🔍 Why id() Matters

  - It’s a quick way to check whether two names refer to the same object.
  - It helps explain mutability and reference behavior.
  - It can reveal optimizations (like integer or string interning).

  This is why id() pairs nicely with the is operator:

  ```py
  a = [1, 2]
  b = a
  print(a is b)  # True
  print(id(a) == id(b))  # True

  b = [1, 2]
  print(a is b)  # False, same content but different object
  ```

  is is essentially just id(a) == id(b) under the hood — but written more clearly.

## Type Conversion

Converting between data types is a fundamental operation in Python, just like in JavaScript.
However, Python’s conversions are explicit and type-safe — there’s no automatic coercion like in JavaScript.

- `float()` — String to floating-point number

  Converts a string or integer into a floating-point (decimal) number.

  ```py
  print(float("3.14"))     # 3.14
  print(float("  3.14"))   # 3.14
  print(float("+3.14"))    # 3.14
  print(float(5))          # 5.0
  ```

  If conversion fails, Python raises an error instead of returning NaN:

  ```py
  print(float("3.14abc"))  # ValueError: could not convert string to float
  ```

  Equivalent to parseFloat() in JavaScript, but Python never partially parses a number from a longer string.

- `int()` — String or float to integer

  Converts a string (containing a whole number) or a float to an integer.

  ```py
  print(int("42"))      # 42
  print(int(3.14))      # 3
  print(int("   7"))    # 7
  print(int("+12"))     # 12
  ```

  Fails if the string isn’t a valid integer:

  ```py
  print(int("42px"))  # ValueError
  ```

  ✅ Difference from JS:
  Python does not ignore trailing non-numeric characters, while JavaScript’s parseInt("42px") returns 42.

- `str()` — Converts values to strings

  Python’s str() works like toString() in JavaScript, converting any value to a string.

  ```py
  num = 10
  print(str(num))   # "10"
  print(str(True))  # "True"
  print(str(None))  # "None"
  print(str([1, 2, 3]))  # "[1, 2, 3]"
  print(str({"name": "John"}))  # "{'name': 'John'}"
  ```

  Equivalent to:

  ```js
  num.toString(); // "10"
  ```

- `bool()` — Converts values to boolean

  Useful for determining the truthiness of a value.

  ```py
  print(bool(1))        # True
  print(bool(0))        # False
  print(bool("Hello"))  # True
  print(bool(""))       # False
  print(bool([]))       # False
  print(bool(None))     # False
  ```

  Similar to JavaScript’s truthy/falsy concept, but no coercion happens automatically in operations.

- `complex()` — Creates a complex number

  Python supports complex numbers natively (unlike JavaScript).

  ```py
  z = complex(2, 3)
  print(z)        # (2+3j)
  print(z.real)   # 2.0
  print(z.imag)   # 3.0
  ```

- `round()` — Format or round decimals

  Rounds a float to a specific number of decimal places. Similar to `.toFixed()` in JavaScript, but returns a number instead of a string.

  ```py
  num = 3.14159
  print(round(num))    # 3
  print(round(num, 2)) # 3.14
  print(round(5.678, 1)) # 5.7
  ```

  For precise financial calculations, use decimal.Decimal instead.

- `format()` — Number formatting with decimals

  Equivalent to JavaScript’s .toFixed(), but far more powerful.

  ```py
  num = 3.14159
  print(format(num, ".2f"))  # "3.14"
  print(format(num, ".3f"))  # "3.142"

  price = 19.99
  tax_rate = 0.08
  total = price + price * tax_rate
  print(f"Total: ${total:.2f}")  # Total: $21.59
  ```

- Unary + and - operators

  Unlike JavaScript, Python’s unary + and - operators don’t perform string-to-number conversion. They only work on numeric types.

  ```py
  num = 42
  print(+num)   # 42
  print(-num)   # -42
  ```

  But trying to apply them to strings raises an error:

  ```py
  str_num = "42"
  print(+str_num)  # TypeError: bad operand type for unary +: 'str'
  ```

  So, always convert explicitly:

  ```py
  print(+int("42"))  # 42
  ```

- Base Conversion — Binary, Octal, Hexadecimal

  Python provides both string formatting and int conversion for number systems.

  ```py
  num = 10
  print(bin(num))  # "0b1010"  (binary)
  print(oct(num))  # "0o12"    (octal)
  print(hex(num))  # "0xa"     (hexadecimal)
  ```

  You can also convert back:

  ```py
  print(int("1010", 2))   # 10  (binary to decimal)
  print(int("a", 16))     # 10  (hex to decimal)
  ```

  Equivalent to Javascript `.toString()`:

  ```js
  num.toString(2); // "1010"
  ```

- (Special Case) Mixed-Type Arithmetic

  Python does not coerce types automatically like JavaScript.

  ```py
  print("10" + "5")  # "105"
  print("10" + 5)    # TypeError: can only concatenate str (not "int") to str
  ```

  You must convert explicitly:

  ```py
  print(int("10") + 5)  # 15
  ```

  For arithmetic:

  ```py
  print("10" * 2)  # "1010" (string repetition)
  ```

  Compare with JavaScript:

  ```js
  "10" * 2; // 20 (JS coerces to number)
  ```

- (Special Case) `None`, `True`, `False` Conversions

  ```py
    print(int(True)) # 1
    print(int(False)) # 0
    print(int(None)) # TypeError
  ```

  And note that:

  ```py
  print(None == 0) # False
  print(None == "") # False
  print(None == False) # False
  ```

  Unlike JavaScript:

  ```js
  null == 0; // false
  null >= 0; // true
  ```

- (Special Case) type() — Checking Data Types

  Python’s type() acts like typeof in JavaScript.

  ```py
  x = 5
  print(type(x)) # <class 'int'>
  y = "Hello"
  print(type(y)) # <class 'str'>
  z = None
  print(type(z)) # <class 'NoneType'>
  ```

  Compare to JavaScript:

  ```js
  typeof 5; // "number"
  typeof "Hello"; // "string"
  typeof null; // "object" (quirk)
  ```

  ✅ Python fixes JS’s “null is object” bug — None has its own clean type.

🔹 Summary Comparison Table
| Operation | JavaScript | Python Equivalent |
| --------------------- | -------------------------------- | ----------------------------------- |
| String → Int | `parseInt("42")` | `int("42")` |
| String → Float | `parseFloat("3.14")` | `float("3.14")` |
| Any → String | `.toString()` | `str()` |
| Any → Number | `Number(value)` | `int()`, `float()` |
| Number formatting | `.toFixed(2)` | `format(x, ".2f")` or `round(x, 2)` |
| Binary/Hex conversion | `.toString(2)` / `.toString(16)` | `bin()`, `hex()` |
| Type check | `typeof x` | `type(x)` |
| Null type | `"object"` (quirk) | `NoneType` |
| Boolean conversion | `Boolean(value)` | `bool(value)` |
| Implicit coercion | ✅ Yes | ❌ No (explicit only) |

## `Math` Operation Module

In Python, mathematical operations are handled by the built-in math module, which provides functions and constants for performing advanced mathematical calculations. You need to import it before using.

Common Methods

```py
import math

print(math.sqrt(25))      # 5.0  → square root
print(math.pow(2, 3))     # 8.0  → power (2³)
print(math.floor(3.7))    # 3    → round down
print(math.ceil(3.7))     # 4    → round up
print(math.fabs(-9))      # 9.0  → absolute value
print(math.trunc(4.9))    # 4    → remove decimal part
print(round(3.5))         # 4    → round to nearest integer
print(math.log10(100))    # 2.0  → base-10 logarithm
print(math.log(100))      # 4.605... → natural log (base e)
print(max(1, 5, 9))       # 9    → highest value
print(min(1, 5, 9))       # 1    → lowest value
```

Common Constants

```py
import math

print(math.pi)   # 3.141592653589793
print(math.e)    # 2.718281828459045
print(math.tau)  # 6.283185307179586
print(math.inf)  # Infinity
print(math.nan)  # Not a Number (NaN)
```

Random and Advanced Functions

For random numbers, use the random module (separate from math):

```py
import random
import math

print(random.random())      # Random float between 0 and 1
print(math.sin(math.pi))    # 0.0  → sine
print(math.cos(math.pi))    # -1.0 → cosine
print(math.tan(math.pi))    # ~0.0 → tangent
print(math.sqrt(49))        # 7.0
print(math.hypot(3, 4))     # 5.0  → Pythagorean theorem √(3² + 4²)
```

Example Usage

```py
import math

radius = 5
area = math.pi * math.pow(radius, 2)
print("Circle area:", area)  # Circle area: 78.53981633974483
```

# Operator

## Arithmetic Operators

Used for mathematical calculations:

- (+) (Addition): Adds numbers or concatenates strings

  ```py
  sum_result = 5 + 3  # 8
  text = "Hello" + " World"  # "Hello World"
  ```

- (-) (Subtraction): Subtracts numbers

  ```py
  difference = 10 - 5  # 5
  ```

- (\*) (Multiplication): Multiplies numbers or repeats sequences

  ```py
  product = 4 * 3  # 12
  repeated = "Hi" * 3  # "HiHiHi"
  ```

- (/) (Division): Divides numbers (always returns float)

  ```py
  quotient = 15 / 3  # 5.0
  quotient2 = 7 / 2  # 3.5
  ```

- (//) Floor Division: Divides and rounds down to nearest integer

  ```py
  floor_result = 7 // 2  # 3
  ```

- (%) (Modulus): Returns the division remainder

  ```py
  remainder = 10 % 3  # 1
  ```

- \*\* (Exponentiation): is right-to-left associative/precedence. Same as x^2 or x² in mathematical notation.

  ```py
  result = 2 ** (3 ** 2)
  print(result)  # 512

  # Same associativity rule: evaluates exponent from right to left
  # (2 ** 3 ** 2) means 2 ** (3 ** 2) → 2 ** 9 → 512
  ```

- (+=) Increment and (-=) Decrements operators (It was for main loop function)

  Python doesn’t have dedicated increment (++) or decrement (--) operators like JavaScript or C-based languages.

  Instead, you use augmented assignment operators such as += and -= to update variable values.

  Developers still often use the variable name i for loop counters, short for “index” or “iterator,” as a long-standing programming convention.

  Increment Operator (+=) - Increments the value of the variable by 1.

  Excrement Operator (-=) - Decrements the value of the variable by 1.

  ```
  What they do:
      += = add 1
      -= = subtract 1
  Two ways to write them:
  (x+=, x-=)
      Returns the current value
      Then changes the variable
  (+=x, -=x)
      Changes the variable first
      Then returns the new value
  ```

  ```py
  x = 5
  x += 1  # increment
  print(x)  # 6

  x -= 1  # decrement
  print(x)  # 5
  ```

  **Explanation**

  What they do conceptually:

  ```
  x += 1   →  x = x + 1
  x -= 1   →  x = x - 1
  ```

## Assignment Operators

Used to assign values to variables:

- (=) Basic assignment

  ```py
  x = 10
  ```

- (+=) Addition assignment

  ```py
  y = 5
  y += 3  # Same as y = y + 3
  print(y)  # 8

  greet = 'Hello'
  greet += ' World'

  print(greet) # Hello World
  ```

- (-=) Subtraction assignment

  ```py
  z = 10
  z -= 4  # 6

  greet = 'Hello'
  greet -= ' World'

  print(greet) # TypeError: unsupported operand type(s) for -=: 'str' and 'str'
  ```

- (\*=) Multiplication assignment

  ```py
  a = 3
  a *= 2  # 6

  greet = 'Hello'
  greet *= 3

  print(greet) # HelloHelloHello
  ```

- (\*\*=) Exponentiation assignment

  ```py
  power = 2
  power **= 3

  print(power) # 8
  ```

- (/=) Division assignment

  ```py
  b = 8
  b /= 2  # 4.0


  greet = 'Hello'
  greet /= 'World'

  print(greet) # TypeError: unsupported operand type(s) for /=: 'str' and 'str'
  ```

- (//=) Floor division assignment

  ```py
  c = 9
  c //= 2  # 4
  ```

- (%=) Modulus assignment

  ```py
  d = 7
  d %= 2  # 1
  ```

- (\*\*=) Exponentiation assignment
  ```py
  e = 3
  e **= 2  # 9
  ```

## Comparison Operators

Used to compare values:

- (==) Equality: Checks if values are equal (no type coercion)

  ```py
  5 == 5  # True
  5 == "5"  # False
  ```

- (!=) Inequality: Checks if values are not equal

  ```py
  5 != 6  # True
  5 != "5"  # True
  ```

- (>) (Greater than): Checks if left value is greater

  ```py
  10 > 5; # true
  ```

- (<) (Less than): Checks if left value is smaller

  ```py
  5 < 10; # true
  ```

- (>=) (Greater than or equal): Checks if left value is greater or equal

  ```py
  5 >= 5; # true
  ```

- (<=) (Less than or equal): Checks if left value is smaller or equal

  ```py
  5 <= 10; # true
  ```

- Chained comparisons (Python-only feature):
  ```py
  x = 7
  print(5 < x < 10)  # True (Python evaluates in sequence)
  ```

## Logical Operators

Used to determine logic between variables or values:

- (and) Logical AND: Returns `True` if both operands are true

  ```py
  True and True  # True
  True and False  # False
  ```

  ```py
  result = True and "hello"
  print(result)  # "hello"

  result = 0 and 3
  print(result)  # 0 (since 0 is falsy)
  # (Since 0 is a falsy value, the number 0 is logged to the console.)

  result = False and 0
  print(result)  # False
  # (Since false is a falsy value, then false is logged to the console.)

  if 2 < 3 and 3 < 4:
    print("The if block runs")
  else:
    print("The else block runs")
  # The if block runs
  ```

- (or) Logical OR: Returns `True` if at least one operand is true

  ```py
  True or False  # True
  False or False  # False
  ```

  ```py
  result = "This is truthy" or False
  print(result)  # "This is truthy"

  result = 0 or "This is truthy"
  print(result)  # "This is truthy"

  user_input = ""
  if user_input or "Guest":
      print("A user is present")
  else:
      print("No user detected")

  # A user is present (since "" is falsy, "Guest" is used)
  ```

- (not) Logical NOT: Reverses the boolean result

  ```py
  not True  # False
  not False  # True
  ```

  ```py
  # Basic boolean negation
  print(not "Hello")  # False (non-empty string is truthy)
  print(not "")       # True (empty string is falsy)

  # The NOT operator converts non-boolean values to boolean first, then negates
  print(not "Hello"); # false (string is truthy, so !truthy becomes false)
  print(not ""); # true (empty string is falsy, so !falsy becomes true)

  # Useful for checking empty values
  username = ""
  if not username:
      print("Username is required!")  # Executes

  # Double negation for coercing truthy/falsy to boolean
  print(bool(0))       # False
  print(bool("text"))  # True
  print(bool(None))    # False

  # Using NOT in conditions
  const isLoggedIn = false;
  if (!isLoggedIn) {
    console.log("Please log in first!"); // This will execute
  }
  ```

## Other Important Operators

- Ternary conditional expression: Short form of if-else

  ```py
  status = "Adult" if age >= 18 else "Minor"
  ```

  ```py
  is_logged_in = True
  msg = "Welcome back!" if is_logged_in else "Please log in."
  print(msg)  # Welcome back!
  ```

  ```py
  import random

  fortunes = [
      "Your cat will look very cuddly today.",
      "The weather will be nice tomorrow.",
      "Be cautious of your new neighbors.",
      "You will find a new hobby soon.",
      "It would be wise to avoid the color red today."
  ]

  selected_fortune = random.choice(fortunes)
  print(selected_fortune)
  ```

- Safe property access (Optional Chaining equivalent):

  Python does not have ?., but .get() and dict.get() safely return None instead of an error.

  ```py
  user = {
      "name": "John",
      "profile": {
          "email": "john@example.com",
          "address": {
              "street": "123 Main St",
              "city": "Somewhere",
          },
      },
  }

  print(user.get("profile", {}).get("address", {}).get("street"))  # "123 Main St"
  print(user.get("profile", {}).get("phone", {}).get("number"))    # None
  ```

- Nullish coalescing equivalent (??):

  Use x if x is not None else y

  ```py
  username = None
  display_name = username if username is not None else "Anonymous"
  print(display_name)  # "Anonymous"
  ```

- Unpacking / Spread equivalent (...):

  Python uses the `*` (for lists/tuples) and `**` (for dicts) unpacking operators.

  ```py
  old_list = [1, 2, 3]
  new_list = [*old_list, 4, 5]
  print(new_list)  # [1, 2, 3, 4, 5]
  ```

  ```py
  original_dict = {"a": 1, "b": 2}
  merged = {**original_dict, "c": 3}
  print(merged)  # {'a': 1, 'b': 2, 'c': 3}
  ```

- Bitwise Operators (&, |, ^, ~, <<, >>)

  (&) bitwise AND operator returns a 1 in each bit position for which the corresponding bits of both operands are 1.

  (|) bitwise OR operator returns a 1 in each bit position for which the corresponding bits of either or both operands are 1.

  (^) bitwise XOR operator returns a 1 in each bit position for which the corresponding bits of either, but not both, operands are 1.

  (~) bitwise NOT operator inverts all the bits of its operand.

  (<<) left shift operator shifts all bits to the left by a specified number of positions.

  (>>) right shift operator shifts all bits to the right.

  ```py
  a = 5  # Binary: 101
  b = 3  # Binary: 011

  print(a & b)  # 1 (AND)
  print(a | b)  # 7 (OR)
  print(a ^ b)  # 6 (XOR)
  print(~a)     # -6 (NOT)
  print(a << 1) # 10 (left shift)
  print(a >> 1) # 2 (right shift)
  ```

- Unary Operators (+, -, not, ~):
  Act on a single operand to modify or check values.

  (+) unary plus operator converts its operand into a number.
  If the operand is already a number, it remains unchanged.

  (-) unary negation operator negates the value of the operand.

  (not) unary logical NOT operator flips the boolean value of its operand

  (~) bitwise NOT operator inverts the binary representation of a number

  ```py
  num = "42"
  print(+int(num))  # 42
  print(-int(num))  # -42

  is_online = True
  print(not is_online)  # False

  a = 5  # 00000101 → 11111010
  print(~a)  # -6
  ```

- void equivalent:

  Python doesn’t have `void`; functions that don’t return anything implicitly return `None`.

  ```py
  def example():
      2 + 2

  print(example())  # None
  ```

- typeof equivalent:

  Python uses type() or isinstance().

  ```py
  num = 42
  print(type(num))         # <class 'int'>
  print(isinstance(num, int))  # True
  ```

## Membership / Identity

### Membership Operators: `in`, `not in`

Used to test whether a value exists in a sequence or collection.

- `in` — Returns `True` if the value is found

  ```py
  fruits = ["apple", "banana", "cherry"]
  print("apple" in fruits)   # True
  print("mango" in fruits)   # False
  ```

  Works with strings too:

  ```py
  text = "Hello World"
  print("Hello" in text)  # True
  print("bye" in text)    # False
  ```

  Also works for dictionary keys:

  ```py
  user = {"name": "Alice", "age": 25}
  print("name" in user)  # True (checks keys)
  print("Alice" in user) # False (doesn't check values)
  ```

- `not in` — Returns `True` if the value is not found
  ```py
  numbers = [1, 2, 3, 4]
  print(5 not in numbers)  # True
  print(2 not in numbers)  # False
  ```

Comparison to JavaScript:
| JavaScript Example | Python Equivalent | Meaning |
| ------------------ | ----------------- | ----------------------------------- |
| `"x" in arr` | `"x" in arr` | Same behavior for lists and strings |
| `"key" in obj` | `"key" in dict` | Checks only keys (JS checks props) |
| `!("x" in arr)` | `"x" not in arr` | Negated membership |

### Identity Operators `is`, `is not`

Used to compare object identity, not value equality.

These tell you whether two variables refer to the same object in memory, not whether their contents are equal.

- `is` — Returns `True` if both variables point to the same object

  ```py
  a = [1, 2, 3]
  b = a
  c = [1, 2, 3]

  print(a is b)  # True — both refer to the same list
  print(a is c)  # False — same contents, different memory objects
  ```

- `is` not — Returns `True` if they are not the same object

  ```py
  name = "Alice"
  alias = name
  clone = "Alice"

  print(name is alias)  # True (same object)
  print(name is not clone)  # True or False? Depends on interning
  ```

  (Small strings and numbers may be “interned” — stored once for efficiency — so identity can appear True even for separately written literals.)

Why is `is` different from `==`:

```py
x = [1, 2, 3]
y = [1, 2, 3]

print(x == y)  # True (same content)
print(x is y)  # False (different memory references)
```

You use `is` for checking identity, such as comparing to `None`:

```py
x = None
if x is None:
    print("x has no value")
```

Never use `== None` — always use `is None` and is `not None`.

Comparison to JavaScript:
| Concept | JavaScript | Python | Meaning |
| ------------------------- | ----------------------- | ---------------- | ------------------------------------------------- |
| Value equality | `a == b` | `a == b` | Compare values (coercive in JS, strict in Python) |
| Strict equality | `a === b` | `a == b` | JS strict equals → Python equals (no coercion) |
| Identity (same reference) | `a === b` (for objects) | `a is b` | Same memory object |
| Non-identity | `a !== b` | `a is not b` | Not same object |
| Membership check | `"x" in arr` | `"x" in arr` | Same logic for sequences |
| Negated membership | `!("x" in arr)` | `"x" not in arr` | Logical opposite |

🧠 Example Combining Both

```py
user = {"name": "Alice", "role": "admin"}

# Membership check
if "role" in user:
    print("Role found!")  # Role found!

# Identity check
user_copy = user
print(user_copy is user)  # True

new_user = {"name": "Alice", "role": "admin"}
print(new_user == user)   # True (same data)
print(new_user is user)   # False (different objects)
```

🔬 Advanced: Identity & Interning Behavior

Python may reuse immutable objects (like small integers and short strings) internally for efficiency.

```py
a = 256
b = 256
print(a is b)  # True (interned)

x = 1000
y = 1000
print(x is y)  # False (not interned)

s1 = "hello"
s2 = "hello"
print(s1 is s2)  # True (string interning)
```

Mutable types like list, dict, or set are never interned.

✅ Summary Table
| Operator | Description | Example | Result |
| -------- | ----------------------------------- | -------------------- | ---------- |
| `in` | Value exists in container | `"a" in ["a","b"]` | True |
| `not in` | Value not in container | `"z" not in "pizza"` | False |
| `is` | Two vars refer to same object | `x is y` | True/False |
| `is not` | Two vars refer to different objects | `x is not y` | True/False |

# Collections & Objects (Dictionary)

## Braces Literal Syntax

```py
Curly Braces {}         - Objects & Code Blocks
    Objects             : { name: "John", age: 25 }
    Code blocks         : if (condition) { ... }
    Function bodies     : function() { return "hello"; }
    Destructuring       : const { name } = person
```

```py
Square Brackets []      - Arrays & Property Access
    Arrays              : [1, 2, 3, "hello"]
    Array access        : array[0]
    Dynamic properties  : object[variableName]
    Computed properties : { [key]: value }
```

```py
Parentheses ()          - Functions & Grouping
    Function calls      : myFunction()
    Parameters          : function(a, b) { }
    Grouping            : (2 + 3) * 4
    Conditions          : if (x > 5)
```

```jpy
Memory Tips:
{} = "Container for properties" (objects) or "group statements" (blocks)
[] = "List of items" (arrays) or "get item by position/key"
() = "Execute this" (functions) or "do this first" (grouping)
```

```py
# (Special Case) Bracket notation
greeting = "hello"
print(greeting[1])  # Output: e
print(greeting[len(greeting) - 1])  # Output: o
```

## Dictionary (Object) Manipulation Structure Levels

Accessing Nested Dictionary Data

```py
person = {
    "name": "Alice",
    "age": 30,
    "contact": {
        "email": "alice@example.com",
        "phone": {
            "home": "123-456-7890",
            "work": "098-765-4321",
        },
    },
}

print(person["name"])                 # Alice
print(person["age"])                  # 30
print(person["contact"]["phone"]["work"])  # 098-765-4321
```

Object property operations:

- Add properties: `person["job"] = "Engineer"` or `person["hobby"] = "Knitting"`

  ```py
  person["job"] = "Engineer"
  person["hobby"] = "Knitting"
  print(person)
  # {'name': 'Alice', 'age': 30, 'contact': {...}, 'job': 'Engineer', 'hobby': 'Knitting'}
  ```

- Delete properties: del person["job"]

  ```py
  del person["job"]
  print(person.get("job"))  # None
  ```

- Check if property exists: 'name' in person

  ```py
  print("name" in person)  # True
  ```

- Check if a dictionary has a specific key: .get() or .keys()
  ```py
  print("name" in person.keys())  # True
  print("job" in person.keys())   # False
  ```
- Get a property safely with default value (like optional chaining):

  ```py
  print(person.get("nickname", "No nickname"))  # "No nickname"
  ```

  Unlike JavaScript, Python dictionaries don’t throw an error when you access a missing key via .get().

  Instead, they return None (or a default you specify).

### Natural Hierarchical Structure Levels in Different Variable Declarations {Classification}

Single level, no structure.

```py
name = "John"    # Single level, no structure
age = 25         # Single level, no structure
score = 100      # Single level, no structure
```

It doesn't matter how you call the identifier or classification as long as clear on structure.

```py
record_collection = {
    # This is the main (records) dictionary
    5439: {
        # This is a key (id) in the main dictionary
        "albumTitle": "ABBA Gold",  # (property) of the id dictionary
        "artist": "",                # (property) of the id dictionary
        "tracks": [],                # (property) of the id dictionary
    },
}


def update_records(records, record_id, prop, value):
    if record_id not in records:
        return records
    if value == "":
        records[record_id].pop(prop, None)
    else:
        records[record_id][prop] = value
    return records


print(update_records(record_collection, 5439, "artist", "ABBA"))
#                        ^records          ^id      ^prop      ^value
```

Example of Well-Identified Dictionary Structure

```py
students = {
    "STU_001": {  # Identifier with clear prefix
        "name": "John",           # Property with string value
        "grades": [90, 85],       # Property with list value
        "active": True,           # Property with boolean value
    },
}
```

Numeric identifier style

```py
records = {
    2548: {                       # Numeric identifier
        "albumTitle": "...",      # String property
        "tracks": [],             # List property
    },
}
```

More explicit classification

```py
inventory = {
    "itemId": {                   # Named identifier
        "type": "product",        # Classification property
        "metadata": {             # Nested classification
            "category": "electronics",
            "subCategory": "phones",
        },
    },
}
```

E-commerce System

```py
ecommerce_system = {
    "STORE_001": {  # Level 1: Store ID
        "details": {  # Level 2: Store Details
            "name": "Main Branch",
            "location": {  # Level 3: Location Details
                "street": "123 Main St",
                "city": "Boston",
                "zip": "02108",
            },
        },
        "inventory": {  # Level 2: Inventory
            "products": [  # Level 3: Product List
                {  # Level 4: Product Details
                    "id": "P001",
                    "name": "Laptop",
                    "specs": {  # Level 5: Product Specifications
                        "brand": "Dell",
                        "model": "XPS",
                    },
                },
            ],
        },
    },
}
```

School Management System

```py
school_system = {
    "departments": {  # Level 1: Department Structure
        "DEPT_001": {  # Level 2: Department ID
            "name": "Computer Science",
            "courses": {  # Level 3: Course Structure
                "CS101": {  # Level 4: Course Details
                    "title": "Intro to Programming",
                    "students": [  # Level 5: Student List
                        {  # Level 6: Student Details
                            "id": "STU_001",
                            "grades": {
                                "midterm": 95,
                                "final": 88,
                            },
                        },
                    ],
                },
            },
        },
    },
}
```

File System Structure

```py
file_system = {
    "root": {  # Level 1: Root Directory
        "documents": {  # Level 2: Subdirectory
            "work": {  # Level 3: Nested Directory
                "files": [  # Level 4: File List
                    {  # Level 5: File Details
                        "name": "report.doc",
                        "metadata": {
                            "size": "1.2MB",
                            "created": "2023-01-01",
                            "type": "document",
                        },
                    },
                ],
            },
        },
    },
}
```

Safe Nested Access (Equivalent to JS Optional Chaining ?.)

Python doesn’t have ?., but you can chain .get() calls safely:

```py
user = {
    "name": "John",
    "profile": {
        "email": "john@example.com",
        "address": {
            "street": "123 Main St",
            "city": "Somewhere",
        },
    },
}

print(user.get("profile", {}).get("address", {}).get("street"))  # "123 Main St"
print(user.get("profile", {}).get("phone", {}).get("number"))    # None
```

Or define a small helper for optional chaining-like access:

```py
def safe_get(data, *keys):
    for key in keys:
        if isinstance(data, dict):
            data = data.get(key)
        else:
            return None
    return data

print(safe_get(user, "profile", "address", "street"))  # "123 Main St"
print(safe_get(user, "profile", "phone", "number"))    # None
```

✅ Summary Comparison

| Operation                | JavaScript Syntax        | Python Equivalent                       |
| ------------------------ | ------------------------ | --------------------------------------- |
| Access property          | `obj.key` / `obj["key"]` | `dict["key"]`                           |
| Add property             | `obj.newKey = val`       | `dict["newKey"] = val`                  |
| Delete property          | `delete obj.key`         | `del dict["key"]`                       |
| Check if property exists | `"key" in obj`           | `"key" in dict`                         |
| Get safely (avoid error) | `obj.key ?? "default"`   | `dict.get("key", "default")`            |
| Optional chaining        | `obj?.key?.sub`          | `dict.get("key", {}).get("sub")`        |
| Loop through properties  | `for (let k in obj)`     | `for k in dict:`                        |
| Nested hierarchy         | Objects inside objects   | Dicts inside dicts / lists inside dicts |

## String Methods

Python provides a number of built-in methods that make working with strings a breeze. They include, but are not limited to, the following:

- upper(): Returns a new string with all characters converted to uppercase.
  my_str = 'hello world'

  ```py
  uppercase_my_str = my_str.upper()
  print(uppercase_my_str) # HELLO WORLD
  ```

- lower(): Returns a new string with all characters converted to lowercase.

  ```py
  my_str = 'Hello World'

  lowercase_my_str = my_str.lower()
  print(lowercase_my_str) # hello world
  ```

- strip(): Returns a new string with the specified leading and trailing characters removed. If no argument is passed it removes leading and trailing whitespace.

  ```py
  my_str = ' hello world '

  trimmed_my_str = my_str.strip()
  print(trimmed_my_str) # "hello world"
  ```

- replace(old, new): Returns a new string with all occurrences of old replaced by new.

  ```py
  my_str = 'hello world'

  replaced_my_str = my_str.replace('hello', 'hi')
  print(replaced_my_str) # hi world
  ```

- split(separator): Splits a string on a specified separator into a list of strings. If no separator is specified, it splits on whitespace.

  ```py
  my_str = 'hello world'

  split_words = my_str.split()
  print(split_words) # ['hello', 'world']
  ```

- join(iterable): Joins elements of an iterable into a string with a separator.

  ```py
  my_list = ['hello', 'world']

  joined_my_str = ' '.join(my_list)
  print(joined_my_str) # hello world
  ```

- startswith(prefix): Returns a boolean indicating if a string starts with the specified prefix.

  ```py
  my_str = 'hello world'

  starts_with_hello = my_str.startswith('hello')
  print(starts_with_hello) # True
  ```

- endswith(suffix): Returns a boolean indicating if a string ends with the specified suffix.

  ```py
  my_str = 'hello world'

  ends_with_world = my_str.endswith('world')
  print(ends_with_world) # True
  ```

- find(substring): Returns the index of the first occurrence of substring, or -1 if it doesn't find one.

  ```py
  my_str = 'hello world'

  world_index = my_str.find('world')
  print(world_index) # 6
  ```

- count(substring): Returns the number of times a substring appears in a string.

  ```py
  my_str = 'hello world'

  o_count = my_str.count('o')
  print(o_count) # 2
  ```

- capitalize(): Returns a new string with the first character capitalized and the other characters lowercased.

  ```py
  my_str = 'hello world'

  capitalized_my_str = my_str.capitalize()
  print(capitalized_my_str) # Hello world
  ```

- isupper(): Returns True if all letters in the string are uppercase and False if not.

  ```py
  my_str = 'hello world'

  is_all_upper = my_str.isupper()
  print(is_all_upper) # False
  ```

- islower(): Returns True if all letters in the string are lowercase and False if not.

  ```py
  my_str = 'hello world'

  is_all_lower = my_str.islower()
  print(is_all_lower) # True
  ```

- title(): Returns a new string with the first letter of each word capitalized.

  ```py
  my_str = 'hello world'

  title_case_my_str = my_str.title()
  print(title_case_my_str) # Hello World
  ```

## List Methods: append(), extend(), insert(), pop(), remove(), sort()

## Tuple Operations: indexing, slicing, unpacking

## Dict Methods: .keys(), .values(), .items(), .get(), .update()

## Set Methods: .add(), .remove(), .union(), .intersection()

## Object Orientation: class, **init**, self

## Data Model Hooks: **str**, **repr**, **len**, **iter**

# Control Flow

## Conditionals: if/elif/else

## Loops: for, while, break, continue

## Loop Tools: enumerate(), zip(), range()

## Exception Handling: try/except/finally/else, raise

# Functions & Scope

Functions in Python are reusable blocks of code that perform specific tasks or compute values. They make code modular, easier to test, and reusable — just like in JavaScript.

You define a function with the def keyword, optionally pass in parameters, and call it by name. Think of it as a “mini program” inside your main program.

- Function declaration:

```py
def greet(name):
    print("Hello,", name + "!")

greet("Alice")  # Hello, Alice!
```

A function can take parameters (placeholders) that receive arguments (actual values). Parameters make functions flexible and reusable.

```py
def greet(name):
    print("Hello,", name + "!")

greet("Alice")
greet("Nick")
```

Every function in Python returns a value.
If you don’t use return, the function implicitly returns None.

```py
def do_something():
    print("Doing something...")

result = do_something()
print(result)  # None
```

To return a specific value, use the return keyword.

```py
def calculate_sum(num1, num2):
    return num1 + num2

print(calculate_sum(3, 4))  # 7
```

You can also assign functions to variables — functions are first-class objects in Python:

```py
sum_func = lambda a, b: a + b
print(sum_func(3, 4))  # 7
```

Python supports default parameter values — used when no argument is provided.

```py
def greetings(name="Guest"):
    print("Hello,", name + "!")

greetings()        # Hello, Guest!
greetings("Anna")  # Hello, Anna!
```

You can even define multiple defaults:

```py
def mystery(a, b=3):
    return a * b

print(mystery(4))  # 12
```

- Lambda (Anonymous) Functions

Arrow functions in JavaScript are conceptually similar to lambda functions in Python. They’re used for short, simple, one-line operations.

```py
# Regular function
def add(a, b):
    return a + b

# Lambda equivalent
add = lambda a, b: a + b

print(add(3, 4))  # 7
```

Lambdas are often used inline with tools like map(), filter(), or sorted().

```py
numbers = [1, 2, 3, 4]
doubles = list(map(lambda x: x * 2, numbers))
print(doubles)  # [2, 4, 6, 8]
```

You can return values directly or assign them before returning:

```py
def calculate_area(width, height):
    area = width * height
    return area

print(calculate_area(5, 3))  # 15
```

You can simplify one-liners like this:

```py
def calculate_area(width, height): return width * height
```

## Closures

## Decorators: @decorator syntax

## Scopes: LEGB rule (Local, Enclosing, Global, Built-in)

## Generators: yield, yield from

# Asynchronous Python

## Coroutines: async def, await

## Event Loop: asyncio.run()

## Tasks / Futures: asyncio.create_task, Future

## Async Iteration: async for, async with

# Modules & Imports

## Import Variants: import, from ... import ..., import as

## Packages: **init**.py, namespace packages

## Built-in Modules: math, os, sys, json

## Virtual Environments: venv, pip

# Advanced Constructs

## Comprehensions: [x*x for x in range(5)]

## Context Managers: with, custom **enter** / **exit**

## Iterators & Iterables: iter(), next()

## Metaclasses: class X(metaclass=...)

## Typing: from typing import List, Dict, Optional

# Error & Debugging

## Exceptions: built-in (ValueError, TypeError)

## Assertion: assert condition

## Logging: import logging

## Debugging: pdb, breakpoint()

# Common Gotchas & Semantics

## Mutability (list vs tuple)

## Default argument traps (def f(x=[]))

## is vs ==

## Integer caching and interning

## Late binding in closures
