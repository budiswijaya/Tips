- [Basic Concepts](#basic-concepts)
  - [JavaScript Introduction](#javascript-introduction)
  - [Character Encoding](#character-encoding)
  - [Number Systems](#number-systems)
  - [Variable Naming Conventions](#variable-naming-conventions)
  - [Variable Declarations](#variable-declarations)
  - [String Literals \& Formatting](#string-literals--formatting)
  - [Console.logging for debugging](#consolelogging-for-debugging)
  - [Modules \& Imports/Exports](#modules--importsexports)
- [Data Types](#data-types)
  - [Primitive Data \& Non Primitive Data](#primitive-data--non-primitive-data)
    - [The Real Meaning of “Primitive” vs “Non-Primitive”](#the-real-meaning-of-primitive-vs-non-primitive)
  - [Type Checking](#type-checking)
  - [Type Conversion](#type-conversion)
  - [`Math` Operations](#math-operations)
  - [JSON](#json)
- [Operator](#operator)
  - [Arithmetic Operators](#arithmetic-operators)
  - [Assignment Operators](#assignment-operators)
  - [Comparison Operators](#comparison-operators)
  - [Logical Operators](#logical-operators)
  - [Other Important Operators](#other-important-operators)
- [Objects \& Arrays](#objects--arrays)
  - [Braces Literal Syntax](#braces-literal-syntax)
  - [**Comparative Syntax Table — `{}`, `[]`, `()`**](#comparative-syntax-table----)
  - [String Manipulation](#string-manipulation)
  - [Object Manipulation Structure Levels](#object-manipulation-structure-levels)
    - [Natural Hierarchical Structure Levels in Different Variable Declarations {Classification}](#natural-hierarchical-structure-levels-in-different-variable-declarations-classification)
    - [Object Constructors](#object-constructors)
  - [Array Constructors](#array-constructors)
  - [Array Methods](#array-methods)
  - [Tuple-like Structures (JS/TS)](#tuple-like-structures-jsts)
  - [Object Methods](#object-methods)
  - [Set Methods](#set-methods)
  - [Classes and Constructors](#classes-and-constructors)
  - [Object Model Hooks](#object-model-hooks)
  - [Classes \& Prototypes (Object-Oriented JavaScript)](#classes--prototypes-object-oriented-javascript)
- [Control Flow](#control-flow)
  - [if/else if/ else](#ifelse-if-else)
  - [switch](#switch)
  - [Loops](#loops)
    - [Primary Loop Structures (for... / while / do... while)](#primary-loop-structures-for--while--do-while)
    - [Specialized Loops (for... of / for... in / forEach())](#specialized-loops-for-of--for-in--foreach)
    - [Loop Control (break/continue/labelled loops)](#loop-control-breakcontinuelabelled-loops)
    - [There are a lot of purpose to use loop:](#there-are-a-lot-of-purpose-to-use-loop)
  - [return](#return)
  - [throw](#throw)
  - [try / catch / finally](#try--catch--finally)
- [Functions \& Scope](#functions--scope)
  - [Function declaration:](#function-declaration)
  - [`=>` Arrow functions](#-arrow-functions)
  - [Closures](#closures)
  - [Scope Accessibility](#scope-accessibility)
- [Asynchronous JavaScript](#asynchronous-javascript)
  - [async Function](#async-function)
    - [Clear Difference: async function vs normal function](#clear-difference-async-function-vs-normal-function)
  - [Promises](#promises)
    - [new Promise (executor)](#new-promise-executor)
    - [Static methods](#static-methods)
    - [Instance methods (.then / .catch / .finally)](#instance-methods-then--catch--finally)
  - [Iterators \& Generators (sync and async)](#iterators--generators-sync-and-async)
  - [Error handling in async (try/catch with await)](#error-handling-in-async-trycatch-with-await)
- [TypeScript vs JavaScript — Deep Technical Documentation](#typescript-vs-javascript--deep-technical-documentation)
  - [1. Grammar (Syntax Layer)](#1-grammar-syntax-layer)
  - [2. Constructs TypeScript Adds That JavaScript Lacks](#2-constructs-typescript-adds-that-javascript-lacks)
  - [3. Semantics (Meaning \& Runtime Behavior)](#3-semantics-meaning--runtime-behavior)
  - [4. React + TypeScript Event Deep Dive](#4-react--typescript-event-deep-dive)
  - [5. Summary Table](#5-summary-table)
  - [6. Why TypeScript Exists](#6-why-typescript-exists)
  - [7. Mental Model](#7-mental-model)

# Basic Concepts

## JavaScript Introduction

Variables: Store information.

```js
let message = "Hello!";
```

Functions: Block of code that runs when called.

```js
function greet() {
  alert("Hi!");
}
```

Event Listeners: Run code when an event happens.

```js
button.addEventListener("click", greet);
```

Accessing HTML Elements:

```js
document.querySelector("button") gets the first <button>
document.getElementById("important")
document.getElementsByClassName("")
document.querySelctorAll("")
```

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

- Variable names should be descriptive and meaningful.
- Variable names should be camelCase like cityName, isLoggedIn, and veryBigNumber.
- Variable names should not start with a number. They must begin with a letter, \_, or $.
- Variable names should not contain spaces or special characters, except for \_ and $.
- Variable names should not be reserved keywords.
- Variable names are case-sensitive. age and Age are different variables.

```js
let isLoading = true;
let hasPermission = false;
let canEdit = true;

function getUserData() {
  /* ... */
}
function calculateTotal() {
  /* ... */
}
function validateInput() {
  /* ... */
}
function isValidEmail(email) {
  /* ... */
}
function hasRequiredFields(form) {
  /* ... */
}
function getProductDetails(productId) {
  /* ... */
}
function getUserProfile(userId) {
  /* ... */
}
function setUserPreferences(preferences) {
  /* ... */
}
function setPageTitle(title) {
  /* ... */
}
function handleClick() {
  /* ... */
}
function onSubmit() {
  /* ... */
}
function keyPressHandler() {
  /* ... */
}
```

When naming iterator variables and loops, it's common to use single letters like i, j, or k, but for nested loops or more complex iterations more descriptive names can be helpful:

```js
for (let i = 0; i < array.length; i++) {
  /* ... */
}

for (let studentIndex = 0; studentIndex < students.length; studentIndex++) {
  /* ... */
}
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

## String Literals & Formatting

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

## Primitive Data & Non Primitive Data

Primitive Data Types: These data types include numbers, strings, booleans, null, undefined, and symbols. These types are called "primitive" because they represent single values and are not objects. Primitive values are immutable, which means once they are created, their value cannot be changed.

- **string** - Text in quotes ("Hello" or 'Hello')
- **number** - Numeric values (1, 3.14)
- **boolean** - true/false values

Non Primitive Data Types: In JavaScript, these are objects, which include regular objects,
arrays, and functions. Unlike primitives, non-primitive types can hold multiple values as properties or elements.

- **array** - Collections of items [1, 2, 3]
- **object** - Key-value pairs { name: "John" }

Example below:

```js
let myvariable = "Hello, World!";
console.log(myvariable);

const name = "Shay";                                             //string
const age = 30;                                                  //number
const isStudent = true;                                          //boolean
const hobbies = ["reading", "coding", "gaming"];                 //array
const person = { firstName : "Shay", lastName: "Doe", age: 30 }; //object

console.log(name, age, isStudent, hobbies, person);

//Results below:
Hello, World!
Shay, 30, true, ["reading", "coding", "gaming"], { firstName: "Shay", lastName: "Doe", age: 30 }
```

- (undefined) means a variable has been declared but hasn't been given a value yet.
- (null) means the variable has been intentionally set to "nothing" and does not hold any value.
- (Infinity) represent numbers that are beyond the maximum limit with Infinity.

  ```js
  const infiniteNumber = 1 / 0;
  console.log(infiniteNumber); // Infinity
  console.log(typeof infiniteNumber); // number
  ```

- (NaN) stands for "Not a Number"

  ```js
  const notANumber = "hello world" / 2;
  console.log(notANumber); // NaN
  ```

- (-1) it means negative infinity or not found
  ```js
  console.log("freeCodeCamp".indexOf("F")); // -1
  ```

### The Real Meaning of “Primitive” vs “Non-Primitive”

Think of a primitive value as a direct box of data, like a sticky note with the number “10” written on it.

A non-primitive value is a box that points to another box, like a label that says “look over there” — it doesn’t hold the data itself, just a reference to where it lives in memory.

- Example 1 — Numbers (Primitive)

  ```js
  let x = 10;
  let y = x;
  y = 20;

  console.log(x); // 10
  console.log(y); // 20
  ```

  Why both behave the same:

  - Both numbers are primitive.
  - When you assign y = x, you copy the value, not a pointer.
  - Changing y does not affect x, because they’re separate values in memory.

- Example 2 — Arrays (Non-Primitive)

  ```js
  let a = [1, 2, 3];
  let b = a;
  b.push(4);

  console.log(a); // [1, 2, 3, 4]
  console.log(b); // [1, 2, 3, 4]
  ```

  Why both behave the same again—but differently from primitives:

  - Arrays are non-primitive — stored by reference.
  - b = a doesn’t make a new copy; it makes a new label pointing to the same list in memory.
  - When you modify b, you’re really modifying the shared data both labels point to.

  If you want a separate copy, you must do it explicitly:

  ```js
  let b = a.slice();
  ```

- Example 3 — Strings: a tricky “in-between” case

  ```js
  let s1 = "hello";
  let s2 = s1;
  s2 = "world";

  console.log(s1); // "hello"
  console.log(s2); // "world"
  ```

  Explanation:

  - Strings look like objects, but they’re immutable primitives.
  - When you assign or “change” them, you’re not editing the same string — you’re creating a new one.

🧭 The Real Difference (In Simple Words)
| Property | Primitive | Non-Primitive |
| ----------- | ---------------------------- | -------------------------------------- |
| Stored as | Actual value | Reference (pointer) |
| Mutability | Immutable (can’t be changed) | Mutable (can be changed) |
| When copied | Creates a _new value_ | Shares the _same memory address_ |
| Examples | numbers, strings, booleans | lists/arrays, objects/dicts, functions |

## Type Checking

- Function similar to typeof but more precise and easy to use

  ```js
  const isString = (val) => typeof val === "string";
  const isNumber = (val) => typeof val === "number" && !isNaN(val);
  const isObject = (val) =>
    val !== null && typeof val === "object" && !Array.isArray(val);
  const isFunction = (val) => typeof val === "function";
  const isDate = (val) => val instanceof Date && !isNaN(val);
  ```

- .isNaN() function property is used to determine whether a value is NaN or not
  ```js
  console.log(isNaN(NaN)); // true
  console.log(isNaN(undefined)); // true
  console.log(isNaN({})); // true
  console.log(isNaN(true)); // false
  console.log(isNaN(null)); // false
  console.log(isNaN(37)); // false
  console.log(isNaN("37")); // false: "37" is converted to 37
  console.log(isNaN("37.37")); // false: "37.37" is converted to 37.37
  console.log(isNaN("")); // false: empty string is converted to 0
  console.log(isNaN(" ")); // false: string with a space is converted to 0
  console.log(isNaN("shit")); // true: "shit" is not a number
  ```

Due to these potential inconsistencies, ES6 introduced Number.isNaN(). This method does not attempt to convert the parameter to a number before testing. It only returns true if the value is exactly NaN:

```js
console.log(Number.isNaN(NaN)); // true
console.log(Number.isNaN(Number.NaN)); // true
console.log(Number.isNaN(0 / 0)); // true

console.log(Number.isNaN("NaN")); // false
console.log(Number.isNaN(undefined)); // false
console.log(Number.isNaN({})); // false
console.log(Number.isNaN("shit")); // false
```

Number.isNaN() provides a more reliable way to check for NaN values, especially in cases where type coercion might lead to unexpected results with the global isNaN() function. In practice, when dealing with numerical operations or user inputs that should be numbers, it's often necessary to check for NaN to handle errors or unexpected inputs gracefully.

```js
function divide(a, b) {
  let result = a / b;
  if (Number.isNaN(result)) {
    return "Error: Division resulted in NaN";
  }
  return result;
}

console.log(divide(10, 2)); // 5
console.log(divide(10, 0)); // Infinity
console.log(divide(0, 0)); // "Error: Division resulted in NaN"
```

## Type Conversion

Converting between types:

- `parseFloat()` - String to decimal number
- `parseInt()` - String to integer

Are two essential methods in JavaScript for converting strings to numbers.
parseFloat() converts a string to a floating-point number. Floating-point is a number with a decimal point.
parseInt() converts a string to an integer. Integer is a whole number without a decimal point.
These methods are particularly useful when dealing with user input or
processing data that comes in string format but needs to be treated as numerical values.

```js
console.log(parseFloat("3.14")); // Output: 3.14
console.log(parseFloat("3.14 abc")); // Output: 3.14
console.log(parseFloat("3.14.5")); // Output: 3.14
console.log(parseFloat("abc 3.14")); // Output: NaN
console.log(parseFloat("  3.14")); // Output: 3.14
console.log(parseFloat("+3.14")); // Output: 3.14

console.log(parseInt("42")); // Output: 42
console.log(parseInt("42px")); // Output: 42
console.log(parseInt("3.14")); // Output: 3
console.log(parseInt("abc123")); // Output: NaN
console.log(parseInt("-42")); // Output: -42
console.log(parseInt("  42")); // Output: 42
```

- `Number()` - Converts to number

  ```js
  Number("5"); // Returns: 5 (number)
  Number("hello"); // Returns: NaN (Not a Number)
  Number("3.14"); // Returns: 3.14 (number)
  Number(true); // Returns: 1 (number)
  Number(false); // Returns: 0 (number)
  ```

  The Number() constructor is used to create a number object. The number object contains a few helpful properties and methods like the isNaN and the toFix method. Here's an example using the Number() constructor with the new keyword:

  ```js
  const myNum = new Number("34");
  console.log(typeof myNum); // "object"
  ```

  When the Number() constructor is called as a function without the new keyword, then the return value will be the primitive number type. Most of the time you will be using the Number() constructor to convert other data types to the number data type. Here's an example of converting a string to a number:

  ```js
  const myNum = Number("100");
  console.log(myNum); // 100

  console.log(typeof myNum); // number

  const num = Number("");
  console.log(num); // 0

  const undefinedNum = Number(undefined);
  const nullNum = Number(null);

  console.log(undefinedNum); // NaN
  console.log(nullNum); // 0

  const emptyArr = Number([]);
  const arrOneNum = Number([7]);
  const arrMultiNum = Number([7, 36, 12]);
  const arrStr = Number(["str1"]);
  const arrMultiStr = Number(["str1", "str2"]);

  console.log(emptyArr); // 0
  console.log(arrOneNum); // 7
  console.log(arrMultiNum); // NaN
  console.log(arrStr); // NaN
  console.log(arrMultiStr); // NaN

  const obj1 = Number({});
  const obj2 = Number({ 2: 2 });
  const obj3 = Number({ key: "val" });
  const obj4 = Number({ key: true });

  console.log(obj1); // NaN
  console.log(obj2); // NaN
  console.log(obj3); // NaN
  console.log(obj4); // NaN
  ```

- `.toFixed()` - Format number with specific decimals

  ```js
  let num = 3.14159;
  console.log(num.toFixed()); // Output: "3"
  console.log(num.toFixed(2)); // Output: "3.14"
  console.log(num.toFixed(3)); // Output: "3.142"

  let num = 5.678;
  console.log(num.toFixed(1)); // Output: "5.68"

  let price = 19.99;
  let taxRate = 0.08;
  let total = price + price * taxRate;
  console.log("Total: $" + total.toFixed(2)); // Output: "Total: $21.59"
  ```

- (+) unary plus operator converts its operand into a number. If the operand is already a number, it remains unchanged.

  ```js
  const str = "42";
  const strToNum = +str;

  console.log(strToNum); // 42
  console.log(typeof str); // string
  console.log(typeof strToNum); // number
  ```

- (-) unary negation operator negates the value of the operand.

  ```js
  const str = "42";
  const strToNegativeNum = -str;

  console.log(strToNegativeNum); // -42
  console.log(typeof str); // string
  console.log(typeof strToNegativeNum); // number
  ```

- toString() method is a fundamental feature in JavaScript that converts a value to its string representation. It's a method you can use for numbers, booleans, arrays, and objects. One of the most common uses of toString() is to convert a number to its string representation.
  ```js
  const num = 10;
  console.log(num.toString()); // "10"
  ```

This method accepts an optional radix which is a number from 2 to 36. This radix represents the base, such as base 2 for binary or base 8 for octal. If the radix is not specified it defaults to base 10, which is decimal. Here's an example of passing 2 as an argument to the toString() method:

```js
const num = 10;
console.log(num.toString(2)); // "1010"
```

The meaning it's just number system conversion that use in computer. There are 4 option:

- toString(2) - Binary: Base-2 (0,1) with 8 digits
- toString(16) - Hexadecimal: Base-16 (0-9, A-F) with 2 digits
- toString(10) - Decimal: Base-10 (0-9) with values 0-127
- toString(8) - Octal: Base-8 (0-7) with 3 digits

You can also use the toString() method to convert arrays and objects to strings. Arrays have a custom implementation of toString() that converts each element to a string and joins them with commas. Here's an example:

```js
const arr = [1, 2, 3];
console.log(arr.toString()); // "1,2,3"
```

When toString() method is used with objects, the result will not be a stringified version of the object properties.

```js
const person = {
  name: "John",
  age: 30,
  isStudent: true
},

console.log(person.toString()); // "[object Object]"
```

- (Special Case) What happens when you try to do calculations with numbers and strings?

  ```js
  // This only occur when you *Addition* something with a string and number. + does concatenation if ANY operand is a string
  const result = "10" + 5;
  console.log(result); // 105
  console.log(typeof result); // string

  // When you try to perform other arithmetic operations like subtraction, multiplication, or division with a string and number.
  //All other operators (-, *, /, %) convert to numbers
  const subtractionResult = "10" - 5;
  console.log(subtractionResult); // 5
  console.log(typeof subtractionResult); // number

  const multiplicationResult = "10" * 2;
  console.log(multiplicationResult); // 20
  console.log(typeof multiplicationResult); // number

  const divisionResult = "20" / 2;
  console.log(divisionResult); // 10
  console.log(typeof divisionResult); // number

  //But what if the string doesn't look like a number?

  const subtractionResult = "abc" - 5;
  console.log(subtractionResult); // NaN
  console.log(typeof subtractionResult); // number

  const multiplicationResult = "abc" * 2;
  console.log(multiplicationResult); // NaN
  console.log(typeof multiplicationResult); // number

  const divisionResult = "abc" / 2;
  console.log(divisionResult); // NaN
  console.log(typeof divisionResult); // number

  // (Special Case)
  true + true; // 2 (true = 1)
  false * 5; // 0 (false = 0)
  null + 5; // 5 (null = 0)
  undefined + 5; // NaN
  null == undefined; // true (Special Rule)
  NaN == NaN; // false (Always!)
  ```

- (Special Case) Well-known quirk in JavaScript when it comes to (null)

  ```js
  //This is because null is an object in JavaScript.
  let exampleVariable = null;
  console.log(typeof exampleVariable); // "object" where data should be type string not object
  ```

  - (Special Case) How do comparisons work with null and undefined data types?

  ```js
  /* JavaScript, null and undefined are two distinct data types that represent the absence of a value, but they behave differently in comparisons. Understanding how these types interact in various comparison scenarios is crucial for writing robust and bug-free code.*/

  console.log(null == undefined); // true
  console.log(null === undefined); // false
  console.log(null == 0); // false
  console.log(null == ""); // false
  console.log(undefined == 0); // false
  console.log(undefined == ""); // false
  console.log(null > 0); // false
  console.log(null == 0); // false
  console.log(null >= 0); // true
  console.log(undefined > 0); // false
  console.log(undefined < 0); // false
  console.log(undefined == 0); // false

  /* Given these nuances, it's generally recommended to use the strict equality operator when comparing values, especially when dealing with null and undefined. This approach helps avoid unexpected type coercion and makes your code's behavior more predictable.
  
  In summary, while null and undefined are both used to represent the absence of a value, they behave differently in comparisons. Understanding these differences is key to 
  writing clear and error-free JavaScript code.*/
  ```

## `Math` Operations

In JavaScript, mathematical operations are handled by the built-in `Math` object, which provides a collection of properties and methods for numerical calculations.

You don’t need to import anything — the `Math` object is available globally.

Common Methods

```js
console.log(Math.sqrt(25)); // 5  → square root
console.log(Math.pow(2, 3)); // 8  → power (2³)
console.log(Math.floor(3.7)); // 3  → round down
console.log(Math.ceil(3.7)); // 4  → round up
console.log(Math.abs(-9)); // 9  → absolute value
console.log(Math.trunc(4.9)); // 4  → remove decimal part
console.log(Math.round(3.5)); // 4  → round to nearest integer
console.log(Math.log10(100)); // 2  → base-10 logarithm
console.log(Math.log(100)); // 4.605... → natural log (base e)
console.log(Math.max(1, 5, 9)); // 9  → highest value
console.log(Math.min(1, 5, 9)); // 1  → lowest value
```

Common Constants

```js
console.log(Math.PI); // 3.141592653589793
console.log(Math.E); // 2.718281828459045
console.log(Math.SQRT2); // 1.4142135623730951
console.log(Math.LN10); // 2.302585092994046
console.log(Math.LOG10E); // 0.4342944819032518
```

Random and Advanced Functions

```js
console.log(Math.random()); // Random number between 0 and 1
console.log(Math.sin(Math.PI)); // 0  → sine
console.log(Math.cos(Math.PI)); // -1 → cosine
console.log(Math.tan(Math.PI)); // ~0 → tangent
console.log(Math.sqrt(49)); // 7
console.log(Math.hypot(3, 4)); // 5  → Pythagorean theorem √(3² + 4²)
```

Example Usage

```js
const radius = 5;
const area = Math.PI * Math.pow(radius, 2);
console.log("Circle area:", area); // Circle area: 78.53981633974483
```

## JSON

Stands for JavaScript Object Notation. It is a lightweight data-interchange format for storing and transporting data. It is a lightweight data-interchange format that is easy to read and write, and it is easy to parse and generate. Here's an example of a JSON object:

```js
{
  "name": "Alice",
  "age": 30,
  "isStudent": false,
  "list of courses": ["Mathematics", "Physics", "Computer Science"]
}

```

To access data from a JSON object, you can either use dot or bracket notation.
In this example, we are using dot notation to access the age from the JSON object:

```js
import data from "./example.json" with { type: "json" };
console.log(data.age);

import data from "./example.json" with { type: "json" };
console.log(data["list of courses"]);
```

Converting between JSON and JavaScript objects:

- **JSON.stringify()** - Converts JS objects to JSON strings

This is useful when you want to store or transmit data in a format that can be easily shared or
transferred between systems.

```js
const user = {
  name: "John",
  age: 30,
  isAdmin: true,
};

const jsonString = JSON.stringify(user);
console.log(jsonString);

// Output:
('{"name":"John","age":30,"isAdmin":true}');
```

The JSON.stringify() method also accepts an optional parameter called a replacer, which can
be a function or an array.

```js
const developerObj = {
firstName: "Jessica",
isAwesome: true,
isMusician: true,
country: "USA",
};

console.log(JSON.stringify(developerObj, ["firstName", "country"]));
// Result below:
{"firstName":"Jessica","country":"USA"}

//In this example, we have a developerObj with four properties. When we use the JSON.stringify() method, we can pass in an array for the second parameter and specify which properties we want stringified. The result will be a stringified object containing only the firstName and country properties.
```

Another optional parameter for the JSON.stringify() method would be the spacer parameter.
This allows you to control the spacing for the stringified result:

```js
const developerObj = {
	firstName: "Jessica",
	isAwesome: true,
	isMusician: true,
	country: "USA",
};
console.log(JSON.stringify(developerObj, null, 2));

// Result below:
{
  "firstName": "Jessica",
  "isAwesome": true,
  "isMusician": true,
  "country": "USA"
}

// Most of the time you will not be using either of these optional parameters for the JSON.stringify() method but it is still helpful to be aware of them. JSON.stringify(value, replacer, space)
```

- **JSON.parse()** - Converts JSON strings to JS objects

This is useful when you retrieve JSON data from a web server or from localStorage and
you need to manipulate the data in your application.

```js
const jsonString = '{"name":"John","age":30,"isAdmin":true}';
const userObject = JSON.parse(jsonString);

Result below:
{
name: "John",
age: 30,
isAdmin: true
}

//This allows you to work with the data in your program as a normal JavaScript object, making it easier to manipulate and use.
```

# Operator

## Arithmetic Operators

Used for mathematical calculations:

- (+) (Addition): Adds numbers or concatenates strings

  ```js
  let sum = 5 + 3; // 8
  let text = "Hello" + " World"; // "Hello World"
  ```

- (-) (Subtraction): Subtracts numbers

  ```js
  let difference = 10 - 5; // 5
  ```

- (\*) (Multiplication): Multiplies numbers

  ```js
  let product = 4 * 3; // 12
  ```

- (/) (Division): Divides numbers

  ```js
  let quotient = 15 / 3; // 5
  ```

- (%) (Modulus): Returns the division remainder

  ```js
  let remainder = 10 % 3; // 1
  ```

- \*\* (Exponentiation): is right-to-left associative/precedence. Same as x^2 or x² in mathematical notation.

  ```js
  const result = 2 ** (3 ** 2);
  console.log(result); // 512

  /*Evaluates 3 ** 2, which equals 9, then, it evaluates 2 ** 9, which equals 512. 
  If the exponent operator had left-to-right associativity, 
  would have calculated 2 ** 3 first to get 8, then 8 ** 2 to get 64*/
  ```

- (++) Increment and (--) Decrements operators (It was for main loop function)

  Dev choose "i" as the loop variable recognized by every programmer, stands for "index" or "iterator"

  Increment Operator (++) - Increments the value of the variable by 1.

  Excrement Operator (--) - Decrements the value of the variable by 1.

  ```
  What they do:
      ++ = add 1
      -- = subtract 1
  Two ways to write them:
  (x++, x--)
      Returns the current value
      Then changes the variable
  (++x, --x)
      Changes the variable first
      Then returns the new value
  ```

  ```js
  // Example below: (Read Below Note First!!)
  let x = 5;  console.log(x++ *2);
      x = 5;  console.log(++x *2);
      x = 5;  console.log(x-- *2);
      x = 5;  console.log(--x *2);

  /*Explanation:
  You still have to declare x=5 after the first one, it's there
  because to reset it, if not the answer will be related to the first statement.)
  First Statement Explain
  ++ is after X. So the X value is still 5 and next time it will be 6
  Second Statement Explain
  ++ is before X. So the X value will be 6 and next time it will be 7
  Third Statement Explain
  -- is after X. S. So the X value is still 5 and next time it will be 4
  Forth Statement Explain
  -- is before X. So the X value will be 4 and next time it will be 3*/

  // Result below: (Reset condition or Not reset condition)
  10
  12 or 14
  10 or 14
  8 or 10
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

  ```js
  let x = 10;
  ```

- (+=) Addition assignment

  ```js
  let y = 5;
  y += 3; // Same as y = y + 3 (y becomes 8)
  ```

- (-=) Subtraction assignment

  ```js
  let z = 10;
  z -= 4; // Same as z = z - 4 (z becomes 6)
  ```

- (\*=) Multiplication assignment

  ```js
  let a = 3;
  a *= 2; // Same as a = a * 2 (a becomes 6)
  ```

- (/=) Division assignment

  ```js
  let b = 8;
  b /= 2; // Same as b = b / 2 (b becomes 4)
  ```

- (%=) Modulus assignment
  ```js
  let c = 7;
  c %= 2; // Same as c = c % 2 (c becomes 1)
  ```

## Comparison Operators

Used to compare values:

- (==) Loose equality: It does check type but more emphasis on the value, so it performs type coercion, converting values to the same type before comparing them.

  ```js
  5 == "5"; // true (string is converted to number)
  ```

- (===) Strict equality: It checks both value and type, providing more precise, strict, predictable results.

  ```js
  5 === "5"; // false (different types)
  ```

  ```js
  console.log("5" == 5); // true

  /*Step 1: Types differ (string vs num ber)
  Step 2: Convert string '5' to number 5  
  Step 3: Compare 5 == 5
  Step 4: Result is true (they're equal after conversion)*/

  console.log("5" === 5); // false

  /*Step 1: Types differ (string vs number)
  Step 2: Return false immediately (different types = not equal)*/
  ```

- (!=) Loose inequality: It does check type but more emphasis on the value, so it performs type coercion, converting values to the same type before comparing them.

  ```js
  5 != "6"; // true
  ```

- (!==) Strict inequality: It checks both value and type, providing more precise, strict, predictable results.

  ```js
  5 !== "5"; // true (different types)
  ```

  ```js
  console.log("5" != 5); // false

  /*Step 1: Types differ (string vs number)
  Step 2: Convert string '5' to number 5  
  Step 3: Compare 5 != 5
  Step 4: Result is false (they're equal after conversion)*/

  console.log("5" !== 5); // true

  /*Step 1: Types differ (string vs number)
  Step 2: Return true immediately (different types = not equal)*/
  ```

- (>) (Greater than): Checks if left value is greater

  ```js
  10 > 5; // true
  ```

- (<) (Less than): Checks if left value is smaller

  ```js
  5 < 10; // true
  ```

- (>=) (Greater than or equal): Checks if left value is greater or equal

  ```js
  5 >= 5; // true
  ```

- (<=) (Less than or equal): Checks if left value is smaller or equal
  ```js
  5 <= 10; // true
  ```

## Logical Operators

Used to determine logic between variables or values:

- (&&) AND: Returns true if both operands are true

  ```js
  true && true; // true
  true && false; // false
  ```

  ```js
  const result = true && 'hello';
  console.log(result); // hello

  const result = 0 && 3;
  console.log(result); // 0
  // (Since 0 is a falsy value, the number 0 is logged to the console.)

  const result = false && 0;
  console.log(result); // false
  // (Since false is a falsy value, then false is logged to the console.)

  if (2 < 3 && 3 < 4) {
  console.log('The if block runs');
  } else {
  console.log('The else block runs');
  }

  // Result:
  The if block runs
  ```

- (||) OR: Returns true if at least one operand is true

  ```js
  true || false; // true
  false || false; // false
  ```

  ```js
  const result = 'This is truthy' || false;
  console.log(result); // This is truthy

  const result = 0 || 'This is truthy';
  console.log(result); // This is truthy

  let userInput;
  if (userInput || 'Guest') {
  console.log('A user is present');
  } else {
  console.log('No user detected');
  }

  // Result:
  A user is present

  // (Because userInput have no value)
  ```

- (!) NOT: Reverses the boolean result

  ```js
  !true; // false
  !false; // true
  ```

  ```js
  // Basic boolean negation
  console.log(!true); // false
  console.log(!false); // true

  // The NOT operator converts non-boolean values to boolean first, then negates
  console.log(!"Hello"); // false (string is truthy, so !truthy becomes false)
  console.log(!""); // true (empty string is falsy, so !falsy becomes true)

  // Useful for checking empty values
  const username = "";
  if (!username) {
    console.log("Username is required!"); // This will execute
  }

  // Double negation (!!) can be used to convert a value to boolean
  console.log(!!0); // false
  console.log(!!"text"); // true
  console.log(!!null); // false
  console.log(!!undefined); // false

  // Using NOT in conditions
  const isLoggedIn = false;
  if (!isLoggedIn) {
    console.log("Please log in first!"); // This will execute
  }
  ```

## Other Important Operators

- **Ternary operator (?:)**: Shorthand for if-else statements ? expression if true : expression if false

  ```js
  let status = age >= 18 ? "Adult" : "Minor";
  ```

  ```js
  const isLoggedIn = true;
  const msg = isLoggedIn ? "Welcome back!" : "Please log in.";
  console.log(msg); // Welcome back!

  const weather = temperature > 25 ? "sunny" : "cool";
  console.log(`It's a ${weather} day!`); // It's a sunny day!

  let fortune1 = "Your cat will look very cuddly today.";
  let fortune2 = "The weather will be nice tomorrow.";
  let fortune3 = "Be cautious of your new neighbors.";
  let fortune4 = "You will find a new hobby soon.";
  let fortune5 = "It would be wise to avoid the color red today.";
  let min = 1;
  let max = 5;
  let randomNumber = Math.round(Math.random() * (max - min) + min);
  let selectedFortune =
    randomNumber == 1
      ? fortune1
      : randomNumber == 2
      ? fortune2
      : randomNumber == 3
      ? fortune3
      : randomNumber == 4
      ? fortune4
      : fortune5;

  console.log(selectedFortune);
  ```

- **?.** (Optional chaining): Safely access nested properties or call methods without worrying wether they exist. It’s like a safety net for working with objects that might have missing parts.

  ```js
  user.profile?.address?.street; // Returns undefined if any property in chain is null/undefined
  ```

  ```js
  const user = {
    name: "John",
    profile: {
      email: "john@example.com",
      address: {
        street: "123 Main St",
        city: "Somewhere",
      },
    },
  };
  console.log(user.profile?.address?.street); // "123 Main St"
  console.log(user.profile?.phone?.number); // undefined

  /*By using the optional chaining operator, we are telling JavaScript to only continue with the operation if the object (or the value before the ?.) exists and is not null or undefined. If the value before the ?. is null or undefined, JavaScript returns undefined rather than attempting to proceed with the operation and throwing an error.*/
  ```

- **??** (Nullish coalescing): Return a value only if the first one is null or undefined.

  ```js
  let username = null ?? "Anonymous"; // "Anonymous"
  ```

  ```js
  const result = null ?? "default";
  console.log(result); // default

  const userSettings = {
    theme: null,
    volume: 0,
    notifications: false,
  };

  let theme = userSettings.theme ?? "light";
  console.log(theme); // light
  ```

- **...** (Spread): Expands an iterable (like an array or string) into individual elements.

  ```js
  let newArray = [...oldArray, newItem];
  ```

  ```js
  let originalArray = [1, 2, 3];
  let copyArray = [...originalArray];

  console.log(copyArray); // [1, 2, 3]
  console.log(copyArray === originalArray); // false
  ```

- Bitwise Operators (&, |, ^, ~, <<, >>)

  (&) bitwise AND operator returns a 1 in each bit position for which the corresponding bits of both operands are 1.

  ```js
  let a = 5; // Binary: 101
  let b = 3; // Binary: 011
  console.log(a & b); // Output: 1 (Binary: 001)
  ```

  (|) bitwise OR operator returns a 1 in each bit position for which the corresponding bits of either or both operands are 1.

  ```js
  let a = 5; // Binary: 101
  let b = 3; // Binary: 011
  console.log(a | b); // Output: 7 (Binary: 111)
  ```

  (^) bitwise XOR operator returns a 1 in each bit position for which the corresponding bits of either, but not both, operands are 1.

  ```js
  let a = 5; // Binary: 101
  let b = 3; // Binary: 011
  console.log(a ^ b); // Output: 6 (Binary: 110)
  ```

  (~) bitwise NOT operator inverts all the bits of its operand.

  ```js
  let a = 5; // Binary: 101
  console.log(~a); // Output: -6
  ```

  (<<) left shift operator shifts all bits to the left by a specified number of positions.

  ```js
  let a = 5; // Binary: 101
  console.log(a << 1); // Output: 10 (Binary: 1010)
  ```

  (>>) right shift operator shifts all bits to the right.

  ```js
  let a = 5; // Binary: 101
  console.log(a >> 1); // Output: 2 (Binary: 10)
  ```

- Unary operators (+, -, !, ~, void, typeof)
  Act on a single operand to perform operations like type conversion, value manipulation, or checking certain conditions.

  (+) unary plus operator converts its operand into a number.
  If the operand is already a number, it remains unchanged.

  ```js
  const str = "42";
  const strToNum = +str;

  console.log(strToNum); // 42
  console.log(typeof str); // string
  console.log(typeof strToNum); // number
  ```

  (-) unary negation operator negates the value of the operand.

  ```js
  const str = "42";
  const strToNegativeNum = -str;

  console.log(strToNegativeNum); // -42
  console.log(typeof str); // string
  console.log(typeof strToNegativeNum); // number
  ```

  (!) unary logical NOT operator flips the boolean value of its operand

  ```js
  let isOnline = true;
  console.log(!isOnline); // false

  let isOffline = false;
  console.log(!isOffline); // true
  ```

  (~) bitwise NOT operator inverts the binary representation of a number

  ```js
  const num = 5; // The binary for 5 is 00000101 becomes 11111010 which total is 6
  console.log(~num); // -6
  ```

  (void) unary operator that evaluates an expression and returns undefined.

  ```js
  const result = void (2 + 2);
  console.log(result); // undefined

  <a href="javascript:void(0);">Click Me</a>; // commonly used in hyperlinks HTML
  ```

  (typeof) is used to determine the type of a variable.

  ```js
  let num = 42;
  console.log(typeof num); // "number"
  ```

# Objects & Arrays

## Braces Literal Syntax

```js
Curly Braces {}         - Objects & Code Blocks
    Objects             : { name: "John", age: 25 }
    Code blocks         : if (condition) { ... }
    Function bodies     : function() { return "hello"; }
    Destructuring       : const { name } = person
```

```js
Square Brackets []      - Arrays & Property Access
    Arrays              : [1, 2, 3, "hello"]
    Array access        : array[0]
    Dynamic properties  : object[variableName]
    Computed properties : { [key]: value }
```

```js
Parentheses ()          - Functions & Grouping
    Function calls      : myFunction()
    Parameters          : function(a, b) { }
    Grouping            : (2 + 3) * 4
    Conditions          : if (x > 5)
```

```js
Memory Tips:
{} = "Container for properties" (objects) or "group statements" (blocks)
[] = "List of items" (arrays) or "get item by position/key"
() = "Execute this" (functions) or "do this first" (grouping)
```

```js
// (Special Case) Bracket notation
let greeting = "hello";
console.log(greeting[1]); // Output: "e"
console.log(greeting[greeting.length - 1]); // Output:
```

## **Comparative Syntax Table — `{}`, `[]`, `()`**

| Symbol        | Python                                                      | JavaScript                                                      | C / Java / C++                                                    | Meaning Summary                                               |
| :------------ | :---------------------------------------------------------- | :-------------------------------------------------------------- | :---------------------------------------------------------------- | :------------------------------------------------------------ |
| `{}`          | **Dictionary** (key–value pairs) or **Set** (unique values) | **Object literal** (key–value pairs)                            | **Code block** (not data; defines scope in functions, loops, ifs) | Represents **mapping or grouping** of related items           |
| Example       | `{"name": "Alice", "age": 25}`<br>`{1, 2, 3}`               | `{ name: "Alice", age: 25 }`                                    | `{ printf("Hi"); }`                                               | Python/JS: data container<br>C/Java: block of executable code |
| Mutable?      | ✅ **Mutable** (dict, set can be changed)                   | ✅ **Mutable** (object properties can change)                   | N/A (not data)                                                    | Mapping containers usually mutable                            |
| Ordered?      | ✅ **Yes** (since Python 3.7)                               | 🚫 **No guaranteed order before ES2015**, now insertion-ordered | N/A                                                               | Usually _insertion-ordered_ in modern langs                   |
| Keys / Values | Dict: key–value<br>Set: unique values only                  | Object: key–value                                               | Code only                                                         | Represents data associations                                  |

| Symbol       | Python                                | JavaScript                            | C / Java / C++                           | Meaning Summary                           |
| :----------- | :------------------------------------ | :------------------------------------ | :--------------------------------------- | :---------------------------------------- |
| `[]`         | **List** (ordered, mutable sequence)  | **Array** (ordered, mutable sequence) | **Array indexing or declaration**        | Represents **sequential collections**     |
| Example      | `[1, 2, 3]`                           | `[1, 2, 3]`                           | `int nums[3] = {1, 2, 3};`               | Indexed sequence of values                |
| Mutable?     | ✅ **Mutable**                        | ✅ **Mutable**                        | ✅ **Mutable** (fixed-size, static type) | Usually mutable but differs by language   |
| Ordered?     | ✅ **Yes**                            | ✅ **Yes**                            | ✅ **Yes**                               | Ordered, index-based                      |
| Mixed Types? | ✅ Allowed (e.g., `[1, "two", True]`) | ✅ Allowed (e.g., `[1, "two", true]`) | 🚫 Usually not (fixed type per array)    | JS/Python flexible; C/Java strongly typed |
| Use Case     | Storing sequences of elements         | Storing sequences                     | Declaring fixed arrays                   | Sequential collection of data             |

| Symbol        | Python                                                                       | JavaScript                                   | C / Java / C++                               | Meaning Summary                                        |
| :------------ | :--------------------------------------------------------------------------- | :------------------------------------------- | :------------------------------------------- | :----------------------------------------------------- |
| `()`          | **Tuple** (ordered, immutable sequence)<br>**Function call**<br>**Grouping** | **Function call** or **Expression grouping** | **Function call** or **Grouping expression** | Represents **order, grouping, or function invocation** |
| Example       | `(1, 2, 3)`<br>`print("Hi")`                                                 | `(a + b)` or `sum(1, 2)`                     | `printf("Hi");`                              | Used for grouping or calling functions                 |
| Mutable?      | 🚫 **Immutable** (tuples can’t be changed)                                   | N/A (not a container)                        | N/A                                          | Immutable or not a container                           |
| Ordered?      | ✅ **Yes**                                                                   | N/A                                          | N/A                                          | Preserves order if data container                      |
| Special Notes | `(value,)` is 1-tuple; `()` empty tuple                                      | No tuple type; use arrays or objects         | Only grouping or function parentheses        | Tuple is unique to Python                              |
| Use Case      | Immutable data grouping                                                      | Function calls                               | Function calls                               | Control precedence or encapsulate values               |

🧠 Summary Insights

| Concept                  | Python                                                  | JavaScript                       | C/Java-family                    |     |
| :----------------------- | :------------------------------------------------------ | :------------------------------- | :------------------------------- | --- |
| **{} curly braces**      | Create _dict_ or _set_ (data)                           | Create _object_ (data)           | Create _block_ (code)            |     |
| **[] square brackets**   | Create _list_ (data)                                    | Create _array_ (data)            | Access or define array (data)    |     |
| **() parentheses**       | Create _tuple_ (data), call function, group expressions | Call function, group expressions | Call function, group expressions |     |
| **Data vs Code meaning** | Mostly **data creation**                                | Mostly **data creation**         | Mostly **code control**          |     |
| **Mutability**           | dict ✅ list ✅ tuple 🚫                                | object ✅ array ✅               | arrays fixed type / size         |

🧩 Visual Analogy

| Concept         | Python                       | JavaScript                     | C / Java                          |
| :-------------- | :--------------------------- | :----------------------------- | :-------------------------------- |
| Mapping         | 📦 `{key: value}` (dict/set) | 🗂️ `{key: value}` (object)     | ⚙️ `{}` defines code, not mapping |
| Sequence        | 📚 `[item1, item2]` (list)   | 📜 `[item1, item2]` (array)    | 🧮 `int arr[] = {1,2}`            |
| Grouping / Call | 🎯 `(a, b)` (tuple or call)  | 🔔 `(a, b)` (call or grouping) | 🔔 `(a, b)` (call or grouping)    |

## String Manipulation

- String Length and Indexing

  To get the length of a string, use the `.length` property:

  ```js
  let str = "Hello world";
  console.log(str.length); // 11
  ```

  Indexing lets you access individual characters in a string using square brackets `[]`.

  ```js
  let str = "Hello world";

  console.log(str[0]); // "H"
  console.log(str[6]); // "w"
  ```

  Negative indexing is not supported in JavaScript,
  but you can get the last character using `.length - 1`:

  ```js
  let str = "Hello world";
  console.log(str[str.length - 1]); // "d"
  console.log(str[str.length - 2]); // "l"
  ```

- Nested Arrays and Element Access

  Arrays can store other arrays or mixed data types.
  To access nested elements, chain indices:

  ```js
  let developer = ["Alice", 25, ["Python", "Rust", "C++"]];
  console.log(developer[2]); // ["Python", "Rust", "C++"]
  console.log(developer[2][1]); // "Rust"
  ```

- Destructuring (Unpacking)

  Destructuring allows unpacking array elements into individual variables.

  ```js
  let developer = ["Alice", 34, "Rust Developer"];
  let [name, age, job] = developer;

  console.log(name); // "Alice"
  console.log(age); // 34
  console.log(job); // "Rust Developer"
  ```

  You can also use the rest operator (`...`) to collect remaining elements:

  ```js
  let developer = ["Alice", 34, "Rust Developer"];
  let [name, ...rest] = developer;

  console.log(name); // "Alice"
  console.log(rest); // [34, "Rust Developer"]
  ```

- String Slicing and Substrings

  To extract parts of a string, use `.slice(start, end)` — where `end` is exclusive (not included).

  ```js
  let str = "Hello world";
  console.log(str.slice(1, 4)); // "ell"
  ```

  You can omit start or end to slice from the beginning or to the end:

  ```js
  let str = "Hello world";

  console.log(str.slice(0, 7)); // "Hello w"
  console.log(str.slice(8)); // "rld"
  console.log(str.slice()); // "Hello world"
  ```

  You can also use a negative index to count from the end:

  ```js
  let str = "Hello world";
  console.log(str.slice(-3)); // "rld"
  ```

- Step Slicing (Not Native, But Simulatable)

  JavaScript does not have a built-in “step” slicing like Python’s [`::2`],
  but you can emulate it using `.split("")`, `.filter()`, and `.join()`:

  ```js
  let str = "Hello world";
  let stepped = str
    .split("")
    .filter((_, i) => i % 2 === 0)
    .join("");
  console.log(stepped); // "Hlowrd"
  ```

  To reverse a string:

  ```js
  let str = "Hello world";
  console.log(str.split("").reverse().join("")); // "dlrow olleH"
  ```

- Membership Test (`in` → `.includes()`)

  Use `.includes()` to check if a substring exists:

  ```js
  let str = "Hello world";

  console.log(str.includes("Hello")); // true
  console.log(str.includes("hey")); // false
  console.log(str.includes("e")); // true
  console.log(str.includes("f")); // false
  ```

## Object Manipulation Structure Levels

Accessing nested object data:

```js
const person = {
  name: "Alice",
  age: 30,
  contact: {
    email: "alice@example.com",
    phone: {
      home: "123-456-7890",
      work: "098-765-4321",
    },
  },
};

console.log(person.name); // Alice
console.log(person["age"]); // 30
console.log(person.contact.phone.work); // "098-765-4321"
```

Object property operations:

- Add properties: `person.job = "Engineer"` or `person["hobby"] = "Knitting"`

  ```js
  person.job = "Engineer";
  person["hobby"] = "Knitting";
  console.log(person);
  // {name: 'Alice', age: 30, job: 'Engineer', hobby: 'Knitting'}
  ```

- Delete properties: `delete person.job`

  ```js
  delete person.job;
  console.log(person.job); // undefined
  ```

- Check if property exists: `"name" in person`

  ```js
  console.log("name" in person); // true
  ```

- Checks if an object has a specific property: `.hasOwnProperty()`

  ```js
  const person = {
    name: "Alice",
    age: 30,
  };

  console.log(person.hasOwnProperty("name")); // true
  console.log(person.hasOwnProperty("job")); // false
  ```

- Check if an object has a specific property as its own property, it's directly defined on the object and not inherited from its prototype chain.
  **Why `Object.hasOwn()` is preferred over `Object.prototype.hasOwnProperty()`:**
  **Handles objects created with `Object.create(null)`:** `hasOwnProperty()` fails on objects created with `Object.create(null)` because they do not inherit from `Object.prototype`, and therefore, `hasOwnProperty` is not available on them. `Object.hasOwn()` works correctly in this scenario.

  ```js
  const obj1 = { a: 1 };
  console.log(Object.hasOwn(obj1, "a")); // true
  console.log(Object.hasOwn(obj1, "b")); // false

  const obj2 = Object.create(null);
  obj2.c = 3;
  console.log(Object.hasOwn(obj2, "c")); // true
  // console.log(obj2.hasOwnProperty('c')); // Throws an error
  ```

### Natural Hierarchical Structure Levels in Different Variable Declarations {Classification}

Single level, no structure.

```js
const name = "John"; // Single level, no structure
let age = 25; // Single level, no structure
var score = 100; // Single level, no structure
```

It doesn't matter how you call the identifier or classification as long as clear on structure.

```js
const recordCollection = {
  // This is main (records) object
  5439: {
    // This is a key (id) in the main object
    albumTitle: "ABBA Gold", // (props) of the id object and "(value)" within
    artist: "", // (props) of the id object and "(value)" within
    tracks: [], // (props) of the id object and "(value)" within
  },
};

function updateRecords(records, id, prop, value) {
  if (!records[id]) {
    return records;
  }
  if (value === "") {
    delete records[id][prop];
  } else records[id][prop] = value;
  return records;
}

console.log(updateRecords(recordCollection, 5439, "artist", "ABBA"));
//                         ^records          ^id    ^prop     ^value
```

Example of well-identified object structure

```js
const students = {
  STU_001: {
    // Identifier with clear prefix
    name: "John", // Property with string value
    grades: [90, 85], // Property with array value
    active: true, // Property with boolean value
  },
};
```

Numeric identifier style

```js
const records = {
  2548: {
    // Numeric identifier
    albumTitle: "...", // String property
    tracks: [], // Array property
  },
};
```

More explicit classification

```js
const inventory = {
  itemId: {
    // Named identifier
    type: "product", // Classification property
    metadata: {
      // Nested classification
      category: "electronics",
      subCategory: "phones",
    },
  },
};
```

E-commerce System

```js
const ecommerceSystem = {
  STORE_001: {
    // Level 1: Store ID
    details: {
      // Level 2: Store Details
      name: "Main Branch",
      location: {
        // Level 3: Location Details
        street: "123 Main St",
        city: "Boston",
        zip: "02108",
      },
    },
    inventory: {
      // Level 2: Inventory
      products: [
        // Level 3: Product List
        {
          // Level 4: Product Details
          id: "P001",
          name: "Laptop",
          specs: {
            // Level 5: Product Specifications
            brand: "Dell",
            model: "XPS",
          },
        },
      ],
    },
  },
};
```

School Management System

```js
const schoolSystem = {
  departments: {
    // Level 1: Department Structure
    DEPT_001: {
      // Level 2: Department ID
      name: "Computer Science",
      courses: {
        // Level 3: Course Structure
        CS101: {
          // Level 4: Course Details
          title: "Intro to Programming",
          students: [
            // Level 5: Student List
            {
              // Level 6: Student Details
              id: "STU_001",
              grades: {
                midterm: 95,
                final: 88,
              },
            },
          ],
        },
      },
    },
  },
};
```

File System Structure

```js
const fileSystem = {
  root: {
    // Level 1: Root Directory
    documents: {
      // Level 2: Subdirectory
      work: {
        // Level 3: Nested Directory
        files: [
          // Level 4: File List
          {
            // Level 5: File Details
            name: "report.doc",
            metadata: {
              size: "1.2MB",
              created: "2023-01-01",
              type: "document",
            },
          },
        ],
      },
    },
  },
};
```

Optional chaining operator (?.) for safe property access:

The optional chaining operator (?.) is a useful tool in JavaScript that lets you safely access
object properties or call methods without worrying whether they exist. It's like a safety net for
working with objects that might have missing parts.

```js
const user = {
  name: "John",
  profile: {
    email: "john@example.com",
    address: {
      street: "123 Main St",
      city: "Somewhere",
    },
  },
};
console.log(user.profile?.address?.street); // "123 Main St"
console.log(user.profile?.phone?.number); // undefined

// By using the optional chaining operator, we are telling JavaScript to only continue with the operation if the object (or the value before the ?.) exists and is not null or undefined.If the value before the ?. is null or undefined, JavaScript returns undefined rather than attempting to proceed with the operation and throwing an error.
```

### Object Constructors

New keyword (Object Constructor)

Definition: In JavaScript, a constructor is a special type of function used to create and initialize objects. It is invoked with the new keyword and can initialize properties and methods on the newly created object. The Object() constructor creates a new empty object.

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}

const person1 = new Person("John", 30);
console.log(person1); // Person { name: "John", age: 30 }
```

Object() - Object Constructor

The Object() constructor can be used with or without the new keyword.
When called as a function without new, it behaves differently depending on the type of
value passed to it.

```js
const num = 42;
const numObj = Object(num); // Creates an object wrapper for the number
console.log(numObj); // 42
console.log(typeof numObj); // "object"

//first console.log will show 42, but it is important to note that this is not a regular number. As you can see in the second console.log, numObj is an object. This is happening because we used the Object() constructor to turn that input of a number into an object.
```

What happens if we try to pass null or undefined to the Object() constructor?

```js
const newObj = new Object(undefined);
console.log(newObj); // {}
```

Well, the result will be an empty object. Another use case for the Object() constructor is
when you're working with a value of unknown type and you need to ensure it's an object.

```js
function toObject(value) {
  if (value === null || value === undefined) {
    return {};
  }
  if (typeof value === "object") {
    return value;
  }
  return Object(value);
}

console.log(toObject(null)); // {}
console.log(toObject(true)); // {}
console.log(toObject([1, 2, 3])); // [1, 2, 3]

//In this example, we have a function called toObject. The second condition will check if the value is a type of object and will return the value if the condition is true. This condition will check for objects as well as arrays since arrays are special types of objects.If neither of the conditions is true, the function returns Object(value), which converts the input into an object. This works for values like numbers, strings, and booleans
```

Most of the time you will not be using the Object() constructor to create new objects because
you will be using object literal syntax instead (e.g., const objectLiteral = { name: "Beau" }).
But it is still good to understand the basics of working with the Object constructor.

Object destructuring:

Definition: Object destructuring allows you to extract values from objects and assign them to
variables in a more concise and readable way.

```js
const person = { name: "Alice", age: 30, city: "New York" };
const { name, age } = person;

console.log(name); // Alice
console.log(age); // 30
```

## Array Constructors

Definition
The Array() constructor creates JavaScript array objects. It can:
Initialize an empty array (no arguments).
Create an array of a specific length (single numeric argument).
Initialize with given elements (multiple arguments).

```js
new Array()             // Empty array
new Array(size)         // Array of given length (empty slots)
new Array(e1, e2, ...)  // Array with elements
```

```js
const arr1 = new Array();
console.log(arr1); // [] (length = 0)

const arr2 = new Array(3);
console.log(arr2); // [ <3 empty slots> ] (length = 3)

const arr3 = new Array("a", 2, true);
console.log(arr3); // ["a", 2, true] (length = 3)
```

When to Use Array() Constructor?

- Pre-allocate memory for large arrays (performance optimization):

  ```js
  const bigArray = new Array(1000); // 1000 empty slots
  ```

- Rare edge cases where array length matters more than content.

Best Practice
✅ Use array literals [] 99% of the time:

```js
// Preferred
const arr = [1, 2, 3];
```

❌ Avoid new Array() unless you need sparse arrays:

```js
// Problematic
const badArr = new Array(1, 2, 3); // Works but confusing
```

Special Case: Single Numeric Argument

```js
console.log(new Array(3)); // [empty × 3] (length=3)
console.log(new Array("3")); // ["3"] (length=1)

/*If the only argument is a number, it sets the length.
Otherwise, treats arguments as elements.*/
```

Summary

- new Array(): Creates arrays flexibly but can be tricky.
- Literal []: Simpler, safer, and more readable.
- Sparse arrays: Useful for memory pre-allocation but behave unexpectedly in methods like map().

Use the constructor only when you specifically need its unique behavior. Otherwise, stick with []. 🚀

## Array Methods

**Finding Elements**

- **indexOf()** - Returns the first index of an element in the array

  ```js
  const fruits = ["apple", "banana", "orange", "apple"];
  console.log(fruits.indexOf("apple")); // Output: 0
  console.log(fruits.indexOf("mango")); // Output: -1

  // The first call returns 0 (first position), and the second returns -1 (not found).
  ```

- **lastIndexOf()** - Returns the last index of an element

  ```js
  const fruits = ["apple", "banana", "orange", "apple"];
  console.log(fruits.lastIndexOf("apple")); // Output: 3

  // Returns 3 because the last "apple" is at index 3.
  ```

- **find()** - Returns the first element that satisfies a condition

  ```js
  const numbers = [5, 12, 8, 130, 44];
  const found = numbers.find((num) => num > 10);
  console.log(found); // Output: 12

  // Returns 12 as it's the first number greater than 10.
  ```

- **findIndex()** - Returns the index of the first element that satisfies a condition

  ```js
  const numbers = [5, 12, 8, 130, 44];
  const foundIndex = numbers.findIndex((num) => num > 10);
  console.log(foundIndex); // Output: 1

  // Returns 1 because 12 is at index 1 and is the first element greater than 10.
  ```

- **includes()** - Checks if an array includes a certain value

  ```js
  const pets = ["cat", "dog", "bat"];
  console.log(pets.includes("cat")); // Output: true
  console.log(pets.includes("fish")); // Output: false

  // Returns true if element exists, false if not.
  ```

**Transforming Arrays**

- **map()** - Creates a new array with the results of calling a function on every element

  ```js
  const numbers = [1, 4, 9];
  const roots = numbers.map(Math.sqrt);
  console.log(roots); // Output: [1, 2, 3]

  // Returns a new array with the square root of each number.
  ```

- **filter()** - Creates a new array with elements that pass a test

  ```js
  const words = ["spray", "limit", "elite", "exuberant"];
  const result = words.filter((word) => word.length > 5);
  console.log(result); // Output: ["exuberant"]

  // Returns only words with more than 5 characters.
  ```

- **reduce()** - Reduces array to a single value by executing a function

  ```js
  const numbers = [1, 2, 3, 4];
  const sum = numbers.reduce(
    (accumulator, currentValue) => accumulator + currentValue,
    0
  );
  console.log(sum); // Output: 10

  // Adds all numbers together, starting with initial value 0.
  ```

- **sort()** - Sorts elements of an array in place

  ```js
  const fruits = ["banana", "cherry", "apple"];
  fruits.sort();
  console.log(fruits); // Output: ['apple', 'banana', 'cherry']

  // Sorts alphabetically by default.
  ```

- **reverse()** - Reverses the order of elements in an array

  ```js
  const numbers = [1, 2, 3, 4, 5];
  numbers.reverse();
  console.log(numbers); // Output: [5, 4, 3, 2, 1]

  // Reverses the array in place.
  ```

**Combining/Splitting**

- **concat()** - Joins arrays together

  ```js
  const array1 = ["a", "b"];
  const array2 = ["c", "d"];
  const array3 = array1.concat(array2);
  console.log(array3); // Output: ['a', 'b', 'c', 'd']

  // Returns a new array combining both arrays.
  ```

- **slice()** - Returns a shallow copy of a portion of an array

  ```js
  const fruits = ["apple", "banana", "orange", "mango"];
  const citrus = fruits.slice(1, 3);
  console.log(citrus); // Output: ['banana', 'orange']

  // Returns elements from index 1 to 2 (end index is exclusive).
  ```

- **join()** - Joins all elements into a string

  ```js
  const elements = ["Fire", "Water", "Air"];
  console.log(elements.join()); // Output: "Fire,Water,Air"
  console.log(elements.join("-")); // Output: "Fire-Water-Air"

  // Joins with commas by default or with specified separator.
  ```

- **split()** - Splits a string into an array (string method, not array method)

  ```js
  const str = "The quick brown fox";
  const words = str.split(" ");
  console.log(words); // Output: ["The", "quick", "brown", "fox"]

  // Splits the string at each space.
  ```

**Adding/Removing Elements**

Keep in mind that it can be used with however format we want to.

````js
let arr = [];
arr.push([1, 2, 3]);
console.log(arr); // [[1, 2, 3]] <-- an array inside an array

    let inv = [];
    inv.push({ name: "FLOUR", quantity: 5 });
    console.log(inv); // [{ name: "FLOUR", quantity: 5 }]
    ```

- **pop()** - Removes the last element from an array

  ```js
  const plants = ["broccoli", "cauliflower", "kale"];
  const removed = plants.pop();
  console.log(plants); // Output: ['broccoli', 'cauliflower']
  console.log(removed); // Output: 'kale'

  // Removes and returns the last element.
````

- **push()** - Adds elements to the end of an array

  ```js
  const animals = ["pigs", "goats"];
  const count = animals.push("cows");
  console.log(animals); // Output: ['pigs', 'goats', 'cows']
  console.log(count); // Output: 3

  // Returns the new length of the array.
  ```

- **shift()** - Removes the first element from an array

  ```js
  const array = [1, 2, 3];
  const firstElement = array.shift();
  console.log(array); // Output: [2, 3]
  console.log(firstElement); // Output: 1

  // Removes and returns the first element.
  ```

- **unshift()** - Adds elements to the beginning of an array

  ```js
  const array = [4, 5, 6];
  const newLength = array.unshift(1, 2, 3);
  console.log(array); // Output: [1, 2, 3, 4, 5, 6]
  console.log(newLength); // Output: 6

  // Returns the new length of the array.
  ```

- **splice()** - Changes array by removing, replacing, or adding elements

  ```js
  array.splice(startIndex, deleteCount, item1, item2, ...)
  ```

  ```js
  const months = ["Jan", "March", "April", "June"];
  months.splice(1, 0, "Feb"); // Insert at index 1
  console.log(months); // Output: ['Jan', 'Feb', 'March', 'April', 'June']

  months.splice(4, 1, "May"); // Replace element at index 4
  console.log(months); // Output: ['Jan', 'Feb', 'March', 'April', 'May']

  // The first parameter is the start index, second is delete count, rest are items to add.
  ```

**Checking Elements**

- **every()** - Tests whether all elements pass a test

  ```js
  const numbers = [1, 30, 39, 29, 10, 13];
  const allBelow40 = numbers.every((num) => num < 40);
  console.log(allBelow40); // Output: true

  // Returns true because every number is less than 40.
  ```

- **some()** - Tests whether at least one element passes a test

  ```js
  const numbers = [1, 2, 3, 4, 5];
  const hasEven = numbers.some((num) => num % 2 === 0);
  console.log(hasEven); // Output: true

  // Returns true because at least one number is even.
  ```

**Basic String Access Methods:**

- **charAt()** - Returns the character at a specified index

  ```js
  let str = "Hello";
  console.log(str.charAt(0)); // Output: "H"
  ```

- **Get last character** - Using array notation with length property
  ```js
  let str = "Hello";
  console.log(str[str.length - 1]); // Output: "o"
  ```

**String Manipulation Methods:**

- **replace()** - Replaces the first occurrence of a specified value

  ```js
  let text = "Hello world";
  console.log(text.replace("world", "universe")); // Output: "Hello universe"
  ```

- **repeat()** - Returns a new string with a specified number of copies

  ```js
  let word = "Hi";
  console.log(word.repeat(2)); // Output: "HiHi"
  ```

- **trim()** - Removes whitespace from both ends of a string=

  ```js
  let text = " Hello ";
  console.log(text.trim()); // Output: "Hello"
  ```

- **trimStart()/trimEnd()** - Removes whitespace from beginning/end of string

  ```js
  let text = " Hello ";
  console.log(text.trimStart()); // Output: "Hello "
  ```

- **split()** - Splits a string into an array of substrings
  ```js
  let str = "The quick brown fox";
  let words = str.split(" "); // Output: ["The", "quick", "brown", "fox"]
  ```

**String Information Methods:**

- **length** - Property that returns the length of a string

  ```js
  let text = "Hello";
  console.log(text.length); // Output: 5

  const sparseArray = [1, , , 4];
  console.log(sparseArray.length); // 4
  ```

  Now let's discuss how to create an empty array of fixed length. There are few ways to do this in JavaScript but one common method is to use the Array() constructor with a numeric argument. The Array() constructor can be used with the new keyword to create a new array. Here is an example:

  ```js
  const emptyArray = new Array(5);
  console.log(emptyArray.length); // 5
  console.log(emptyArray); // [,,,,]
  ```

  Another way to create an empty array of fixed length is to use the Array.from() method with a length argument. This method creates an array of the specified length with all elements initialized to undefined:

  ```js
  const fixedLengthArray = Array.from({ length: 5 });
  console.log(fixedLengthArray.length); // 5

  // [undefined, undefined, undefined, undefined, undefined]
  console.log(fixedLengthArray);
  ```

  If you want to create an array of specific length and fill it with a default value, you can use the Array.fill() method:

  ```js
  const filledArray = new Array(3).fill(0);
  console.log(filledArray); // [0, 0, 0]

  // This creates an array of length three and fills all elements with the value 0.
  ```

- **indexOf()** - Returns the position of the first occurrence of a value

  ```js
  let text = "Hello world";
  console.log(text.indexOf("world")); // Output: 6
  ```

- **lastIndexOf()** - Returns the position of the last occurrence of a value

  ```js
  let text = "Hello world world";
  console.log(text.lastIndexOf("world")); // Output: 12
  ```

- **includes()** - Returns true if a string contains a specified value
  ```js
  let text = "Hello world";
  console.log(text.includes("world")); // Output: true
  ```

**Case Conversion Methods:**
`js
    let text = "Hello";
    console.log(text.toUpperCase()); // Output: "HELLO"
    `

- **toLowerCase()** - Converts a string to lowercase
  ```js
  let text = "Hello";
  console.log(text.toLowerCase()); // Output: "hello"
  ```

**Substring Methods:**

- **substring()** - Extracts characters between two indices

  ```js
  let text = "Hello world";
  console.log(text.substring(0, 5)); // Output: "Hello"
  ```

- **slice()** - Extracts a part of a string and returns a new string
  ```js
  let text = "Hello world";
  console.log(text.slice(6)); // Output: "world"
  ```

## Tuple-like Structures (JS/TS)

Definition

JavaScript itself doesn’t have tuples, but TypeScript does. A tuple is a fixed-length, ordered array where each position has a specific type.

```ts
let tuple: [string, number, boolean];
tuple = ["Alice", 30, true];
```

- Indexing

  Access elements by position:

  ```ts
  console.log(tuple[0]); // "Alice"
  console.log(tuple[1]); // 30
  ```

- Destructuring

  Extract values into variables (like unpacking in Python):

  ```ts
  const [name, age, active] = tuple;
  console.log(name); // "Alice"
  console.log(age); // 30
  ```

- Optional and Rest Elements

  Tuples can define optional or rest elements:

  ```ts
  type OptionalTuple = [string, number?];
  type RestTuple = [string, ...number[]];

  const user: OptionalTuple = ["John"];
  const scores: RestTuple = ["Game 1", 10, 15, 20];
  ```

Summary
Tuples are fixed-length arrays with defined types per position.
Useful for structured returns and parameter pairs.

## Object Methods

Definition

Objects in JavaScript are collections of key–value pairs. They’re the closest equivalent to Python dictionaries.

```ts
const person = { name: "Alice", age: 30, city: "Tokyo" };
```

- `Object.keys()`

  Returns an array of keys.

  ```js
  console.log(Object.keys(person)); // ["name", "age", "city"]
  ```

- `Object.values()`

  Returns an array of values.

  ```js
  console.log(Object.values(person)); // ["Alice", 30, "Tokyo"]
  ```

- `Object.entries()`

  Returns key–value pairs as an array of arrays.

  ```js
  console.log(Object.entries(person));
  // [["name", "Alice"], ["age", 30], ["city", "Tokyo"]]
  ```

- Property Access

  ```js
  console.log(person.name); // "Alice"
  console.log(person["city"]); // "Tokyo"
  ```

- Spread Operator (Merging or Updating)

  ```js
  const updated = { ...person, job: "Developer" };
  console.log(updated);
  // { name: "Alice", age: 30, city: "Tokyo", job: "Developer" }
  ```

Summary
Objects are dynamic, flexible key-value containers.

Use `Object.\*()` methods to safely inspect and manipulate properties.

## Set Methods

Definition

ES6 introduced the Set object — a collection of unique values.

```js
const fruits = new Set(["apple", "banana", "cherry"]);
```

- `.add()`

  Adds an element.

  ```js
  fruits.add("orange");
  console.log(fruits); // Set(4) {"apple", "banana", "cherry", "orange"}
  ```

- `.delete()`

  Removes an element.

  ```js
  fruits.delete("banana");
  console.log(fruits); // Set(3) {"apple", "cherry", "orange"}
  ```

- `.has()`

  Checks membership.

  ```js
  console.log(fruits.has("apple")); // true
  ```

- Union and Intersection (via helpers)

  ```js
  const a = new Set([1, 2, 3]);
  const b = new Set([3, 4, 5]);

  const union = new Set([...a, ...b]);
  const intersection = new Set([...a].filter((x) => b.has(x)));

  console.log(union); // Set {1, 2, 3, 4, 5}
  console.log(intersection); // Set {3}
  ```

Summary

Set helps eliminate duplicates, perform quick membership checks, and supports math-like operations (union, intersection, difference).

## Classes and Constructors

Definition

Classes in JavaScript define blueprints for creating objects. They encapsulate data and behavior just like Python classes.

```js
class Person {
  constructor(name, age) {
    this.name = name; // instance property
    this.age = age;
  }

  greet() {
    console.log(`Hello, my name is ${this.name}.`);
  }
}

const p1 = new Person("Alice", 30);
p1.greet(); // "Hello, my name is Alice."
```

Key Concepts

- class → Defines a new object type.
- constructor → Initializes new instances.
- this → Refers to the instance (like self in Python).

Summary
Classes make JS more structured, supporting inheritance, encapsulation, and polymorphism (ES6+ OOP features).

## Object Model Hooks

Definition

Like Python’s dunder methods, JS objects can override built-in behaviors using special methods.

```js
class Book {
constructor(title, pages) {
this.title = title;
this.pages = pages;
}

toString() {
return `Book: ${this.title}`;
}

valueOf() {
return this.pages;
}

\*[Symbol.iterator]() {
for (let i = 1; i <= this.pages; i++) {
yield `Reading page ${i}`;
}
}
}

const book = new Book("JavaScript Mastery", 3);
console.log(String(book)); // "Book: JavaScript Mastery"
console.log(book + 2); // 5 (valueOf adds pages)
for (const p of book) console.log(p);
```

Summary
| Method | Purpose | Example |
| ----------------- | ------------------------ | -------------- |
| `toString()` | User-friendly string | `String(obj)` |
| `valueOf()` | Primitive representation | `obj + 2` |
| `Symbol.iterator` | Makes object iterable | `for...of obj` |

## Classes & Prototypes (Object-Oriented JavaScript)

JavaScript is a prototype-based language, not class-based like Python or Java — but since ES6, it includes the class syntax that acts as syntactic sugar over the prototype system.
Both styles define objects with shared behavior and inheritance.

- ES6 Class Syntax (Modern Approach)

  ```js
  class Person {
    constructor(name, age) {
      this.name = name;
      this.age = age;
    }

    greet() {
      console.log(`Hello, my name is ${this.name}.`);
    }
  }

  const person1 = new Person("Alice", 25);
  person1.greet(); // Output: Hello, my name is Alice.
  ```

  Key Notes:

  - class defines a blueprint for creating objects.
  - constructor() is automatically called when using new.
  - this refers to the instance being created.
  - Methods inside the class are stored on the prototype (shared by all instances).

- Class Inheritance (extends, super)

  ```js
  class Animal {
    constructor(name) {
      this.name = name;
    }

    speak() {
      console.log(`${this.name} makes a sound.`);
    }
  }

  class Dog extends Animal {
    constructor(name, breed) {
      super(name); // calls Animal's constructor
      this.breed = breed;
    }

    speak() {
      console.log(`${this.name} barks.`);
    }
  }

  const dog1 = new Dog("Buddy", "Golden Retriever");
  dog1.speak(); // Output: Buddy barks.
  ```

  Key Notes:

  - extends enables inheritance from another class.
  - super() calls the parent’s constructor or methods.
  - Method overriding is allowed.

- Static Methods and Fields

  ```js
  class MathHelper {
    static square(num) {
      return num * num;
    }
  }

  console.log(MathHelper.square(5)); // 25
  ```

  Notes:

  - static defines methods or properties that belong to the class itself (not instances).
  - Access them via ClassName.method(), not via an object.

- Getters and Setters

  ```js
  class Temperature {
    constructor(celsius) {
      this._celsius = celsius;
    }

    get fahrenheit() {
      return this._celsius * 1.8 + 32;
    }

    set fahrenheit(value) {
      this._celsius = (value - 32) / 1.8;
    }
  }

  const temp = new Temperature(25);
  console.log(temp.fahrenheit); // 77
  temp.fahrenheit = 86;
  console.log(temp.fahrenheit); // 86
  ```

  Notes:

  - get defines computed properties.
  - set allows controlled modification.

- Prototype-Based OOP (Pre-ES6)

  Before class syntax, JavaScript used constructor functions and the prototype chain directly.

  ```js
  function Person(name, age) {
    this.name = name;
    this.age = age;
  }

  Person.prototype.greet = function () {
    console.log(`Hi, I'm ${this.name}.`);
  };

  const p1 = new Person("Bob", 30);
  p1.greet(); // Hi, I'm Bob.
  ```

  How It Works:

  - Person is just a regular function used with new.
  - Each instance gets its own properties (name, age).
  - Shared methods (greet) live on Person.prototype.

- Prototype Inheritance Manually

  ```js
  function Animal(name) {
    this.name = name;
  }

  Animal.prototype.speak = function () {
    console.log(`${this.name} makes a sound.`);
  };

  function Dog(name) {
    Animal.call(this, name); // Inherit constructor properties
  }

  Dog.prototype = Object.create(Animal.prototype); // Inherit methods
  Dog.prototype.constructor = Dog;

  Dog.prototype.speak = function () {
    console.log(`${this.name} barks.`);
  };

  const dog = new Dog("Charlie");
  dog.speak(); // Charlie barks.
  ```

  Notes:

  - Object.create() sets up inheritance manually.
  - You must reset constructor to point to the child.
  - This was the standard way before ES6 introduced class syntax.

✅ Summary
| Concept | Modern Syntax | Pre-ES6 Equivalent |
| ------------------ | -------------------- | ------------------------------------------ |
| Define a blueprint | `class` | `function Constructor()` |
| Instance creation | `new ClassName()` | `new Constructor()` |
| Shared methods | Inside `class {}` | `Constructor.prototype.method` |
| Inheritance | `extends`, `super()` | `Object.create()` chain |
| Static methods | `static` keyword | Attach directly: `Constructor.method = fn` |

# Control Flow

## if/else if/ else

```js
const marks = 85;
if (marks >= 90) {
  console.log("Grade: A");
} else if (marks >= 80) {
  console.log("Grade: B");
} else if (marks >= 70) {
  console.log("Grade: C");
} else if (marks >= 60) {
  console.log("Grade: D");
}
```

An if statement takes a condition and runs a block of code if that condition is truthy.
Truthy values are any values that result in true when evaluated in a Boolean context like an if
statement. Here are examples of truthy values:
~ non-empty strings, for example, hello
~ any number other than 0 and -0, for example, 4, -5, and others
~ arrays
~ objects
~ the boolean true

On the other hand, falsy values are values that evaluate to false in a boolean context.
JavaScript has few falsy values, which makes them easy to remember. Here are a few falsy values:
~ boolean false
~ 0 (zero)
~ "" (empty string)
~ null
~ undefined
~ NaN (Not a Number)

```js
const marks = 85;
if (marks >= 90) {
  console.log("Grade: A");
} else if (marks >= 80) {
  console.log("Grade: B");
} else if (marks >= 70) {
  console.log("Grade: C");
} else if (marks >= 60) {
  console.log("Grade: D");
}

// Results below:
Grade: A;
```

```js
let creditScore = 720;
let annualIncome = 60000;
let loanAmount = 200000;

let eligibilityStatus;

if (creditScore >= 750 && annualIncome >= 80000) {
    eligibilityStatus = "Eligible for premium loan rates.";
    } else if (creditScore >= 700 && annualIncome >= 50000) {
    eligibilityStatus = "Eligible for standard loan rates.";
    } else if (creditScore >= 650 && annualIncome >= 40000) {
    eligibilityStatus = "Eligible for subprime loan rates.";
    } else if (creditScore < 650) {
    eligibilityStatus = "Not eligible due to low credit score.";
    } else {
    eligibilityStatus = "Not eligible due to insufficient income.";
    }

console.log(eligibilityStatus);

// Result below:
Eligible for premium loan rates.
```

```js
// Example below:
function getWordCount(sentence) {
  if (sentence.trim() === "") {
    return 0;
  }

  const words = sentence.trim().split(/\s+/);
  return words.length;
}

const wordCount = getWordCount("I love freeCodeCamp");
console.log(`Word Count: ${wordCount}`); // Word Count: 3
```

## switch

```js
switch (expression) {
let dayOfWeek = 3;

switch (dayOfWeek) {
    case 1:
        console.log("It's Monday! Time to start the week strong.");
        break;
    case 2:
        console.log("It's Tuesday! Keep the momentum going.");
        break;
    case 3:
        console.log("It's Wednesday! We're halfway there.");
        break;
    case 4:
        console.log("It's Thursday! Almost the weekend.");
        break;
    case 5:
        console.log("It's Friday! The weekend is near.");
        break;
    case 6:
        console.log("It's Saturday! Enjoy your weekend.");
        break;
    case 7:
        console.log("It's Sunday! Rest and recharge.");
        break;
    default:
        console.log("Invalid day! Please enter a number between 1 and 7.");
  }
```

## Loops

**"i" as the loop variable recognized by every programmer, stands for "index" or "iterator")**

**Synonym for "Iterable"**

You can think of it as:

- **"Loop-able"** (can be used in loops)
- **"Sequence-able"** (has an order of elements)
- **"Traversable"** (you can go through its items one by one)

  **Real-World Analogy**

Imagine:

- **Iterable** = A **bookshelf** (you can scan each book one by one).
- **Non-iterable** = A **single book** (you can’t "loop through" a standalone book).

**Strings are like bookshelves of characters. Numbers/booleans are single books.**

### Primary Loop Structures (for... / while / do... while)

- **for loop** - When you know how many iterations needed , processing arrays, need a counter.

  ```js
  //      start;         stop;             step
  for (initialization; condition; increment or decrement) {
      *code block to be executed
  }
  ```

  ```js
  for (const char of "code") {
    console.log(char);
  }

  // Output
  // c
  // o
  // d
  // e
  ```

  ```js
  const categories = ["Fruit", "Vegetable"];
  const foods = ["Apple", "Carrot", "Banana"];

  for (const category of categories) {
    for (const food of foods) {
      console.log(category, food);
    }
  }

  // Output
  // Fruit Apple
  // Fruit Carrot
  // Fruit Banana
  // Vegetable Apple
  // Vegetable Carrot
  // Vegetable Banana
  ```

  ```py
  categories = ['Fruit', 'Vegetable']
  foods = ['Apple', 'Carrot', 'Banana']

  for category in categories:
      for food in foods:
          print(category, food)

  # Output
  Fruit Apple
  Fruit Carrot
  Fruit Banana
  Vegetable Apple
  Vegetable Carrot
  Vegetable Banana
  ```

  ```js
  for (let i = 0; i <= 5; i++) {
    console.log("Iteration:", i);
  }

  /*Explanation:
  i value is 0
  i <= 5 means i is less than or equal to 5 so there is 5 arrays (1,2,3,4,5)
  i++ there means is increased by 1 each time, so the loop will run 5 times
  "" is there for regular text
  i there is for display result*/

  // Results below:
  Iteration: 0;
  Iteration: 1;
  Iteration: 2;
  Iteration: 3;
  Iteration: 4;
  Iteration: 5;
  ```

  ```js
  const color = ["red", "green", "blue", "yellow"];

  for (let i = 0; i < color.length; i++) {
    console.log("I =", i);
    console.log("color[i] =", color[i]);
  }

  /*Explanation:
  color is an array (there is 4 item)
  color.length is the number of items in the array
  i is the index of the array
  i++ there means is increased by 1 each time, so the loop will run 4 times*/

  //Results below:
  I = 0;
  color[i] = red;
  I = 1;
  color[i] = green;
  I = 2;
  color[i] = blue;
  I = 3;
  color[i] = yellow;
  ```

- **while loop** - Runs while condition is true

  A while loop will run a block of code as long as the condition is true.
  Best for: When you don't know how many times to repeat or need conditional repetition.
  When to use: When you don't know how many iterations you'll need, but want to check the condition before executing.

  ```js
  while (condition) {
      *code block to be executed
  }
  ```

  ```js
  //Example below:
  let userInput = prompt("Please enter a number between 1 and 10");

  while (isNaN(userInput) || Number(userInput) < 1 || Number(userInput) > 10) {
      userInput = prompt("Invalid input. Please enter a number between 1 and 10.");
  }

  alert("You entered a valid number!");

      /*Explanation:
      prompt() is used to get user input from the console while loop first checks if the userInput is NaN. Remember that NaN is "Not a Number".isNaN checks whether the value is NaN and that NaN is the result of an invalid number conversion because it's not a number. So if the user types in random characters or nothing at all, then they will be prompted with the message again. The while loop is also checking if the userInput, when converted to a number, is between 1 and 10. If the user input is not between 1 and 10, the while loop will continue to prompt the user to enter a number between 1 and 10.*/

  //Results below:
  Please enter a number between 1 and 10
  (user have to input text)
  You entered a valid number!
  ```

  ```js
  //Example below:
  let count = 0;

  while (count <= 5) {
    console.log("count =", count);
    count++;
  }
  /*Explanation:
      count value is 0
      count <= 5 means count is less than or equal to 5 so there is 5 arrays (1,2,3,4,5)
      count++ there means is increased by 1 each time, so the loop will run 5 times
      so if there is no count++ it will continue to loop until the condition is false*/

  //Results below:
  count = 0;
  count = 1;
  count = 2;
  count = 3;
  count = 4;
  count = 5;
  ```

- **do...while loop** - Runs at least once, then checks condition

  One key difference between a do...while loop and a while loop is that the do...while loop will execute the block of code at least once before checking the condition. If the condition is true, the block of code will continue to execute. If the condition is false, the block of code will stop executing.
  When to use: When you need to execute the code at least once, regardless of the condition.

  ```js
  do {
      *code block to be executed
  } while (condition);
  ```

  ```js
  //Example below:
  let number = 0;

  do {
    console.log("number = ", number);
    number++;
  } while (number <= 5);

  /*Explanation:
      number value is 0
      number <= 5 means number is less than or equal to 5 so there is 5 arrays (1,2,3,4,5)
      number++ there means is increased by 1 each time, so the loop will run 5 times
      so if there is no number++ it will continue to loop until the condition is false*/

  //Results below:
  number = 0;
  number = 1;
  number = 2;
  number = 3;
  number = 4;
  number = 5;
  ```

  ```js
  let num;

  do {
  num = prompt("Enter a number greater than 10")
  } while (num <= 10);

  console.log("Thank you.");

  /*Explanation:
  prompt() is used to get user input from the console
  num = prompt means the user will be prompted to enter something
  while (num <= 10) means the loop will continue to run as long as num is less than or equal to 10
  console.log("Thank you.") means the program will print "Thank you."
  when the user enters a number greater than 10 and the loop will end*/

  //Results below:
  Enter a number greater than 10
  (user have to input text)
  Thank you.
  ```

### Specialized Loops (for... of / for... in / forEach())

- **for...of loop** - When you need to loop over values from an iterable.

  Designed for iterable things like:
  Arrays ✅
  Strings ✅
  Maps ✅
  Sets ✅

  ```js
  for (variable of iterable) {
      *code block to be executed
  }
  ```

  ```js
  const fruits = ["Apple", "Banana", "Cherry"];
  for (let fruit of fruits) {
    console.log(fruit);
  }

  /*Explanation:
  fruits is an array (there is 3 item)
  f is the index of the array*/

  // Results below:
  Apple;
  Banana;
  Cherry;
  ```

  ```js
  // Example below:
  const str = "free";

  for (let char of str) {
    console.log(char);
  }

  // Results below:
  f;
  r;
  e * 2;
  ```

  ```js
  *// Example below:
  const people = [
      { name: 'John', age: 30 },
      { name: 'Jane', age: 25 },
      { name: 'Jim', age: 40 }
  ];

  for (const person of people) {
      console.log(`${person.name} is ${person.age} years old`);
  }

  // Results below:
  John is 30 years old
  Jane is 25 years old
  Jim is 40 years old
  ```

  ```js
  // Example below:
  function getPunctuationCount(sentence) {
    const punctuations = ".,!?;:-()[]{}\"'–";
    let count = 0;

    for (const char of sentence) {
      if (punctuations.includes(char)) {
        count++;
      }
    }
    return count;
  }

  const punctuationCount = getPunctuationCount("WHAT?!?!?!?!?");
  console.log(`Punctuation Count: ${punctuationCount}`); // Punctuation Count: 10
  ```

- **for...in loop** - For iterating through object properties names (keys)

  Designed for iterable things like:
  Objects ✅ (gets property names/keys)
  Arrays ⚠️ (works but not recommended - gets indices as strings)
  Strings ⚠️ (works but unusual - gets character positions)

  Best used when you need to loop over the properties of an object. This loop will iterate over all enumerable properties of an object, including inherited properties and non-numeric properties.

  ```js
  for (variable in object) {
      *code block to be executed
  }
  ```

  ```js
  const fruit = {
    name: "apple",
    color: "red",
    price: 0.99,
  };

  for (const prop in fruit) {
    console.log(fruit[prop]);
  }

  //Results below:
  apple;
  red;
  0.99;
  ```

  ```js
  const person = {
    name: "John", // First level (In fact it's already an Object)
    age: 30,
    address: {
      street: "123 Main St", // Second level (It's object within object)
      city: "Anytown",
      state: "CA",
    },
  };

  for (const prop in person) {
    console.log(person[prop]);
  }

  //Results below:
  John;
  30 > { street: `123 Main St`, city: `Anytown`, state: `CA` }; // Click to open the object

  /*Why there is > collapsible object now shown? It's because it is the object within the Object so not shown properly. It's like saying is this item a box?*/
  ```

  ```js
  //Example below:
  function isObject(obj) {
      return typeof obj === 'object' && !Array.isArray(obj) && obj !== null;
  }

  for (const prop in person) {
      if (isObject(person[prop])) {                   // Is this item a box(object within object)?
          for (const nestedProp in person[prop]) {    // If yes, open it!
              console.log(person[prop][nestedProp]);
          }
      } else {
          console.log(person[prop]);                  // If no, just show the item
      }
  }

  /* The difference maker is this line:
  *if (isObject(person[prop])) {

  *This is like asking: "Is this thing I just grabbed actually another box?"
  *If NO → Just show it
  *If YES → Open the box and show what's inside!*/

  //Results below:
  John
  30
  123 Main St
  Anytown
  CA
  ```

  !However for ... in ... is not recommended for arrays

  It is not recommended to use a for...in loop to loop over the elements of an array. Instead, use a for...of loop or other array methods like forEach, map, filter, and reduce. for...in loops through property names (keys), not the actual values. For arrays, this can cause unexpected behavior.

  ```js
  //Example below: Basic Array
  const fruits = ["apple", "banana", "orange"];

  for (const index in fruits) {
    console.log(index); // "0", "1", "2" (strings!)
    console.log(fruits[index]); // apple, banana, orange
  }
  //❌ for...in (NOT recommended)

  for (const fruit of fruits) {
    console.log(fruit); // apple, banana, orange (direct values)
  }
  //✅ for...of (recommended)
  //Problem: for...in gives you string indices, not numbers!
  ```

  ```js
  //Example below: The Real Danger (Added Properties):
  const numbers = [10, 20, 30];
  numbers.customProperty = 'I am not an array element!';

  for (const key in numbers) {
      console.log(key, numbers[key]);
  }
          //❌ for...in loops through EVERYTHING

  //Results below:
  "0" 10
  "1" 20
  "2" 30
  "customProperty" "I am not an array element!" ← UNWANTED!

  for (const num of numbers) {
      console.log(num);
  }
          //✅ for...of only loops through actual array elements

  //Results below:
  10
  20
  30
  ```

- **forEach()** - Executes a function once for each array element

  Parameters <br>
  Callback Function - Executed for each element, taking: <br>

  - currentValue - The current element being processed
  - index (optional) - The index of the current element
  - array (optional) - The array being traversed
  - thisArg (optional) - Value to use as this when executing callback

  ```js
  array.forEach(function (currentValue, index, array) {
    // code to execute for each element
  });
  ```

  ```js
  const sparseArray = [1, , 3];
  sparseArray.forEach((item) => console.log(item));
  // Output:
  // 1
  // 3
  // Performs the callback function on each element without returning anything.
  ```

Practical Use Cases

1. Modifying original array

   ```js
   const buttons = document.querySelectorAll("button");
   buttons.forEach((button) => {
     button.addEventListener("click", handleClick);
   });
   ```

2. DOM manipulation

   ```js
   const buttons = document.querySelectorAll("button");
   buttons.forEach((button) => {
     button.addEventListener("click", handleClick);
   });
   ```

3. Object iteration (with conversion)
   ```js
   const person = { name: "John", age: 30, job: "developer" };
   Object.keys(person).forEach((key) => {
     console.log(`${key}: ${person[key]}`);
   });
   ```

### Loop Control (break/continue/labelled loops)

A break statement is used to exit a loop early, while a continue statement is used to skip the current iteration of a loop and move to the next one.

- `break` - Exit loop early

  ```js
  for (let i = 0; i < 10; i++) {
    if (i === 5) {
      break;
    }
    console.log(i);
  }
  /*Inside the loop, we check if i is equal to 5. If it is, we use the break statement to exit the loop early. If not, we log the value of i to the console. So the output of the code will print the numbers 0, 1, 2, 3, and 4.*/
  ```

- `continue` - Skip current iteration

  ```js
  for (let i = 0; i < 10; i++) {
    if (i === 5) {
      continue;
    }
    console.log(i);
  }
  /*The output of this code will print the numbers 0, 1, 2, 3, 4, 6, 7, 8, and 9. The number 5 is skipped because of the continue statement.*/
  ```

- Labelled Loops: Outer Loop and Inner Loop

  ```js
  // Example below:
  outerLoop: for (let i = 0; i < 3; i++) {
    innerLoop: for (let j = 0; j < 3; j++) {
      if (i === 1 && j === 1) {
        break outerLoop;
      }
      console.log(`i: ${i}, j: ${j}`);
    }
  }

  /* When i is equal to 1 and j is equal to 1, we use the break statement with the outerLoop label to exit the outer loop early. This will exit both the inner and outer loops */

  // Results below:
  ("i: 0, j: 0");
  ("i: 0, j: 1");
  ("i: 0, j: 2");
  ("i: 1, j: 0");

  /* think of it I as the big box and J is the small box INSIDE the big box. you wont start counting the next big box until you done counting small box inside the first big box*/
  ```

  Think of loops like boxes inside boxes:

  ```js
  📦 BIG BOX (Outer Loop)
      📦 Small Box (Inner Loop)
      📦 Small Box (Inner Loop)
      📦 Small Box (Inner Loop)

  // Example below:
  for (let house = 1; house <= 2; house++) {
      console.log("🏠 House " + house);

      *Inner Loop = Which ROOM in this house
      for (let room = 1; room <= 3; room++) {
          console.log("  🚪 Room " + room);
      }
  }

  // Result below:
  🏠 House 1
  🚪 Room 1
  🚪 Room 2
  🚪 Room 3
  🏠 House 2
  🚪 Room 1
  🚪 Room 2
  🚪 Room 3
  ```

```js
const words = ['sky', 'apple', 'rhythm', 'fly', 'orange'];
const vowels = 'aeiou';

for (const word of words) {
    let hasVowel = false;
    for (const letter of word) {
        if (vowels.includes(letter.toLowerCase())) {
            console.log(`'${word}' contains the vowel '${letter}'`);
            hasVowel = true;
            break;
        }
    }
    if (!hasVowel) {
        console.log(`'${word}' has no vowels`);
    }
}

// Output
'sky' has no vowels
'apple' contains the vowel 'a'
'rhythm' has no vowels
'fly' has no vowels
'orange' contains the vowel 'o'
```

### There are a lot of purpose to use loop:

1. Accumulation
   Definition: Combining values across iterations to build a result (e.g., sums, concatenation).

   Scope Relevance: Critical (outer vars required)

   ```js
   let sum = 0;                    // Outer scope variable
   const numbers = [1, 2, 3];
   for (const num of numbers) {
   sum += num;                     // Accumulate across iterations
   }
   console.log(sum);               // 6

   // Explanation:
   The sum variable must be declared outside the loop to persist between iterations.
   Each iteration updates the same sum variable.
   Inner-scope variables would reset the accumulation.
   ```

2. Per-Item Processing
   Definition: Independent operations on each item (no cross-iteration dependency).

   Scope Relevance: Minimal (inner vars OK)

   ```js
   const words = ["hello", "world"];
   for (const word of words) {
       const upper = word.toUpperCase();   // Inner scope
       console.log(upper);                 // "HELLO", "WORLD"
   }

   // Explanation:
   upper is recreated each iteration (no need to persist).
   Inner scope avoids accidental reuse of stale values.
   No accumulation → no outer scope needed.
   ```

3. Searching
   Definition: Finding a specific value/condition in a collection.

   Scope Relevance: Optional (depends on algorithm)

   ```js
   // Example (outer scope for early exit):
   let foundItem;                  // Outer scope
   const items = ["a", "b", "c"];
   for (const item of items) {
       if (item === "b") {
           foundItem = item;
           break;                  // Exit early
       }
   }
   console.log(foundItem);         // "b"

   // Example (stateless search):
   const hasEven = [1, 3, 4].some(num => num % 2 === 0); // No outer scope needed

   // Explanation:
   Outer scope (foundItem) preserves results for early-exit searches
   Stateless searches (e.g., .some()) can use inner scope.
   ```

4. Side Effects
   Definition: Actions triggered per iteration (e.g., logging, DOM updates).

   Scope Relevance: Usually irrelevant

   ```js
   // Logging (scope doesn't matter)
   for (let i = 0; i < 2; i++) {
   console.log(`Iteration ${i}`); // Side effect
   }

   // DOM updates
   const buttons = ["OK", "Cancel"];
   buttons.forEach(text => {
   document.body.appendChild(createButton(text)); // Side effect
   });

   // Explanation:
   Side effects don’t require preserving data across iterations.
   Scope choice depends on readability, not functionality.
   ```

5. Data Generation
   Definition: Creating new data structures or sequences incrementally.

   ```js
   let fibonacci = [0, 1]; // Outer scope
   for (let i = 2; i < 10; i++) {
     fibonacci.push(fibonacci[i - 1] + fibonacci[i - 2]);
   }

   // Scope Need: Outer variables required to maintain growing sequence.
   ```

6. State Machines
   Definition: Maintaining and updating application state.

   ```js
   let position = 0; // Outer scope
   let velocity = 1;
   while (position < 100)
       position += velocity;
       velocity *= 1.1;
       updateGameCharacter(position); // Side effect
   }
   // Scope Need: Outer variables essential for state persistence.
   ```

7. Recursion Simulation
   Definition: Implementing iterative alternatives to recursive algorithms.

   ```js
   function factorial(n) {
     let result = 1; // Outer scope
     while (n > 1) {
       result *= n;
       n--;
     }
     return result;
   }

   // Scope Need: Outer variables preserve intermediate calculations.
   ```

8. Control Flow
   Definition: Managing program flow rather than data processing.
   ```js
   let attempts = 0; // Outer scope
   do {
     attempts++;
   } while (!apiRequestSucceeded() && attempts < 5);
   // Scope Need: Minimal (inner vars possible), but often uses outer for attempt counters.
   ```

When to Use Which Framework

- For scope decisions: Use the original 1 to 4 category model
- For algorithm design: Use the expanded 1 to 8 category model
- For performance optimization: Consider loop type (e.g., while vs for)

All loop applications ultimately fall into two fundamental patterns:

- Stateful loops: Require outer scope (accumulation, state machines)
- Stateless loops: Work with inner scope (transformation, side effects)

Key Insight

The classification answers:

- When to "remember" state (outer scope for accumulation).
- When to isolate (inner scope for independent operations).
- When scope doesn’t drive the logic (side effects).

This framework helps choose the right scope strategy for your loop’s purpose.

## return

`return` ends the current function and hands a value back to the caller. If no value is provided, the result is `undefined`. You cannot use `return` outside a function.
[MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return?utm_source=chatgpt.com)

Why it exists. Functions are little black boxes: inputs → work → output. `return` is the output chute.

- Regular function

  ```js
  function area(r) {
    if (r < 0) return 0; // early exit
    return Math.PI * r * r; // final result
  }
  ```

- Async function — always returns a Promise. <br>
  Returning `x` resolves the returned Promise with `x`. Throwing rejects it.

  ```js
  async function load() {
    return 42; // resolves to 42
  }
  ```

  (Equivalent to `Promise.resolve(42)`). [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function?utm_source=chatgpt.com)

- Generator (`function*`) — `return` finishes the generator and sets the `{ value, done: true }` of the final iterator result. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/function%2A?utm_source=chatgpt.com)

Visualization (what return means).

```
caller --> [ function body ... return VALUE ] --> caller gets VALUE
```

- A return inside finally overrides earlier return or throw. Prefer not to return from finally unless you know why.
- In async functions, return → fulfilled Promise; throw → rejected Promise. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function?utm_source=chatgpt.com)

## throw

`throw` aborts the current execution path by raising an exception value (any value, though `Error` objects are recommended). Control jumps to the nearest matching `catch`; if none exists, the error becomes unhandled. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/throw?utm_source=chatgpt.com)

Why it exists. It signals “this path cannot proceed”—for programmer errors, invalid input, failed invariants, or expected exceptional conditions.

```js
// Throwing built-in errors (recommended)
function parsePort(s) {
  const n = Number(s);
  if (!Number.isInteger(n) || n < 0) {
    throw new RangeError("Invalid port"); // aborts here
  }
  return n;
}

// Custom error with 'cause' (ES2022)
try {
  // ...
} catch (e) {
  throw new Error("Failed to start", { cause: e });
}
```

Async interplay.

- Inside an async function, `throw` rejects the function’s returned Promise.
- Rejections are caught with `try…catch` around `await`, or with `.catch()` in Promise chains. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Async_JS/Promises?utm_source=chatgpt.com)

Visualization (propagation).

```
throw --> bubble up call stack --> nearest try { ... } catch(e) { ... } handles it
```

- `return` → Function control flow & outputs (regular functions, async functions, generators). [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/return?utm_source=chatgpt.com)

## try / catch / finally

A `try` block lets you run code that might fail. If it throws, control jumps to `catch`. The `finally` block (if present) runs no matter what (success, failure, or early `return`) before exiting the whole construct. Since ES2019, `catch` can omit the error binding: `catch { ... }`. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch?utm_source=chatgpt.com)

Why it exists. It’s the language’s structured error-handling: keep the happy path readable while providing a safe landing zone for failures.

Core shapes.

```js
try {
  risky();
} catch (err) {
  // handle or rethrow
} finally {
  cleanup();
}
```

With async & await.

```js
async function main() {
  try {
    const data = await getData(); // if this rejects...
    use(data);
  } catch (err) {
    // ...control comes here
    console.error("Failed:", err);
  } finally {
    stopSpinner();
  }
}
```

- `catch` handles synchronous throws in the `try` block and rejections from awaited Promises. If you forget `await`, the rejection won’t be caught here. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Async_JS/Promises?utm_source=chatgpt.com)

Visualization (control flow).

```
try {
   [ run code ]
   ├─ success ───────────────┐
   └─ throw/reject ─> catch  │
                 (optional)  │
finally { always runs } <────┘
```

- `finally` always runs (including after `return`/`throw`)—except on hard termination (e.g., process exit). [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch?utm_source=chatgpt.com)
- Syntax errors aren’t catchable; `try…catch` only handles runtime errors in the executed block. [javascript.info](https://javascript.info/try-catch?utm_source=chatgpt.com)

try / catch / finally → Structured error handling with guaranteed cleanup via finally. Works with sync code and with awaited Promises. [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch?utm_source=chatgpt.com)

# Functions & Scope

Functions are reusable pieces of code that perform a specific task or calculate a value.
Think of functions as a machine that takes some input, does some operations on it, and
then produces an output. Functions can be called by their name, and they can take parameters.

Different ways to define functions:

## Function declaration:

```js
function greet(name) {
  console.log("Hello, " + name + "!");
}
greet("Alice"); // Hello, Alice!
```

It's like a simple variable declaration like let, const,var but it can store more complicated value. It can perform a specific task or calculate a value. Think of functions as a machine that takes some input, does some operations on it, and then produces an output. Functions can be called by their name, and they can take parameters.

Parameters act as placeholders for the values that will be passed to the function when it is called. They allow functions to accept input and work with that input. Arguments are the actual values passed to the function when it is called. Here is an updated version of the greet function that uses parameters and arguments:

```js
function greet(name) {
  console.log("Hello, " + name + "!");
}

greet("Alice"); // Hello, Alice!
greet("Nick"); // Hello, Nick!
```

The name serves as the parameter while the strings Alice and Nick serve as the arguments. Now we have a reusable function that can be used dozens of times throughout our code with different arguments.

When a function finishes its execution, it will always return a value.
By default, the return value will be undefined.

```js
function doSomething() {
  console.log("Doing something...");
}

let result = doSomething();
console.log(result); // undefined
```

If you need your function to return a specific value, then
you will need to use the return statement.

```js
function calculateSum(num1, num2) {
  return num1 + num2;
}

console.log(calculateSum(3, 4)); // 7
```

In this example, we have a const variable called sum and we are assigning it an anonymous function that returns the sum of num1 and num2. We are then able to call sum and pass in the numbers 3 and 4 to get the result of 7.

```js
const sum = function (num1, num2) {
  return num1 + num2;
};

console.log(sum(3, 4)); // 7
```

Functions support default parameters, allowing you to set default values for parameters.
These default values are used if the function is called without an argument for that parameter.

```js
function greetings(name = "Guest") {
  console.log("Hello, " + name + "!");
}

greetings(); // Hello, Guest!
greetings("Anna"); // Hello, Anna!

function mystery(a, b = 3) {
  return a * b;
}
console.log(mystery(4));
```

## `=>` Arrow functions

```js
//same output, different method
function greetings(name) {
  console.log("Hello, " + name + "!");
}

//same output, different method
const greetings = (name) => {
  console.log("Hello, " + name + "!");
};
```

In this revised example, we are creating a const variable called greetings and assigning it an anonymous function. Most of the syntax will look familiar to you except for the missing function keyword and the addition of the arrow (=>) between the name parameter and the function body. If your parameter list only has one parameter in it, then you can remove the parentheses like this:

```js
const greetings = (name) => {
  console.log("Hello, " + name + "!");
};
```

If your arrow function has no parameters, then you must use the parentheses like this:

```js
const greetings = () => {
  console.log("Hello");
};
```

When first learning about functions, you had to wrap the function body in curly braces. But if your function body only contains a single line of code, you can remove the curly braces like this:

```js
const greetings = (name) => console.log("Hello, " + name + "!");
```

It is important to note that removing the parentheses and curly braces for regular function syntax will not work. You will get errors if you tried to do something like this:

```js
function greetings name console.log("Hello, " + name + "!");
      // This will produce syntax errors
```

These types of one line functions only work if you are using the arrow function syntax. Another key concept is the return statement.

```js
const calculateArea = (width, height) => {
  const area = width * height;
  return area;
};

console.log(calculateArea(5, 3)); // 15
```

We are creating a variable inside the function called area and then returning that variable. But we could clean up our code a bit and return the calculation itself:

```js
const calculateArea = (width, height) => {
  return width * height;
};
```

If you tried to remove the curly braces and place the calculation on the same line, then you would get an Uncaught SyntaxError: Unexpected token 'return' message:

```js
const calculateArea = (width, height) => width * height;
```

## Closures

Definition: A function that remembers and accesses variables from its outer (enclosing) scope, even after the outer function has finished executing.

Requires:

- A nested function.
- Reference to an outer variable.

Closures are one of the most powerful and often misunderstood features in JavaScript. At its core, a closure is a function that has access to variables in its outer enclosing lexical scope, even after the outer function has returned. This might sound complex but it's a fundamental concept that enables many advanced programming patterns in JavaScript.

```js
function outerFunction(x) {
  let y = 10;
  function innerFunction() {
    console.log(x + y);
  }
  return innerFunction;
}

let closure = outerFunction(5);
closure(); // Output: 15

/*In this example, outerFunction takes a parameter x and defines a local variable y. It then defines an innerFunction that uses both x and y. Finally it returns innerFunction. When we call outerFunction(5) it returns innerFunction which we assign to the variable closure. When we later call closure() it still has access to x and y from outerFunction even though outerFunction has already finished executing. This is the essence of a closure.*/
```

```js
function outer() {
  const x = 10;
  function inner() {
    console.log(x); // Accesses `x` from `outer`'s scope (closure)
  }
  return inner;
}
const closureFunc = outer();
closureFunc(); // Logs `10` (closure preserves `x`)
```

Closures are particularly useful for creating private variables and functions. Consider this example:

```js
function createCounter() {
  let count = 0;
  return function () {
    count++;
    return count;
  };
}

let counter = createCounter();
console.log(counter()); // Output: 1
console.log(counter()); // Output: 2

/*In this case, createCounter returns a function that increments and returns a count variable. The count variable is not directly accessible from outside createCounter, but the returned function (our closure) has access to it. Each time we call counter(), it increments and returns the count.*/
```

Closures can also capture multiple variables from their outer scope. For example:

```js
function multiply(x) {
  return function (y) {
    return x * y;
  };
}

let double = multiply(2);
console.log(double(5)); // Output: 10

/*Here the inner function captures the x parameter from multiply. When we create double by calling multiply(2) it returns a function that always multiplies its argument by 2.*/
```

## Scope Accessibility

Definition: Determines where variables/functions can be accessed.

Scope in programming refers to the visibility and accessibility of variables in
different parts of your code. It determines where variables can be accessed or modified. In JavaScript, understanding scope is crucial for writing clean, efficient, and bug-free code.

Global scope is the outermost scope in a JavaScript program.
Variables declared in the global scope are accessible from anywhere in your code,
including within functions and blocks. These variables are often called global variables.
While global variables can be convenient, they should be used sparingly as they can lead to
naming conflicts and make your code harder to maintain. Here's an example of a global variable:

Variable accessibility in different parts of code:

- **Global scope** - Variables accessible everywhere
- **Local scope** - Variables only accessible within functions
- **Block scope** - Variables only accessible within {} blocks (with let/const)

```js
let globalVar = "I'm a global variable";

function printGlobalVar() {
  console.log(globalVar);
}

printGlobalVar(); // Output: "I'm a global variable"

// In this example, globalVar is declared in the global scope and can be accessed inside the printGlobalVar function.

// Local scope, on the other hand, refers to variables that are only accessible within a function.
function greet() {
  let message = "Hello, local scope!";
  console.log(message);
}

greet(); // Output: "Hello, local scope!"
console.log(message); // This will throw an error

// In this code, message is a local variable within the greet function. It can be used inside the function, but trying to access it outside the function will result in an error.
```

In this code, message is a local variable within the greet function. It can be used inside the function, but trying to access it outside the function will result in an error.

Block scope is a concept introduced with the let and const keywords in ES6.
A block is any code section within curly braces, {}, such as in if statements, for loops, or
while loops. The concept of loops will be taught in an upcoming lecture.

Variables declared with let or const inside a block are only accessible within that block.

```js
if (true) {
  let blockVar = "I'm in a block";
  console.log(blockVar); // Output: "I'm in a block"
}
console.log(blockVar); // This will throw an error

/*In this example, blockVar is only accessible within the if block. Trying to access it outside the block will result in an error. Understanding these different types of scope is essential for managing variable accessibility and avoiding unintended side effects in your code.*/
```

Global variables should be used sparingly, as they can lead to naming conflicts and
make your code harder to maintain. Local variables help to keep different parts of your
code isolated, which is especially useful in larger programs. Block scoping with let and
const provides even finer control over variable accessibility, helping to prevent errors and
make your code more predictable. Mastering these basic concepts of global, local, and
block scope will provide a solid foundation for understanding more advanced topics.

# Asynchronous JavaScript

Asynchronous JavaScript refers to techniques that allow code execution without blocking the main thread. In simple terms, instead of waiting for a task (like fetching data from a server) to finish before moving on, JavaScript can “set it aside” and continue running other code, then come back when the task is done.

Why it matters: JavaScript runs on a single thread (one task at a time). Without asynchrony, a slow task (like downloading a file) would freeze the entire page. Asynchrony keeps apps smooth and responsive.

Visualization:

```
[Normal Sync Code]          [Async Code Flow]
 Task A (waits 3s)           Task A (starts)
 Task B (waits A done)       Task B (runs immediately)
 Task C (waits B done)       Task C (runs immediately)
                            [Meanwhile... A finishes later, result returned]
```

Asynchrony in JavaScript is basically an act of tolerance with reality.

**JavaScript is `single-threaded`. That means `it can’t do two things literally at once` in the same thread. So how does it “pretend” to `multitasking`? By compromising:**

- Instead of blocking (like “I’ll just sit here and wait while the file downloads”),
- it says “Okay, I’ll note that you’re downloading. Meanwhile, I’ll keep serving other requests, drawing the UI, running animations. Ping me when you’re done.”

It’s like `human multitasking`, but not the kind where you truly do two things at once (brains are bad at that). It’s the kind where you set a task aside, let it run in the background, and pick it up when it’s ready.

Example in human terms:

- Synchronous life:

  You put water on the stove to boil. You stand there staring at the pot, waiting, doing nothing else until it boils. Super inefficient.

- Asynchronous life:

  You put water on the stove to boil. While it’s heating, you chop vegetables and set the table. Later the pot whistles at you (callback/Promise resolution), and you handle it.

## async Function

An async function is a special type of function in JavaScript that always returns a Promise. Inside it, you can use the await keyword to pause execution until another asynchronous operation finishes.

```js
async function greet() {
  return "Hello";
}

greet().then((msg) => console.log(msg));
// Logs: "Hello"
```

Even though we just returned a string, the function actually returned a Promise that resolves to "Hello".

With `await`

```js
async function fetchData() {
  let res = await fetch("https://jsonplaceholder.typicode.com/todos/1");
  let data = await res.json();
  console.log(data);
}

fetchData();
```

```js
async function fetchData() {
  let response = await fetch("https://api.example.com/data");
  let json = await response.json();
  return json; // returns a Promise
}
```

Here:

- `await fetch(...)` pauses until the Promise from `fetch` resolves.
- Then we can safely call `.json()` on the result.
- The code looks synchronous, but under the hood it’s asynchronous.

Error handling

```js
async function safeFetch() {
  try {
    const res = await fetch("/wrong-url");
    const data = await res.json();
    return data;
  } catch (err) {
    console.error("Something went wrong:", err);
  }
}
```

With `try/catch`, errors in awaited Promises can be handled like synchronous exceptions.

Plain-English Explanation

- Normal function: runs from top to bottom, returns a value immediately.
- Async function: runs, but instead of returning a plain value, it wraps the result in a Promise. If you `return "hi"`, the function really returns `Promise.resolve("hi")`.
- Inside, `await` makes the code “pause” until the awaited Promise is settled, then execution continues.
- This makes asynchronous code linear and much easier to read than nested `.then(...)` chains.

Visualization
Execution model of async function:

```js
async function myFunc() {
   const a = await step1();   // pause until step1 resolves
   const b = await step2(a);  // then pause until step2 resolves
   return b;
}

Your code ----> myFunc() call
               returns a Promise immediately
               |
               v
           [execution happens]
     step1() ---wait---> step2() ---wait---> return value
               |
               v
        Promise resolves to final value
```

#### Clear Difference: async function vs normal function

| Feature                    | **Normal `function`**                                                    | **`async function`**                                                                            |
| -------------------------- | ------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------- |
| Return value               | Returns a plain value (number, string, object, etc.).                    | Always returns a **Promise** (even if you `return 5`, it’s `Promise.resolve(5)`).               |
| Asynchronous code handling | Must use callbacks or `.then()` to work with Promises.                   | Use `await` to pause and resume execution inside the function, making code linear and readable. |
| Error handling             | Errors throw immediately, must be caught by `try/catch` around the call. | Can use `try/catch` inside the async function to handle errors from `await`ed Promises.         |
| Readability                | Asynchronous code looks nested / chained.                                | Asynchronous code looks synchronous, easier to follow.                                          |

Example side by side:

Normal function returning a value

```js
function normalFunc() {
  return 5;
}

console.log(normalFunc()); // 5
```

Async function returning a value

```js
async function asyncFunc() {
  return 5;
}

console.log(asyncFunc()); // Promise { 5 }
asyncFunc().then(console.log); // 5
```

So the only visible difference at call site:

- Normal = gives you the value directly.
- Async = gives you a Promise that eventually resolves to the value.

Bottom line

- `async function` is a newer function type designed to make asynchronous code easier.
- The essential difference: return type (value vs Promise) and the ability to use `await` inside.
- Use `async` when dealing with tasks that take time (network calls, file reads, timers). Use normal functions for everything else.

## Promises

A Promise is a JavaScript object representing the eventual result of an asynchronous operation. Think of it as a placeholder for a value that might not be available yet.

States of a Promise

- Pending: Still working.
- Fulfilled: Finished successfully.
- Rejected: Failed with an error.
- Visualization:

```
Promise lifecycle:
[ Pending ] ---> [ Fulfilled : value ]
          \---> [ Rejected : error ]
```

### new Promise (executor)

You can manually create a Promise using the `new Promise()` constructor.<br>
The `executor` is a function with two arguments:

- resolve(value) → marks success.
- reject(error) → marks failure.

```js
let promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Done!"), 1000);
});

promise.then((result) => console.log(result)); // Done! (after 1s)
```

### Static methods

Static methods are built-in helpers attached to the Promise class itself.

- `Promise.resolve(value)` → creates an immediately resolved promise.
- `Promise.reject(error)` → creates an immediately rejected promise.
- `Promise.all([p1, p2])` → runs multiple promises in parallel, waits for all.
- `Promise.race([p1, p2])` → returns the result of the first finished promise.
- `Promise.allSettled([p1, p2])` → waits for all, gives success/failure info.
- `Promise.any([p1, p2])` → resolves with the first success (ignores rejections).

Visualization:

```
Promise.all    -> [✓ ✓ ✓] Waits for ALL
Promise.race   -> [✓ ✗ ✓] First finished wins
Promise.any    -> [✗ ✓ ✗] First SUCCESS wins
Promise.allSettled -> [✓ ✗ ✓] Gives full report
```

### Instance methods (.then / .catch / .finally)

These are called on an existing Promise.

- `.then(onFulfilled, onRejected)` → handle success or failure.
- `.catch(onRejected)` → handle only failure.
- `.finally(onFinally)` → run cleanup code (success or failure).

```js
fetch("https://api.example.com/data")
  .then((res) => res.json())
  .then((data) => console.log(data))
  .catch((err) => console.error("Error:", err))
  .finally(() => console.log("Done fetching"));
```

## Iterators & Generators (sync and async)

- Iterators

  An iterator is an object that defines a sequence and a way to step through it.
  It has a `next()` method that returns `{ value, done }`.

  ```js
  let arr = [10, 20, 30];
  let iterator = arr[Symbol.iterator]();

  console.log(iterator.next()); // { value: 10, done: false }
  console.log(iterator.next()); // { value: 20, done: false }
  console.log(iterator.next()); // { value: 30, done: false }
  console.log(iterator.next()); // { value: undefined, done: true }
  ```

- Generators

  Generators are special functions that can pause and resume using `function*` and `yield`.

  ```
  function* numberGen() {
    yield 1;
    yield 2;
    yield 3;
  }
  let gen = numberGen();
  console.log(gen.next()); // { value: 1, done: false }
  ```

- Async Generators
  Work like generators but yield Promises. Declared with `async function*`.
  ```js
  async function* asyncNumbers() {
    yield 1;
    yield 2;
  }
  for await (let n of asyncNumbers()) {
    console.log(n); // 1, then 2
  }
  ```

## Error handling in async (try/catch with await)

When using async/await, errors can be caught using try/catch just like synchronous code.

```js
async function loadData() {
  try {
    let response = await fetch("bad-url"); // will throw
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Caught error:", error.message);
  }
}
```

This is cleaner than handling errors only with .catch() in promises.

# TypeScript vs JavaScript — Deep Technical Documentation

```
Core Idea:
TypeScript is a superset of JavaScript.
Every valid JavaScript program is valid TypeScript, but TypeScript adds compile-time types and tooling features that vanish at runtime, leaving pure JavaScript to execute.
```

Think of JavaScript as the runtime language, while TypeScript is a layer of metadata and constraints on top of it.

TS gives your code eyes, but those eyes disappear before running.

## 1. Grammar (Syntax Layer)

Grammar defines what symbols and structures are legal.

| Feature   | JavaScript                                | TypeScript                                                                                     |
| --------- | ----------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Variables | `var`, `let`, `const`                     | Same, plus **type annotations**                                                                |
| Functions | Standard function syntax, arrow functions | Same + typed parameters and return types                                                       |
| Classes   | ES6 classes supported                     | Same + typed properties, access modifiers (`public`, `private`, `protected`), abstract classes |
| Modules   | `import`, `export` (ES Modules)           | Same, plus TS-specific module resolution and `import type`                                     |
| Comments  | `//`, `/* */`                             | Same, plus `/** JSDoc */` works for type hints                                                 |
| Types     | Runtime only (dynamic)                    | Compile-time type annotations                                                                  |

JavaScript

```js
function add(a, b) {
  return a + b;
}
```

TypeScript

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

Type annotations (: number) do not exist in JS.

## 2. Constructs TypeScript Adds That JavaScript Lacks

These are the building blocks unique to TypeScript.

Each of these introduces capabilities that don’t exist in plain JS.

- Type Annotations

  Attach explicit types to variables, parameters, and return values.

  ```ts
  let username: string = "Eeve";
  let age: number = 25;
  let isAdmin: boolean = true;
  ```

  At runtime: These annotations vanish — the emitted JS just has the values.

- Interfaces and Type Aliases

  Define custom shapes for objects and functions

  ```ts
  interface User {
    id: number;
    name: string;
  }

  type StringOrNumber = string | number;

  function printId(id: StringOrNumber) {
    console.log(id);
  }
  ```

  Interfaces are extensible (extends) and perfect for modeling structured data like API responses.

- Union and Intersection Types

  Unions express either/or, intersections express both at once.

  ```ts
  // Union
  let input: string | number;
  input = "hello";
  input = 42;

  // Intersection
  type A = { a: number };
  type B = { b: string };
  type AB = A & B; // must have both `a` and `b`
  ```

  JavaScript cannot declare these relationships at compile time.

- Generics

  Reusable, type-safe code.

  ```ts
  function identity<T>(value: T): T {
    return value;
  }

  let result = identity<string>("Hello"); // `T` inferred as string
  ```

  JavaScript has no way to express this safety — you’d rely on documentation or runtime checks.

- Enums

  Named constants for better readability.

  ```ts
  enum Direction {
    Up,
    Down,
    Left,
    Right,
  }

  let move: Direction = Direction.Up;
  ```

  At runtime, compiled to a JS object:

  ```hs
  {
    0: "Up",
    1: "Down",
    2: "Left",
    3: "Right",
    Up: 0,
    Down: 1,
    Left: 2,
    Right: 3
  }
  ```

- Tuples

  Fixed-size arrays with known types per index.

  ```ts
  let point: [number, number] = [0, 0];
  let person: [string, number, boolean] = ["Alice", 30, true];
  ```

  JavaScript only has plain arrays — no way to enforce structure at compile time.

- Access Modifiers in Classes

  ```ts
  class Person {
    private ssn: string; // only inside class
    protected birthDate: Date; // inside class + subclasses
    public name: string; // anywhere

    constructor(name: string, ssn: string, birthDate: Date) {
      this.name = name;
      this.ssn = ssn;
      this.birthDate = birthDate;
    }
  }
  ```

  JS has no private/protected enforcement except for recent #private syntax — TS provides static enforcement

- Utility Types (Built-in Helpers)

  Reusable type transformations:

  | Utility Type  | Purpose                       |
  | ------------- | ----------------------------- |
  | `Partial<T>`  | Make all properties optional  |
  | `Required<T>` | Make all properties required  |
  | `Pick<T, K>`  | Select a subset of properties |
  | `Omit<T, K>`  | Exclude specific properties   |
  | `Readonly<T>` | Prevent modification          |

  ```ts
  interface User {
    id: number;
    name: string;
    email: string;
  }

  type UserPreview = Pick<User, "id" | "name">;
  ```

- Decorators (Experimental)

  Attach metadata or behavior to classes and methods.

  ```ts
  function log(target: any) {
    console.log("Decorator applied to:", target);
  }

  @log
  class MyClass {}
  ```

  Only in TS (or with experimental JS proposals).

- Type-Only Imports

  Avoid importing runtime code when you only need types.

  ```ts
  import type { User } from "./models";
  ```

  JavaScript can’t distinguish between type-only and runtime imports.

## 3. Semantics (Meaning & Runtime Behavior)

| Aspect          | JavaScript             | TypeScript                                 |
| --------------- | ---------------------- | ------------------------------------------ |
| Type Checking   | Runtime only           | Compile-time                               |
| Error detection | Only when code runs    | Before running (compiler catches)          |
| Tooling         | Basic autocomplete     | Rich autocomplete, refactoring, navigation |
| Scalability     | Harder for large teams | Easier with shared type contracts          |
| Output code     | Original JS            | JS with types removed                      |

## 4. React + TypeScript Event Deep Dive

This is where many niche TypeScript-only constructs live, such as:

```tsx
(e: React.ChangeEvent<HTMLInputElement>)
```

JavaScript doesn’t have these because JS events are untyped until runtime and TS provides synthetic event types from @types/react.

- Why You Need e.currentTarget

  e.target is very generic (EventTarget) and does not guarantee .value exists.

  TS will error on:

  ```tsx
  const handleChange = (e) => {
    console.log(e.target.value); // ❌ Type error
  };
  ```

  Correct way:

  ```tsx
  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    console.log(e.currentTarget.value); // ✅ Fully typed
  };
  ```

- Common React Event Types

| Element               | Event                                    | Type Annotation (for handler parameter)       |
| --------------------- | ---------------------------------------- | --------------------------------------------- |
| `<input>` onChange    | `React.ChangeEvent<HTMLInputElement>`    | `(e: React.ChangeEvent<HTMLInputElement>)`    |
| `<textarea>` onChange | `React.ChangeEvent<HTMLTextAreaElement>` | `(e: React.ChangeEvent<HTMLTextAreaElement>)` |
| `<select>` onChange   | `React.ChangeEvent<HTMLSelectElement>`   | `(e: React.ChangeEvent<HTMLSelectElement>)`   |
| `<form>` onSubmit     | `React.FormEvent<HTMLFormElement>`       | `(e: React.FormEvent<HTMLFormElement>)`       |
| `<button>` onClick    | `React.MouseEvent<HTMLButtonElement>`    | `(e: React.MouseEvent<HTMLButtonElement>)`    |
| Keyboard events       | `React.KeyboardEvent<HTMLInputElement>`  | `(e: React.KeyboardEvent<HTMLInputElement>)`  |

- Example: Fully Typed React Component

  ```tsx
  import React, { useState } from "react";

  function SignupForm(): JSX.Element {
    const [email, setEmail] = useState<string>("");
    const [agree, setAgree] = useState<boolean>(false);

    const handleEmailChange = (e: React.ChangeEvent<HTMLInputElement>) => {
      setEmail(e.currentTarget.value); // safe access to value
    };

    const handleCheckboxChange = (e: React.ChangeEvent<HTMLInputElement>) => {
      setAgree(e.currentTarget.checked); // safe access to checked
    };

    const handleSubmit = (e: React.FormEvent<HTMLFormElement>) => {
      e.preventDefault();
      console.log({ email, agree });
    };

    return (
      <form onSubmit={handleSubmit}>
        <input type="email" value={email} onChange={handleEmailChange} />
        <input
          type="checkbox"
          checked={agree}
          onChange={handleCheckboxChange}
        />
        <button type="submit">Sign Up</button>
      </form>
    );
  }

  export default SignupForm;
  ```

- Niche Situations

  File Input

  ```tsx
  const handleFile = (e: React.ChangeEvent<HTMLInputElement>) => {
    const file = e.currentTarget.files?.[0];
    if (file) console.log(file.name);
  };
  ```

  Casting when using e.target

  ```tsx
  const handleChange = (e: React.ChangeEvent<HTMLInputElement>) => {
    const target = e.target as HTMLInputElement;
    console.log(target.value);
  };
  ```

  Generic event handler

  ```tsx
  function handleEvent<T extends HTMLElement>(e: React.SyntheticEvent<T>) {
    console.log(e.currentTarget.tagName);
  }
  ```

## 5. Summary Table

| Layer             | JavaScript                   | TypeScript                                                                         |
| ----------------- | ---------------------------- | ---------------------------------------------------------------------------------- |
| Grammar           | Pure ECMAScript syntax       | ECMAScript + type annotations                                                      |
| Constructs        | Functions, classes, modules  | + Interfaces, generics, enums, tuples, utility types, access modifiers, decorators |
| Semantics         | Runtime-only type checking   | Compile-time safety, better tooling, erased types at runtime                       |
| React Integration | `e` is untyped, runtime only | Strongly typed events, `React.ChangeEvent<HTMLInputElement>`, etc.                 |

## 6. Why TypeScript Exists

TypeScript gives you:

- Early error detection before running code.
- Confidence when refactoring large codebases.
- Better developer experience with autocompletion and navigation.
- Scalability for teams with clear type contracts.
  And crucially — none of these features change the runtime behavior. The output is always plain JavaScript.

## 7. Mental Model

Think of TypeScript as a translator and enforcer:

```css
[ TypeScript Code + Types ]
             ↓
   Compiler removes types
             ↓
     [ Plain JavaScript ]
             ↓
        Runs in browser/Node
```
