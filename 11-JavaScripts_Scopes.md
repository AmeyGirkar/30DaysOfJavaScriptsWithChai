Here are notes on scopes and variable declaration in JavaScript with code snippets:

# Scopes in JavaScript

## Global Scope
- Variables declared outside any function or block
- Accessible throughout the entire program

```javascript
// Global scope
const globalVariable = "I'm global";

function testFunction() {
  console.log(globalVariable); // Accessible here
}

if (true) {
  console.log(globalVariable); // Accessible here too
}
```

## Function Scope
- Variables declared inside a function
- Only accessible within that function

```javascript
function myFunction() {
  // Function scope
  const functionVariable = "I'm function-scoped";
  console.log(functionVariable); // Works fine
}

myFunction();
// console.log(functionVariable); // ReferenceError: functionVariable is not defined
```

## Block Scope
- Variables declared inside a block (if statements, loops, etc.)
- Only accessible within that block (applies to `let` and `const`, not `var`)

```javascript
if (true) {
  // Block scope
  let blockVariable = "I'm block-scoped";
  const anotherBlockVariable = "I'm also block-scoped";
  console.log(blockVariable); // Works fine
}

// console.log(blockVariable); // ReferenceError: blockVariable is not defined
```

## Lexical Scope
- Inner functions can access variables from outer functions
- Also called "closure"

```javascript
function outer() {
  const outerVariable = "I'm from outer function";
  
  function inner() {
    console.log(outerVariable); // Can access outerVariable
    const innerVariable = "I'm from inner function";
  }
  
  inner();
  // console.log(innerVariable); // ReferenceError: innerVariable is not defined
}
```

# Variable Declaration in JavaScript

## `var`
- Function-scoped (not block-scoped)
- Can be redeclared and updated
- Hoisted to the top of its scope and initialized with `undefined`

```javascript
var x = 10;
var x = 20; // Allowed to redeclare
x = 30;     // Allowed to update

function varTest() {
  var y = 5;
  if (true) {
    var y = 10; // Same variable (function-scoped)
    console.log(y); // 10
  }
  console.log(y); // 10 (not 5)
}
```

## `let`
- Block-scoped
- Cannot be redeclared within the same scope
- Can be updated
- Hoisted but not initialized

```javascript
let a = 10;
// let a = 20; // SyntaxError: Identifier 'a' has already been declared
a = 20;      // Allowed to update

function letTest() {
  let b = 5;
  if (true) {
    let b = 10; // Different variable (block-scoped)
    console.log(b); // 10
  }
  console.log(b); // 5
}
```

## `const`
- Block-scoped
- Cannot be redeclared or reassigned
- Must be initialized at declaration
- For objects and arrays, the content can still be modified

```javascript
const PI = 3.14;
// PI = 3.1415; // TypeError: Assignment to constant variable
// const PI = 3.1415; // SyntaxError: Identifier 'PI' has already been declared

// Object contents can be modified
const person = { name: "John" };
person.name = "Jane"; // Allowed
// person = { name: "Jane" }; // TypeError: Assignment to constant variable

// Array contents can be modified
const arr = [1, 2, 3];
arr.push(4); // Allowed
// arr = [1, 2, 3, 4]; // TypeError: Assignment to constant variable
```

## Differences between var, let, and const

| Feature | var | let | const |
|---------|-----|-----|-------|
| Scope | Function-scoped | Block-scoped | Block-scoped |
| Redeclaration | Allowed | Not allowed | Not allowed |
| Reassignment | Allowed | Allowed | Not allowed |
| Hoisting | Hoisted with `undefined` | Hoisted but not initialized | Hoisted but not initialized |
| Temporal Dead Zone | No | Yes | Yes |
| Must be initialized | No | No | Yes |
