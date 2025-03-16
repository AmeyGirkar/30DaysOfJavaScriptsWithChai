# Closures in JavaScript - Simple Explanation

## What is a Closure?

A closure is when a function remembers and can access variables from outside itself, even after the outer function has finished running.

## How to Create a Closure

You create a closure by putting one function inside another. The inner function can use the outer function's variables.

```javascript
function outer(name) {
  // The inner function can use the "name" variable
  function inner() {
    console.log("Hello, " + name + "!");
  }
  
  return inner;
}

const greetJohn = outer("John");
greetJohn(); // Prints: "Hello, John!"
```

## Syntax

There's no special syntax - you just define a function inside another function. The inner function naturally becomes a closure.

## Purpose

Closures are useful for:

1. **Keeping data private**: Hide variables that only specific functions can access.

```javascript
function createCounter() {
  let count = 0; // Private - can't be accessed directly from outside
  
  return function() {
    count++;
    return count;
  };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
```

2. **Creating function factories**: Make functions that are customized for specific uses.

```javascript
function makeGreeter(greeting) {
  return function(name) {
    return greeting + ", " + name + "!";
  };
}

const sayHello = makeGreeter("Hello");
const sayHowdy = makeGreeter("Howdy");

console.log(sayHello("Maria")); // "Hello, Maria!"
console.log(sayHowdy("Maria")); // "Howdy, Maria!"
```

Think of closures like a backpack that a function carries around. The backpack contains all the variables that were in scope when the function was created.
