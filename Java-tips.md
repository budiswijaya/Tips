## Golden rule and tips

### JavaScript Basics:
Variables: Store information.
```js
let message = "Hello!";
```

Functions: Block of code that runs when called.
```js
function greet() { alert("Hi!"); }
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

### Character Encoding

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
console.log(char);  // Output: A
```

### Number Systems

- **Binary**: Base-2 (0,1) with 8 digits
- **Hexadecimal**: Base-16 (0-9, A-F) with 2 digits
- **Decimal**: Base-10 (0-9) with values 0-127
- **Octal**: Base-8 (0-7) with 3 digits

```
Example below:
    A in ASCII value is 65 Decimal Value / 41 Hexadecimal Value / 101 Octal Value and lastly is
    01000001 Binary Value that can be convert to Decimal Value
     0   1   0   0  0   0   0   1 = A in Binary value
    128	64	32	16	8	4	2	1 = each binary position formula
     0  64   0   0  0   0   0   1 = Total value is 65 Decimal Value

    *Note: other types can also be convert vice versa
```

### Variable Naming Conventions

- Variable names should be descriptive and meaningful.
- Variable names should be camelCase like cityName, isLoggedIn, and veryBigNumber.
- Variable names should not start with a number. They must begin with a letter, _, or $.
- Variable names should not contain spaces or special characters, except for _ and $.
- Variable names should not be reserved keywords.
- Variable names are case-sensitive. age and Age are different variables.

```js
let isLoading = true;
let hasPermission = false;
let canEdit = true;

function getUserData(){
  /* ... */
}
function calculateTotal(){
  /* ... */
}
function validateInput(){
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
}function handleClick(){
  /* ... */
}
function onSubmit(){
  /* ... */
}
function keyPressHandler(){
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

### Variable Declarations

There are three main ways to declare variables:

- **const** - For values that won't change
- **let** - For variables that can change, but not globally
- **var** - For variables that can change globally (not recommended in modern JS)

There are also other keyway manipulation methods:

- **function** - For function declarations
- **delete** - To delete a variable or property
- **new** - For creating objects with constructors
- **class** - For class declarations
- **interface** - For interface declarations

### String Manipulation

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

### Console.logging for debugging

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

## Object Manipulation

### Braces in JavaScript

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
console.log(greeting[greeting.length - 1]); // Output: "o"
```

### Object Manipulation Structure Levels

Accessing nested object data:

```js
const person = {
  name: "Alice",
  age: 30,
  contact: {
    email: "alice@example.com",
    phone: {
      home: "123-456-7890",
      work: "098-765-4321"
    }
  }
};

console.log(person.name);                   // Alice
console.log(person["age"]);                 // 30
console.log(person.contact.phone.work);     // "098-765-4321"
```

Object property operations:

- Add properties: `person.job = "Engineer"` or `person["hobby"] = "Knitting"`

```js
person.job = "Engineer"
person["hobby"] = "Knitting"
console.log(person);        
// {name: 'Alice', age: 30, job: 'Engineer', hobby: 'Knitting'}
```

- Delete properties: `delete person.job`

```js
delete person.job;
console.log(person.job);                    // undefined
```

- Check if property exists: `"name" in person`

```js
console.log("name" in person);              // true
```

- Checks if an object has a specific property: `.hasOwnProperty()`

```js
const person = {
    name: "Alice",
    age: 30
};

console.log(person.hasOwnProperty("name")); // true
console.log(person.hasOwnProperty("job"));  // false
```

- Check if an object has a specific property as its own property, it's directly defined on the object and not inherited from its prototype chain.
    
    **Why `Object.hasOwn()` is preferred over `Object.prototype.hasOwnProperty()`:**
    
    **Handles objects created with `Object.create(null)`:** `hasOwnProperty()` fails on objects created with `Object.create(null)` because they do not inherit from `Object.prototype`, and therefore, `hasOwnProperty` is not available on them. `Object.hasOwn()` works correctly in this scenario.
    

```js
const obj1 = { a: 1 };
console.log(Object.hasOwn(obj1, 'a')); // true
console.log(Object.hasOwn(obj1, 'b')); // false

const obj2 = Object.create(null);
obj2.c = 3;
console.log(Object.hasOwn(obj2, 'c')); // true
// console.log(obj2.hasOwnProperty('c')); // Throws an error
```

### Natural Hierarchical Structure Levels in Different Variable Declarations {Classification}

Single level, no structure.

```js
const name = "John";                // Single level, no structure
let age = 25;                       // Single level, no structure
var score = 100;                    // Single level, no structure
```

It doesn't matter how you call the identifier or classification as long as clear on structure.

```js
const recordCollection = {         // This is main (records) object
     5439: {                       // This is a key (id) in the main object
        albumTitle: 'ABBA Gold',   // (props) of the id object and "(value)" within
        artist: '',                // (props) of the id object and "(value)" within
        tracks: []                 // (props) of the id object and "(value)" within
    }
}

function updateRecords(records,id,prop,value){
    if(!records[id]){
        return records }
    if(value === ""){
        delete records[id][prop]}
    else
    records[id][prop] = value;
    return records ;
}

console.log(updateRecords(recordCollection, 5439, "artist", "ABBA"));
//                         ^records          ^id    ^prop     ^value
```

Example of well-identified object structure

```js
const students = {
    STU_001: {              // Identifier with clear prefix
        name: "John",       // Property with string value
        grades: [90, 85],   // Property with array value
        active: true        // Property with boolean value
    }
};
```

Numeric identifier style

```js
const records = {
    2548: {                 // Numeric identifier
        albumTitle: "...",  // String property
        tracks: []          // Array property
    }
};
```

More explicit classification

```js
const inventory = {
    itemId: {                           // Named identifier
        type: "product",                // Classification property
        metadata: {                     // Nested classification
            category: "electronics",
            subCategory: "phones"
        }
    }
};
```

E-commerce System

```js
const ecommerceSystem = {
    STORE_001: {                        // Level 1: Store ID
        details: {                      // Level 2: Store Details
            name: "Main Branch",
            location: {                 // Level 3: Location Details
                street: "123 Main St",
                city: "Boston",
                zip: "02108"
            }
        },
        inventory: {                    // Level 2: Inventory
            products: [                 // Level 3: Product List
                {                       // Level 4: Product Details
                    id: "P001",
                    name: "Laptop",
                    specs: {            // Level 5: Product Specifications
                        brand: "Dell",
                        model: "XPS"
                    }
                }
            ]
        }
    }
};
```

School Management System

```js
const schoolSystem = {
    departments: {                                  // Level 1: Department Structure
        "DEPT_001": {                               // Level 2: Department ID
            name: "Computer Science",
            courses: {                              // Level 3: Course Structure
                "CS101": {                          // Level 4: Course Details
                    title: "Intro to Programming",
                    students: [                     // Level 5: Student List
                        {                           // Level 6: Student Details
                            id: "STU_001",
                            grades: {
                                midterm: 95,
                                final: 88
                            }
                        }
                    ]
                }
            }
        }
    }
};
```

File System Structure

```js
const fileSystem = {
    root: {                                         // Level 1: Root Directory
        documents: {                                // Level 2: Subdirectory
            work: {                                 // Level 3: Nested Directory
                files: [                            // Level 4: File List
                    {                               // Level 5: File Details
                        name: "report.doc",
                        metadata: {
                            size: "1.2MB",
                            created: "2023-01-01",
                            type: "document"
                        }
                    }
                ]
            }
        }
    }
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
    city: "Somewhere"
    }
}
};
console.log(user.profile?.address?.street); // "123 Main St"
console.log(user.profile?.phone?.number);   // undefined

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
const numObj = Object(num);     // Creates an object wrapper for the number
console.log(numObj);            // 42
console.log(typeof numObj);     // "object"

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

console.log(toObject(null));        // {}
console.log(toObject(true));        // {}
console.log(toObject([1, 2, 3]));   // [1, 2, 3]

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
console.log(age);  // 30
```

### Array Constructors

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
console.log(new Array(3));     // [empty × 3] (length=3)
console.log(new Array("3"));   // ["3"] (length=1)

/*If the only argument is a number, it sets the length.
Otherwise, treats arguments as elements.*/
```

Summary
- new Array(): Creates arrays flexibly but can be tricky.
- Literal []: Simpler, safer, and more readable.
- Sparse arrays: Useful for memory pre-allocation but behave unexpectedly in methods like map().

Use the constructor only when you specifically need its unique behavior. Otherwise, stick with []. 🚀


### JSON

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
    isAdmin: true
};

const jsonString = JSON.stringify(user);
console.log(jsonString);

// Output:
'{"name":"John","age":30,"isAdmin":true}'
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

### Array Methods

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
const found = numbers.find(num => num > 10); 
console.log(found); // Output: 12

// Returns 12 as it's the first number greater than 10.
```

- **findIndex()** - Returns the index of the first element that satisfies a condition

```js
const numbers = [5, 12, 8, 130, 44]; 
const foundIndex = numbers.findIndex(num => num > 10); 
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
const words = ['spray', 'limit', 'elite', 'exuberant']; 
const result = words.filter(word => word.length > 5); 
console.log(result); // Output: ["exuberant"]

// Returns only words with more than 5 characters.
```

- **reduce()** - Reduces array to a single value by executing a functio

```js
const numbers = [1, 2, 3, 4]; 
const sum = numbers.reduce((accumulator, currentValue) => accumulator + currentValue, 0); 
console.log(sum); // Output: 10

// Adds all numbers together, starting with initial value 0.
```

- **sort()** - Sorts elements of an array in place

```js
const fruits = ['banana', 'cherry', 'apple']; 
fruits.sort(); 
console.log(fruits); // Output: ['apple', 'banana', 'cherry']

// Sorts alphabetically by default.
```

- **reverse()** - Reverses the order of elements in an array

```js
const numbers = [1, 2, 3, 4, 5]; numbers.reverse(); 
console.log(numbers); // Output: [5, 4, 3, 2, 1]

// Reverses the array in place.
```

**Combining/Splitting**

- **concat()** - Joins arrays together

```js
const array1 = ['a', 'b']; 
const array2 = ['c', 'd']; 
const array3 = array1.concat(array2); 
console.log(array3); // Output: ['a', 'b', 'c', 'd']

// Returns a new array combining both arrays.
```

- **slice()** - Returns a shallow copy of a portion of an array

```js
const fruits = ['apple', 'banana', 'orange', 'mango']; 
const citrus = fruits.slice(1, 3); 
console.log(citrus); // Output: ['banana', 'orange']

// Returns elements from index 1 to 2 (end index is exclusive).
```

- **join()** - Joins all elements into a string

```js
const elements = ['Fire', 'Water', 'Air']; 
console.log(elements.join()); // Output: "Fire,Water,Air" 
console.log(elements.join('-')); // Output: "Fire-Water-Air"

// Joins with commas by default or with specified separator.
```

- **split()** - Splits a string into an array (string method, not array method)

```js
const str = 'The quick brown fox'; 
const words = str.split(' '); 
console.log(words); // Output: ["The", "quick", "brown", "fox"]

// Splits the string at each space.
```

**Adding/Removing Elements**

- **pop()** - Removes the last element from an array

```js
const plants = ['broccoli', 'cauliflower', 'kale']; 
const removed = plants.pop(); 
console.log(plants); // Output: ['broccoli', 'cauliflower'] 
console.log(removed); // Output: 'kale'

// Removes and returns the last element.
```

- **push()** - Adds elements to the end of an array

```js
const animals = ['pigs', 'goats']; 
const count = animals.push('cows'); 
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
const months = ['Jan', 'March', 'April', 'June']; 
months.splice(1, 0, 'Feb');     // Insert at index 1 
console.log(months);            // Output: ['Jan', 'Feb', 'March', 'April', 'June'] 

months.splice(4, 1, 'May');     // Replace element at index 4 
console.log(months);            // Output: ['Jan', 'Feb', 'March', 'April', 'May']

// The first parameter is the start index, second is delete count, rest are items to add.
```

**Checking Elements**

- **every()** - Tests whether all elements pass a test

```js
const numbers = [1, 30, 39, 29, 10, 13]; 
const allBelow40 = numbers.every(num => num < 40); 
console.log(allBelow40); // Output: true

// Returns true because every number is less than 40.
```

- **some()** - Tests whether at least one element passes a test

```js
const numbers = [1, 2, 3, 4, 5]; 
const hasEven = numbers.some(num => num % 2 === 0); 
console.log(hasEven); // Output: true

// Returns true because at least one number is even.
```

**Basic String Access Methods:**

- **charAt()** - Returns the character at a specified index

```js
let str = "Hello"; console.log(str.charAt(0)); // Output: "H"
```

- **Get last character** - Using array notation with length property

```js
let str = "Hello"; console.log(str[str.length - 1]); // Output: "o"
```

**String Manipulation Methods:**

- **replace()** - Replaces the first occurrence of a specified value

```js
let text = "Hello world"; console.log(text.replace("world", "universe")); // Output: "Hello universe"
```

- **repeat()** - Returns a new string with a specified number of copies

```js
let word = "Hi"; console.log(word.repeat(2)); // Output: "HiHi"
```

- **trim()** - Removes whitespace from both ends of a string=

```js
let text = " Hello "; console.log(text.trim()); // Output: "Hello"
```

- **trimStart()/trimEnd()** - Removes whitespace from beginning/end of string

```js
let text = " Hello "; console.log(text.trimStart()); // Output: "Hello "
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
let text = "Hello world"; console.log(text.indexOf("world")); // Output: 6
```

- **lastIndexOf()** - Returns the position of the last occurrence of a value

```js
let text = "Hello world world"; console.log(text.lastIndexOf("world")); // Output: 12
```

- **includes()** - Returns true if a string contains a specified value

```js
let text = "Hello world"; console.log(text.includes("world")); // Output: true
```

**Case Conversion Methods:**

```js
let text = "Hello"; console.log(text.toUpperCase()); // Output: "HELLO"
```

- **toLowerCase()** - Converts a string to lowercase

```js
let text = "Hello"; console.log(text.toLowerCase()); // Output: "hello"
```

**Substring Methods:**

- **substring()** - Extracts characters between two indices

```js
let text = "Hello world"; console.log(text.substring(0, 5)); // Output: "Hello"
```

- **slice()** - Extracts a part of a string and returns a new string

```js
let text = "Hello world"; console.log(text.slice(6)); // Output: "world"
```

## Operator

### Arithmetic Operators

Used for mathematical calculations:

- (+) (Addition): Adds numbers or concatenates strings
```js
`let sum = 5 + 3;` // 8
`let text = "Hello" + " World";` // "Hello World"
```

- (-) (Subtraction): Subtracts numbers
```js
`let difference = 10 - 5;` // 5
```

- (*) (Multiplication): Multiplies numbers
```js
`let product = 4 * 3;` // 12
```

- (/) (Division): Divides numbers
```js
`let quotient = 15 / 3;` // 5
```

- (%) (Modulus): Returns the division remainder
```js
`let remainder = 10 % 3;` // 1
```
### Assignment Operators

Used to assign values to variables:

- (=:) Basic assignment
```js
`let x = 10;`
```

- (+=) Addition assignment
```js
`let y = 5; y += 3;` // Same as y = y + 3 (y becomes 8)
```

- (-=) Subtraction assignment
```js
`let z = 10; z -= 4;` // Same as z = z - 4 (z becomes 6)
```

- (*=) Multiplication assignment
```js
`let a = 3; a *= 2;` // Same as a = a * 2 (a becomes 6)
```

- (/=) Division assignment
```js
`let b = 8; b /= 2;` // Same as b = b / 2 (b becomes 4)
```

- (%=) Modulus assignment
```js
`let c = 7; c %= 2;` // Same as c = c % 2 (c becomes 1)
```

### Comparison Operators

Used to compare values:

- (==) Loose equality: It does check type but more emphasis on the value, so it performs type coercion, converting values to the same type before comparing them.
```js
`5 == "5"` // true (string is converted to number)
```

- (===) Strict equality: It checks both value and type, providing more precise, strict, predictable results.
```js
`5 === "5"` // false (different types)
```

```js
console.log('5' == 5); // true

/*Step 1: Types differ (string vs num ber)
Step 2: Convert string '5' to number 5  
Step 3: Compare 5 == 5
Step 4: Result is true (they're equal after conversion)*/

console.log('5' === 5); // false

/*Step 1: Types differ (string vs number)
Step 2: Return false immediately (different types = not equal)*/
```

- (!=) Loose inequality: It does check type but more emphasis on the value, so it performs type coercion, converting values to the same type before comparing them.
```js
`5 != "6"` // true
```

- (!==) Strict inequality: It checks both value and type, providing more precise, strict, predictable results.
```js
`5 !== "5"` // true (different types)
```

```js
console.log('5' != 5); // false

/*Step 1: Types differ (string vs number)
Step 2: Convert string '5' to number 5  
Step 3: Compare 5 != 5
Step 4: Result is false (they're equal after conversion)*/

console.log('5' !== 5); // true

/*Step 1: Types differ (string vs number)
Step 2: Return true immediately (different types = not equal)*/
```

- (>) (Greater than): Checks if left value is greater
```js
`10 > 5` // true
```

- (<) (Less than): Checks if left value is smaller
```js
`5 < 10` // true
```

- (>=) (Greater than or equal): Checks if left value is greater or equal
```js
`5 >= 5` // true
```

- (<=) (Less than or equal): Checks if left value is smaller or equal
```js
`5 <= 10` // true
```

### Logical Operators

Used to determine logic between variables or values:

- (&&) AND: Returns true if both operands are true
```js
`true && true` // true
`true && false` // false
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
`true || false` // true
`false || false` // false
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
`!true` // false
`!false` // true
```

```js
// Basic boolean negation
console.log(!true);     // false
console.log(!false);    // true

// The NOT operator converts non-boolean values to boolean first, then negates
console.log(!"Hello");  // false (string is truthy, so !truthy becomes false)
console.log(!"");       // true (empty string is falsy, so !falsy becomes true)

// Useful for checking empty values
const username = "";
if (!username) {
  console.log("Username is required!");  // This will execute
}

// Double negation (!!) can be used to convert a value to boolean
console.log(!!0);       // false
console.log(!!"text");  // true
console.log(!!null);    // false
console.log(!!undefined); // false

// Using NOT in conditions
const isLoggedIn = false;
if (!isLoggedIn) {
  console.log("Please log in first!");  // This will execute
}
```

### Other Important Operators

- **Ternary operator (?:)**: Shorthand for if-else statements ? expression if true : expression if false
```js
`let status = (age >= 18) ? "Adult" : "Minor";`
```

```js
const isLoggedIn = true;
const msg = isLoggedIn ? "Welcome back!" : "Please log in."
console.log(msg); // Welcome back!

const weather = temperature > 25 ? 'sunny' : 'cool';
console.log(`It's a ${weather} day!`); // It's a sunny day!

let fortune1 = "Your cat will look very cuddly today.";
let fortune2 = "The weather will be nice tomorrow.";
let fortune3 = "Be cautious of your new neighbors.";
let fortune4 = "You will find a new hobby soon.";
let fortune5 = "It would be wise to avoid the color red today.";
let min = 1;
let max = 5;
let randomNumber = Math.round(Math.random()*(max-min)+min);
let selectedFortune = randomNumber == 1 ? fortune1 : 
                    randomNumber == 2 ? fortune2 : 
                    randomNumber == 3 ? fortune3 : 
                    randomNumber == 4 ? fortune4 :
                    fortune5 ;
                        
console.log(selectedFortune);
```

- **?.** (Optional chaining): Safely access nested properties or call methods without worrying wether they exist. It’s like a safety net for working with objects that might have missing parts.
```js
`user.profile?.address?.street` // Returns undefined if any property in chain is null/undefined
```

```js
const user = {
name: "John",
profile: {
    email: "john@example.com",
    address: {
    street: "123 Main St",
    city: "Somewhere"
    }
}
};
console.log(user.profile?.address?.street); // "123 Main St"
console.log(user.profile?.phone?.number);   // undefined

    /*By using the optional chaining operator, we are telling JavaScript to only continue with the operation if the object (or the value before the ?.) exists and is not null or undefined. If the value before the ?. is null or undefined, JavaScript returns undefined rather than attempting to proceed with the operation and throwing an error.*/
```

- **??** (Nullish coalescing): Return a value only if the first one is null or undefined.
```js
`let username = null ?? "Anonymous";` // "Anonymous"
```

```js
const result = null ?? 'default';
console.log(result); // default

const userSettings = {
	theme: null,
	volume: 0,
	notifications: false,
};

let theme = userSettings.theme ?? 'light';
console.log(theme); // light
```

- **...** (Spread): Expands an iterable (like an array or string) into individual elements.
```js
`let newArray = [...oldArray, newItem];`
```

```js
let originalArray = [1, 2, 3];
let copyArray = [...originalArray];

console.log(copyArray); // [1, 2, 3]
console.log(copyArray === originalArray); // false
```

- ** (Exponentiation): is right-to-left associative/precedence. Same as x^2 or x² in mathematical notation.

```js
const result = 2 ** 3 ** 2;
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

- Bitwise Operators (&, |, ^, ~, <<, >>)

(&) bitwise AND operator returns a 1 in each bit position for which the corresponding bits of both operands are 1.
```js
    let a = 5;  // Binary: 101
    let b = 3;  // Binary: 011
    console.log(a & b);  // Output: 1 (Binary: 001)
```

(|) bitwise OR operator returns a 1 in each bit position for which the corresponding bits of either or both operands are 1.
```js
    let a = 5;  // Binary: 101
    let b = 3;  // Binary: 011
    console.log(a | b);  // Output: 7 (Binary: 111)
```

(^) bitwise XOR operator returns a 1 in each bit position for which the corresponding bits of either, but not both, operands are 1.
```js
    let a = 5;  // Binary: 101
    let b = 3;  // Binary: 011
    console.log(a ^ b);  // Output: 6 (Binary: 110)
```

(~) bitwise NOT operator inverts all the bits of its operand.
```js
    let a = 5;  // Binary: 101
    console.log(~a);  // Output: -6
```

(<<) left shift operator shifts all bits to the left by a specified number of positions. 
```js
    let a = 5;  // Binary: 101
    console.log(a << 1);  // Output: 10 (Binary: 1010)
```

(>>) right shift operator shifts all bits to the right.
```js
    let a = 5;  // Binary: 101
    console.log(a >> 1);  // Output: 2 (Binary: 10)
```

- Unary operators (+, -, !, ~, .void, typeof)
Act on a single operand to perform operations like type conversion, value manipulation, or checking certain conditions.

(+) unary plus operator converts its operand into a number. 
If the operand is already a number, it remains unchanged.
```js
    const str = '42';
    const strToNum = +str;

    console.log(strToNum); // 42
    console.log(typeof str); // string
    console.log(typeof strToNum); // number
```

(-) unary negation operator negates the value of the operand. 
```js
    const str = '42';
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

(.void) unary operator that evaluates an expression and returns undefined.
```js
    const result = void (2 + 2);
    console.log(result); // undefined

    <a href="javascript:void(0);">Click Me</a> // commonly used in hyperlinks HTML
```

(typeof) is used to determine the type of a variable.
```js
    let num = 42;
    console.log(typeof num); // "number"
```

## Data Types

Primitive Data Types: These data types include numbers, strings, booleans, null, undefined, and symbols. These types are called "primitive" because they represent single values and are not  objects. Primitive values are immutable, which means once they are created, their value cannot be changed. 

Non Primitive Data Types: In JavaScript, these are objects, which include regular objects,
arrays, and functions. Unlike primitives, non-primitive types can hold multiple values as properties or elements.

- **string** - Text in quotes ("Hello" or 'Hello')
- **number** - Numeric values (1, 3.14)
- **boolean** - true/false values
- **array** - Collections of items [1, 2, 3]
- **object** - Key-value pairs { name: "John" }

```js
//Example below:
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
const notANumber = 'hello world' / 2;
console.log(notANumber); // NaN
```

- (-1) it means negative infinity or not found
```js
console.log("freeCodeCamp".indexOf("F")) // -1
```

### Data type identifier

- Function similar to typeof but more precise and easy to use
```js
const isString = (val) => typeof val === 'string'
const isNumber = (val) => typeof val === 'number' && !isNaN(val)
const isObject = (val) => val !== null && typeof val === 'object' && !Array.isArray(val)
const isFunction = (val) => typeof val === 'function'
const isDate = (val) => val instanceof Date && !isNaN(val)
```

- .isNaN() function property is used to determine whether a value is NaN or not
```js
console.log(isNaN(NaN));       // true
console.log(isNaN(undefined)); // true
console.log(isNaN({}));        // true
console.log(isNaN(true));      // false
console.log(isNaN(null));      // false
console.log(isNaN(37));        // false
console.log(isNaN("37"));      // false: "37" is converted to 37
console.log(isNaN("37.37"));   // false: "37.37" is converted to 37.37
console.log(isNaN(""));        // false: empty string is converted to 0
console.log(isNaN(" "));       // false: string with a space is converted to 0
console.log(isNaN("shit"));    // true: "shit" is not a number
```

Due to these potential inconsistencies, ES6 introduced Number.isNaN(). This method does not attempt to convert the parameter to a number before testing. It only returns true if the value is exactly NaN:
```js
console.log(Number.isNaN(NaN));        // true
console.log(Number.isNaN(Number.NaN)); // true
console.log(Number.isNaN(0 / 0));      // true

console.log(Number.isNaN("NaN"));      // false
console.log(Number.isNaN(undefined));  // false
console.log(Number.isNaN({}));         // false
console.log(Number.isNaN("shit"));   // false
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

console.log(divide(10, 2));  // 5
console.log(divide(10, 0));  // Infinity
console.log(divide(0, 0));   // "Error: Division resulted in NaN"
```

### Type Conversion

Converting between types:

- `parseFloat()` - String to decimal number
- `parseInt()` - String to integer

Are two essential methods in JavaScript for converting strings to numbers. 
parseFloat() converts a string to a floating-point number. Floating-point is a number with a decimal point.
parseInt() converts a string to an integer. Integer is a whole number without a decimal point.
These methods are particularly useful when dealing with user input or 
processing data that comes in string format but needs to be treated as numerical values.
```js
console.log(parseFloat("3.14"));     // Output: 3.14
console.log(parseFloat("3.14 abc")); // Output: 3.14
console.log(parseFloat("3.14.5"));   // Output: 3.14
console.log(parseFloat("abc 3.14")); // Output: NaN
console.log(parseFloat("  3.14"));   // Output: 3.14
console.log(parseFloat("+3.14"));    // Output: 3.14

console.log(parseInt("42"));       // Output: 42
console.log(parseInt("42px"));     // Output: 42
console.log(parseInt("3.14"));     // Output: 3
console.log(parseInt("abc123"));   // Output: NaN
console.log(parseInt("-42"));      // Output: -42
console.log(parseInt("  42"));     // Output: 42
```

- `Number()` - Converts to number
```js
Number("5")      // Returns: 5 (number)
Number("hello")  // Returns: NaN (Not a Number)
Number("3.14")   // Returns: 3.14 (number)
Number(true)     // Returns: 1 (number)
Number(false)    // Returns: 0 (number)
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
const obj2 = Number({2: 2});
const obj3 = Number({key: "val"});
const obj4 = Number({key: true});

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
console.log(num.toFixed(3));  // Output: "3.142"

let num = 5.678;
console.log(num.toFixed(1)); // Output: "5.68"

let price = 19.99;
let taxRate = 0.08;
let total = price + (price * taxRate);
console.log("Total: $" + total.toFixed(2)); // Output: "Total: $21.59"
```

- (+) unary plus operator converts its operand into a number. 
If the operand is already a number, it remains unchanged.
```js
const str = '42';
const strToNum = +str;

console.log(strToNum); // 42
console.log(typeof str); // string
console.log(typeof strToNum); // number
```

- (-) unary negation operator negates the value of the operand. 
```js
const str = '42';
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

The meaning it's just number system convertion that use in computer. There are 4 option:
- toString(2) - Binary: Base-2 (0,1) with 8 digits
- toString(16) - Hexadecimal: Base-16 (0-9, A-F) with 2 digits
- toString(10 - Decimal: Base-10 (0-9) with values 0-127
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
const result = '10' + 5;
console.log(result); // 105
console.log(typeof result); // string

// When you try to perform other arithmetic operations like subtraction, multiplication, or division with a string and number. 
//All other operators (-, *, /, %) convert to numbers
const subtractionResult = '10' - 5;
console.log(subtractionResult); // 5
console.log(typeof subtractionResult); // number

const multiplicationResult = '10' * 2;
console.log(multiplicationResult); // 20
console.log(typeof multiplicationResult); // number

const divisionResult = '20' / 2;
console.log(divisionResult); // 10
console.log(typeof divisionResult); // number

//But what if the string doesn't look like a number? 

const subtractionResult = 'abc' - 5;
console.log(subtractionResult); // NaN
console.log(typeof subtractionResult); // number

const multiplicationResult = 'abc' * 2;
console.log(multiplicationResult); // NaN
console.log(typeof multiplicationResult); // number

const divisionResult = 'abc' / 2;
console.log(divisionResult); // NaN
console.log(typeof divisionResult); // number

// (Special Case)
true + true         // 2 (true = 1)
false * 5           // 0 (false = 0)
null + 5            // 5 (null = 0)
undefined + 5       // NaN
null == undefined   // true (Special Rule)
NaN == NaN          // false (Always!)
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
    console.log(null == 0);  // false
    console.log(null == ''); // false
    console.log(undefined == 0); // false
    console.log(undefined == ''); // false
    console.log(null > 0);  // false
    console.log(null == 0); // false
    console.log(null >= 0); // true
    console.log(undefined > 0);  // false
    console.log(undefined < 0);  // false
    console.log(undefined == 0); // false

/* Given these nuances, it's generally recommended to use the strict equality operator when comparing values, especially when dealing with null and undefined. This approach helps avoid unexpected type coercion and makes your code's behavior more predictable.

In summary, while null and undefined are both used to represent the absence of a value, they behave differently in comparisons. Understanding these differences is key to 
writing clear and error-free JavaScript code.*/
```

### Math Operations

Common math methods:

- `Math.random()` - Generate random number between 0 (inclusive) and 1 (exclusive). This means the possible output can be 0, but it will never actually reach 1.
```js
const randomNum = Math.random();
console.log(randomNum); 
// any number between 0 and 1 – 0 inclusive and 1 exclusive
```

- `Math.min()/Math.max()` - Both take a set of numbers and return the minimum and maximum value, respectively.
```js
const smallest = Math.min(1, 5, 3, 9);
console.log(smallest); // 1

const largest = Math.max(1, 5, 3, 9);
console.log(largest); // 9
```

- `Math.ceil()/Math.floor()` - To round numbers up or down to the nearest whole integer
```js
console.log(Math.ceil(4.3)); // 5
console.log(Math.floor(4.7)); // 4
```

- `Math.round()` - Round to nearest integer
```js
console.log(Math.round(2.3)); // 2
console.log(Math.round(4.5)); // 5
console.log(Math.round(4.8)); // 5
```

A practical application of Math.floor() and Math.random() is 
to generate a random number between two whole numbers. 
```js
const randomNumBtw1And20 = Math.floor(Math.random() * 20) + 1;
console.log(randomNumBtw1And20); 
```

- `Math.trunc()` - Remove decimal portion
```js
console.log(Math.trunc(2.9)); // 2
console.log(Math.trunc(9.1)); // 9
```

- `Math.sqrt()/Math.cbrt()` - Square (x√x) / cube (∛) root
```js
console.log(Math.sqrt(81)); // 9
console.log(Math.cbrt(27)); // 3
```

- `Math.abs()` - Absolute value
```js
  console.log(Math.abs(-5)); // 5
  console.log(Math.abs(5)); // 5
```

- `Math.pow()` - Takes two numbers and raise the first to the power of the second
```js
console.log(Math.pow(2, 3)); // 8
console.log(Math.pow(8, 2)); // 64
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

## Closure

Definition: A function that remembers and accesses variables from its outer (enclosing) scope, even after the outer function has finished executing.

Requires:
- A nested function.
- Reference to an outer variable.

Closures are one of the most powerful and often misunderstood features in JavaScript. At its core, a closure is a function that has access to variables in its outer enclosing lexical scope, even after the outer function has returned. This might sound complex but it's a fundamental concept that enables many advanced programming patterns in JavaScript.

```js
function outerFunction(x) {
    let y = 10;
    function innerFunction(){
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


## Logical / Reasoning Method

### Functions

Functions are reusable pieces of code that perform a specific task or calculate a value. 
Think of functions as a machine that takes some input, does some operations on it, and 
then produces an output. Functions can be called by their name, and they can take parameters.

Different ways to define functions:

Function declaration:
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

=> Arrow functions

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
const greetings = name => {
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
const greetings = name => console.log("Hello, " + name + "!");
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

### Control Flow

**if/else statements**:

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
const marks = 85
if (marks >= 90) {
    console.log("Grade: A")
    } else if (marks >= 80) {
    console.log("Grade: B")
    } else if (marks >= 70) {
    console.log ("Grade: C")
    } else if (marks >= 60) {
    console.log("Grade: D")
    }
  
// Results below:
Grade: A
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
    if (sentence.trim() === '') {
        return 0;
    }

const words = sentence.trim().split(/\s+/);
return words.length;
}

const wordCount  = getWordCount ("I love freeCodeCamp");
console.log(`Word Count: ${wordCount}`);                  // Word Count: 3
```

**switch statements**:

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

### Loops

**"i" as the loop variable recognized by every programmer, stands for "index" or "iterator")**

### **Synonym for "Iterable"**

You can think of it as:

- **"Loop-able"** (can be used in loops)
- **"Sequence-able"** (has an order of elements)
- **"Traversable"** (you can go through its items one by one)

### **Real-World Analogy**

Imagine:

- **Iterable** = A **bookshelf** (you can scan each book one by one).
- **Non-iterable** = A **single book** (you can’t "loop through" a standalone book).

**Strings are like bookshelves of characters. Numbers/booleans are single books.**

Different types of loops for iteration:

**1. Primary Loop Structures**

- **for loop** - When you know how many iterations needed , processing arrays, need a counter.

```js
for (initialization; condition; increment or decrement) {
    *code block to be executed
}
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
Iteration: 0
Iteration: 1
Iteration: 2
Iteration: 3
Iteration: 4
Iteration: 5
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
I = 0
color[i] = red
I = 1
color[i] = green
I = 2
color[i] = blue
I = 3
color[i] = yellow
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

while (count <= 5){
console.log("count =", count);
count++;
}
    /*Explanation:
    count value is 0
    count <= 5 means count is less than or equal to 5 so there is 5 arrays (1,2,3,4,5)
    count++ there means is increased by 1 each time, so the loop will run 5 times
    so if there is no count++ it will continue to loop until the condition is false*/

//Results below:
count = 0
count = 1
count = 2
count = 3
count = 4
count = 5
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
number =  0
number =  1
number =  2
number =  3
number =  4
number =  5
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

**2. Specialized Loops**

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
Apple
Banana
Cherry
```

```js
// Example below:
const str = 'free';

for (let char of str) {
    console.log(char);
}

// Results below:
f
r
e*2
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
    name: 'apple',
    color: 'red',
    price: 0.99
};

for (const prop in fruit) {
    console.log(fruit[prop]);
}

//Results below:
apple
red
0.99
```

```js
const person = {
    name: 'John',                   // First level (In fact it's already an Object)
    age: 30,
    address: {
        street: '123 Main St',      // Second level (It's object within object)
        city: 'Anytown',
        state: 'CA'
    }
};

for (const prop in person) {
    console.log(person[prop]);
}

//Results below:
John
30
>{street: `123 Main St`, city: `Anytown`, state: `CA`} // Click to open the object

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
const fruits = ['apple', 'banana', 'orange'];

for (const index in fruits) {
    console.log(index);                                 // "0", "1", "2" (strings!)
    console.log(fruits[index]);                         // apple, banana, orange
}
        //❌ for...in (NOT recommended)

for (const fruit of fruits) {
    console.log(fruit);                               // apple, banana, orange (direct values)
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
array.forEach(function(currentValue, index, array) {
  // code to execute for each element
});
```

```js
const sparseArray = [1, , 3];
sparseArray.forEach(item => console.log(item));
// Output:
// 1
// 3
// Performs the callback function on each element without returning anything.
```
Practical Use Cases
1. Modifying original array
```js
const buttons = document.querySelectorAll('button');
buttons.forEach(button => {
  button.addEventListener('click', handleClick);
});
```
2. DOM manipulation
```js
const buttons = document.querySelectorAll('button');
buttons.forEach(button => {
  button.addEventListener('click', handleClick);
});
```
3. Object iteration (with conversion)
```js
const person = {name: 'John', age: 30, job: 'developer'};
Object.keys(person).forEach(key => {
  console.log(`${key}: ${person[key]}`);
});
```

**Loop Control**

A break statement is used to exit a loop early, while a continue statement is used to skip the current iteration of a loop and move to the next one.
`break` - Exit loop early

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

Outer Loop and Inner Loop

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
"i: 0, j: 0"
"i: 0, j: 1"
"i: 0, j: 2"
"i: 1, j: 0"

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
    fibonacci.push(fibonacci[i-1] + fibonacci[i-2]); 
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
~ For scope decisions: Use the original 1 to 4 category model
~ For algorithm design: Use the expanded 1 to 8 category model
~ For performance optimization: Consider loop type (e.g., while vs for)
All loop applications ultimately fall into two fundamental patterns:
~ Stateful loops: Require outer scope (accumulation, state machines)
~ Stateless loops: Work with inner scope (transformation, side effects)

Key Insight
The classification answers:
~ When to "remember" state (outer scope for accumulation).
~ When to isolate (inner scope for independent operations).
~ When scope doesn’t drive the logic (side effects).
This framework helps choose the right scope strategy for your loop’s purpose.


### DOM Manipulation
DOM (Document Object Model) manipulation is how you interact with HTML elements using JavaScript. 

1. Selecting Elements by ID (getElementById) - Finds a single element with the specified id attribute.
```js
const element = document.getElementById('id-name');
```
Example
```html
<div id="header">Welcome</div>
```
```js
const header = document.getElementById('header');
header.textContent = 'Hello World!'; // Changes text
```

2. Selecting Elements by Class (getElementsByClassName) - Finds all elements with a given class name.
```js
const elements = document.getElementsByClassName('class-name');
```
Example
```html
<p class="highlight">First</p>
<p class="highlight">Second</p>
```
```js
const highlights = document.getElementsByClassName('highlight');
highlights[0].style.color = 'red'; // Changes first element
```

3. Selecting Elements by Tag Name (getElementsByTagName) - Finds all elements with a given HTML tag (e.g., `<div>`, `<p>`).
```js
const elements = document.getElementsByTagName('div');
```
Example
```html
<div>Box 1</div>
<div>Box 2</div>
```
```js
const divs = document.getElementsByTagName('div');
divs[1].style.backgroundColor = 'blue'; // Changes second div
```

4. Query Selector (querySelector & querySelectorAll) - Finds elements using CSS-style selectors (more flexible).

| Method | Returns | Example |
|----------|----------|----------|
| querySelector()  | First matching element  | document.querySelector('.class')  |
| querySelectorAll()  | NodeList (all matches)  | document.querySelectorAll('div.highlight')  |

Examples
```js
// Single element
const button = document.querySelector('#submit-btn');

// Multiple elements
const redItems = document.querySelectorAll('.red');
redItems.forEach(item => item.style.color = 'red');
```

Summary Cheat Sheet
```js
// By ID (fastest)
document.getElementById('id');

// By Class (returns HTMLCollection)
document.getElementsByClassName('class');

// By Tag (e.g., div, p)
document.getElementsByTagName('div');

// CSS Selectors (modern)
document.querySelector('.class'); // First match
document.querySelectorAll('div.highlight'); // All matches
```