# JavaScript Variables Notes

## Declaration, Assignment, and Initialization

### Declaration
Declaration is creating a variable without assigning a value.
```javascript
var name;
let age;
const PI; // Error: const declarations must be initialized
```

### Assignment
Assignment is giving a value to a previously declared variable.
```javascript
name = "John";
age = 25;
```

### Initialization
Initialization is declaring and assigning a value in a single statement.
```javascript
var name = "John";
let age = 25;
const PI = 3.14159;
```

## Scope

Scope determines where variables are accessible in your code.

```javascript
// Global scope
var globalVar = "I'm global";
let globalLet = "I'm also global";

function exampleFunction() {
  // Function scope
  var functionVar = "I'm function-scoped";
  let functionLet = "I'm also function-scoped";
  
  if (true) {
    // Block scope
    var blockVar = "I'm still function-scoped";
    let blockLet = "I'm block-scoped";
    const blockConst = "I'm also block-scoped";
    
    console.log(globalVar);      // Accessible
    console.log(functionVar);    // Accessible
    console.log(blockLet);       // Accessible
  }
  
  console.log(blockVar);         // Accessible (var ignores blocks)
  console.log(blockLet);         // Error: blockLet is not defined
}

console.log(functionVar);        // Error: functionVar is not defined
```

## Variable Keywords

### var
- Function scoped
- Can be redeclared without error
- Hoisted with initial value of `undefined`
- Can be updated

```javascript
var x = 10;
var x = 20; // No error
x = 30;     // No error

console.log(y);   // undefined (hoisted)
var y = 5;

function varExample() {
  var inside = "I'm inside";
  if (true) {
    var inside = "I'm still inside"; // Same variable
  }
  console.log(inside); // "I'm still inside"
}
```

### let
- Block scoped
- Cannot be redeclared in same scope
- Hoisted but not initialized (temporal dead zone)
- Can be updated

```javascript
let x = 10;
// let x = 20; // Error: x has already been declared
x = 20;      // No error

// console.log(y); // Error: Cannot access 'y' before initialization
let y = 5;

function letExample() {
  let inside = "I'm inside";
  if (true) {
    let inside = "I'm in a block"; // Different variable
    console.log(inside); // "I'm in a block"
  }
  console.log(inside); // "I'm inside"
}
```

### const
- Block scoped
- Cannot be redeclared in same scope
- Cannot be reassigned after initialization
- Must be initialized upon declaration
- Hoisted but not initialized (temporal dead zone)

```javascript
const PI = 3.14159;
// PI = 3; // Error: Assignment to constant variable

// const RATE; // Error: Missing initializer in const declaration

const user = { name: "John" };
user.name = "Jane"; // Valid - object content can be modified
// user = { name: "Jane" }; // Error: Assignment to constant variable

function constExample() {
  const greeting = "Hello";
  if (true) {
    const greeting = "Hi"; // Different variable
    console.log(greeting); // "Hi"
  }
  console.log(greeting); // "Hello"
}
```

## Best Practices

1. Use `const` by default for variables that won't be reassigned
2. Use `let` when you need to reassign values
3. Avoid `var` in modern JavaScript code
4. Initialize variables when declaring them
5. Keep variable scope as limited as possible
6. Use meaningful variable names
