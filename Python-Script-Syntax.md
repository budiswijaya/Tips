- [Basic Concepts](#basic-concepts)
  - [Python Introduction](#python-introduction)
  - [Character Encoding](#character-encoding)
  - [Number Systems](#number-systems)
  - [Variable Naming Conventions](#variable-naming-conventions)
  - [Variable Declarations](#variable-declarations)
  - [String Manipulation](#string-manipulation)
  - [Console.logging for debugging](#consolelogging-for-debugging)
  - [Modules \& Imports/Exports](#modules--importsexports)
- [Data Types](#data-types)
  - [Primitive (Built-ins): int, float, bool, str, bytes, NoneType](#primitive-built-ins-int-float-bool-str-bytes-nonetype)
  - [Composite / Collections: list, tuple, dict, set, frozenset](#composite--collections-list-tuple-dict-set-frozenset)
  - [Special: complex, range, memoryview](#special-complex-range-memoryview)
  - [Dynamic Typing: type(), isinstance(), id()](#dynamic-typing-type-isinstance-id)
  - [int("42"), float("3.14"), str(123)](#int42-float314-str123)
  - [Casting collections: list("abc"), tuple(\[1,2\])](#casting-collections-listabc-tuple12)
  - [Truthiness rules: empty structures → False](#truthiness-rules-empty-structures--false)
- [Operators](#operators)
  - [Arithmetic: + - \* / // % \*\*](#arithmetic--------)
  - [Comparison: \< \> \<= \>= == !=](#comparison------)
  - [Logical: and or not](#logical-and-or-not)
  - [Membership / Identity: in, not in, is, is not](#membership--identity-in-not-in-is-is-not)
  - [Assignment (Augmented): +=, -=, \*=, /=, etc.](#assignment-augmented------etc)
- [Collections \& Objects](#collections--objects)
  - [Literal Syntax: \[\], {}, ()](#literal-syntax---)
  - [Dict: {"a":1}, methods like .keys(), .values()](#dict-a1-methods-like-keys-values)
  - [Set: {1,2,3}, .union(), .intersection()](#set-123-union-intersection)
  - [Object Orientation: class, **init**, self](#object-orientation-class-init-self)
  - [Data Model Hooks: **str**, **repr**, **len**, **iter**](#data-model-hooks-str-repr-len-iter)
- [Control Flow](#control-flow)
  - [Conditionals: if/elif/else](#conditionals-ifelifelse)
  - [Loops: for, while, break, continue](#loops-for-while-break-continue)
  - [Loop Tools: enumerate(), zip(), range()](#loop-tools-enumerate-zip-range)
  - [Exception Handling: try/except/finally/else, raise](#exception-handling-tryexceptfinallyelse-raise)
- [Functions \& Scope](#functions--scope)
  - [Definitions: def, lambda](#definitions-def-lambda)
  - [Closures: inner functions capturing variables](#closures-inner-functions-capturing-variables)
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

```js
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

There are three main ways to declare variables:

- **const** - For values that won't change
- **let** - For variables that can change, but not globally
- **var** - For variables that can change globally (not recommended in modern JS)

There are also other keyway manipulation methods:

- **function** - For function declarations
- **delete** - Does not delete variables declared with var/let/const; it only deletes object properties.
- **new** - For creating objects with constructors
- **class** - For class declarations

## String Manipulation

The newline character (\n) functions similarly to the line break element (< br >) in HTML/CSS

Another great feature of template literals is that they support multiline strings. With regular strings, you would need to use escape characters (\n) to create new lines. With template literals, you can simply write the string across multiple lines, and the formatting is preserved:

```js
let poem = `Roses are red,
Violets are blue,
JavaScript is fun,
And so are you.`;
console.log(poem);

// Output:
Roses are red,
Violets are blue,
JavaScript is fun,
And so are you.
```

Escape quotes with backslash:

```js
let statement = "She said, \\"Hello!\\"";
console.log(statement); // Output: She said, "Hello!"
```

You can also escape other special characters,
such as the backslash itself (\\), or single quotes within a string surrounded by single quotes (\').

```js
let quote = 'It\\'s a beautiful day!';
console.log(quote); // Output: It's a beautiful day!
```

String interpolation with template literals:

```js
// Allow for embedding variables directly inside a string,
let name = "Alice";
let greeting = `Hello, ${name}!`; // Output: "Hello, Alice!"

// Example using string concatenation and the plus (+) operator:
let name = "Alice";
let age = 25;
let message = "My name is " + name + " and I am " + age + " years old.";
console.log(message); // Output: "My name is Alice and I am 25 years old."

// And here is an example using template literals and string interpolation:
let message = `My name is ${name} and I am ${age} years old.`;
console.log(message); // Output: "My name is Alice and I am 25 years old."
```

## Console.logging for debugging

```js
console.log()    : is used to print messages to the console for debugging purposes.
console.warn()   : is used to print warning messages.
console.error()  : is used to print error messages.

// Example below:
console.log("This is a console log message.");
console.warn("This is a warning message.");
console.error("This is an error message.");

// Result below:
This  a console log message.
! This is a warning message.
X This is an error message.
```

## Modules & Imports/Exports

Modules are files that explicitly declare what they export (make public) and what they import (use from other modules). They give JavaScript a first-class, standardized way to structure programs across files. ES Modules (ESM) are static (the imports/exports are known at parse time), support live bindings (imports “see” updates), and enable features like top-level `await`.
[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules?utm_source=chatgpt.com)

Why it exists. Before ESM, developers used script tags, IIFEs, or bundler conventions. Modules bring portability, better tooling, and clear boundaries. Node.js also supports ESM alongside the older CommonJS (require, module.exports).
[Node.js](https://nodejs.org/api/esm.html?utm_source=chatgpt.com)

- Named exports & imports

  ```js
  // math.js
  export const TWO = 2;
  export function add(a, b) {
    return a + b;
  }

  // app.js
  import { TWO, add } from "./math.js";
  ```

- Default export (one per module)

  ```js
  // api.js
  export default function request(url) {
    /* ... */
  }

  // app.js
  import request from "./api.js";
  ```

- Renaming & namespace imports

  ```js
  import { add as plus } from "./math.js";
  import * as MathLib from "./math.js";
  ```

- Re-exporting

  ```js
  export { add } from "./math.js"; // pass-through
  export * as MathLib from "./math.js"; // namespace re-export
  ```

- Dynamic import (async)

  ```js
  const mod = await import("./heavy.js"); // returns a Promise
  mod.run(); // use when needed
  ```

  Dynamic import() loads a module on demand and returns a Promise.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/import?utm_source=chatgpt.com)

- Module metadata

  ```js
  console.log(import.meta.url); // URL of this module file
  ```

  `import.meta` exposes context info about the current module. Some environments also provide `import.meta.resolve()`.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/import.meta?utm_source=chatgpt.com)

- Top-level await (in modules only)
  ```js
  // config.js (ES module)
  const resp = await fetch("/config.json");
  export const config = await resp.json();
  ```
  `await` is allowed at the module’s top level; the module pauses loading until the awaited Promise settles.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await?utm_source=chatgpt.com)

Visualization (module graph).

```
[ app.js ] --imports--> [ math.js ]
        \--dynamic-->   [ heavy.js ] (only when needed)
```

- You can’t use `import`/`export` inside blocks or conditionals (they’re static).
- Imported bindings are live: if the exporter updates a binding, importers “see” it.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export?utm_source=chatgpt.com)
- Top-level `await` works in modules, not classic scripts.
  [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await?utm_source=chatgpt.com)

Modules & Imports/Exports → Program structure (ESM): import, export, import(), import.meta, top-level await. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules?utm_source=chatgpt.com)

# Data Types

## Primitive (Built-ins): int, float, bool, str, bytes, NoneType

## Composite / Collections: list, tuple, dict, set, frozenset

## Special: complex, range, memoryview

## Dynamic Typing: type(), isinstance(), id()

## int("42"), float("3.14"), str(123)

## Casting collections: list("abc"), tuple([1,2])

## Truthiness rules: empty structures → False

# Operators

## Arithmetic: + - \* / // % \*\*

## Comparison: < > <= >= == !=

## Logical: and or not

## Membership / Identity: in, not in, is, is not

## Assignment (Augmented): +=, -=, \*=, /=, etc.

# Collections & Objects

## Literal Syntax: [], {}, ()

## Dict: {"a":1}, methods like .keys(), .values()

## Set: {1,2,3}, .union(), .intersection()

## Object Orientation: class, **init**, self

## Data Model Hooks: **str**, **repr**, **len**, **iter**

# Control Flow

## Conditionals: if/elif/else

## Loops: for, while, break, continue

## Loop Tools: enumerate(), zip(), range()

## Exception Handling: try/except/finally/else, raise

# Functions & Scope

## Definitions: def, lambda

## Closures: inner functions capturing variables

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
