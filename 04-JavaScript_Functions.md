# JavaScript Functions: Detailed Notes

## What is a Function?
A function is a reusable block of code designed to perform a specific task. Functions are one of the fundamental building blocks in JavaScript and help organize code into logical, manageable parts.

## Purpose of Functions
- Promote code reusability
- Reduce redundancy
- Organize and structure code
- Make code easier to test and maintain
- Create abstraction by hiding implementation details
- Enable modularity in applications

## Syntax to Create a Function

```javascript
function functionName(parameter1, parameter2, ...) {
    // code to be executed
    return value; // optional
}
```

## Function Definition
The function definition (also called declaration) consists of:
- The `function` keyword
- A unique function name (follows variable naming rules)
- A list of parameters enclosed in parentheses (optional)
- A code block enclosed in curly braces `{}`

```javascript
function greet(name) {
    return "Hello, " + name + "!";
}
```

## Function Scope
- Functions create their own scope for variables
- Variables declared inside a function are local to that function
- Variables declared outside functions are globally accessible within functions
- Functions can access variables in their parent scope (closure)

```javascript
let globalVar = "I'm global";

function scopeExample() {
    let localVar = "I'm local";
    console.log(globalVar); // Accessible
    console.log(localVar);  // Accessible
}

console.log(globalVar);     // Accessible
console.log(localVar);      // Error: localVar is not defined
```

## Function Block
The function block is the code enclosed within curly braces `{}` that executes when the function is called. It can contain any valid JavaScript statements.

## Function Call
A function call invokes the function to execute its code block. The syntax is:

```javascript
functionName(argument1, argument2, ...);
```

Example:
```javascript
let message = greet("Alice");
console.log(message); // "Hello, Alice!"
```

## Types of Functions

### Normal Function
A standard function declaration that can be called by its name.

```javascript
function multiply(a, b) {
    return a * b;
}
let result = multiply(5, 3); // 15
```

### Parameters and Arguments
- **Parameters** are variables listed in the function definition
- **Arguments** are the actual values passed to the function when called

```javascript
// x and y are parameters
function add(x, y) {
    return x + y;
}

// 5 and 3 are arguments
let sum = add(5, 3);
```

#### Parameter Features:
- Default parameters: `function greet(name = "Guest") {...}`
- Rest parameters: `function sum(...numbers) {...}`
- Destructuring parameters: `function printPerson({name, age}) {...}`

### Return
The `return` statement:
- Ends function execution
- Specifies the value to be returned
- Without a return statement, functions return `undefined`

```javascript
function square(x) {
    return x * x; // Returns the square of x
}

function logMessage(msg) {
    console.log(msg);
    // No return statement, so returns undefined
}
```

### Callback Function
A function passed as an argument to another function, to be executed later.

```javascript
function processUserInput(callback) {
    let name = prompt("Please enter your name.");
    callback(name);
}

function greeting(name) {
    console.log("Hello " + name);
}

processUserInput(greeting); // passing greeting as a callback
```

### Function Expression
Assigning a function to a variable.

```javascript
let square = function(x) {
    return x * x;
};

let result = square(5); // 25
```

### Anonymous Function
A function without a name, often used as callbacks or in function expressions.

```javascript
let numbers = [1, 2, 3, 4];
let doubled = numbers.map(function(num) {
    return num * 2;
});
// doubled: [2, 4, 6, 8]
```

### Arrow Function
A concise way to write functions using `=>` syntax.

```javascript
// Regular function
let multiply = function(x, y) {
    return x * y;
};

// Arrow function
let multiplyArrow = (x, y) => x * y;

// Arrow function with block
let checkPositive = (x) => {
    if (x > 0) return true;
    return false;
};
```

**Syntax variations:**
- `param => expression` (single parameter, implicit return)
- `(param1, param2) => expression` (multiple parameters)
- `() => expression` (no parameters)
- `param => { statements }` (block body, requires explicit return)

**Arrow function characteristics:**
- No `this` binding (inherits from parent scope)
- Cannot be used as constructors
- No `arguments` object
- Cannot use `yield` within them

### Async Function
Functions that work with promises and asynchronous operations.

```javascript
async function fetchUserData() {
    try {
        let response = await fetch('https://api.example.com/user');
        let userData = await response.json();
        return userData;
    } catch (error) {
        console.error('Error fetching user data:', error);
    }
}
```

**Key features:**
- Marked with the `async` keyword
- Can use `await` to pause execution until promises resolve
- Always return a promise
- Can be combined with arrow functions: `const getData = async () => {...}`

### Higher Order Function
A function that takes one or more functions as arguments and/or returns a function.

#### Syntax
```javascript
function higherOrderFunction(callback) {
    // Do something
    return callback();
}

// Or returning a function
function createMultiplier(factor) {
    return function(number) {
        return number * factor;
    };
}
```

#### Purpose
- Enables function composition
- Supports abstraction
- Allows for code reuse
- Foundation for functional programming patterns

#### Examples
```javascript
// Higher-order function taking a function as argument
function applyOperation(numbers, operation) {
    let result = [];
    for (let num of numbers) {
        result.push(operation(num));
    }
    return result;
}

let numbers = [1, 2, 3, 4, 5];
let doubled = applyOperation(numbers, x => x * 2);
let squared = applyOperation(numbers, x => x * x);

// Higher-order function returning a function
function createGreeter(greeting) {
    return function(name) {
        return `${greeting}, ${name}!`;
    };
}

let sayHello = createGreeter("Hello");
let sayHi = createGreeter("Hi");

console.log(sayHello("John")); // "Hello, John!"
console.log(sayHi("Alice"));   // "Hi, Alice!"
```

Common built-in higher-order functions in JavaScript:
- `Array.prototype.map()`
- `Array.prototype.filter()`
- `Array.prototype.reduce()`
- `Array.prototype.forEach()`
- `setTimeout()`
- `addEventListener()`
