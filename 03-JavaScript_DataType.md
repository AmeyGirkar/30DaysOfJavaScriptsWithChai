# JavaScript Data Types

Here are detailed notes on JavaScript data types with code snippets:

## 1. Number

Numbers in JavaScript represent both integers and floating-point values.

```javascript
// Integer
let age = 25;

// Floating-point
let price = 19.99;

// Scientific notation
let largeNumber = 1.23e6; // 1,230,000

// Special values
let infinity = Infinity;
let negativeInfinity = -Infinity;
let notANumber = NaN;

// Number methods
let num = 123.456;
console.log(num.toFixed(2)); // "123.46"
console.log(num.toString()); // "123.456"
console.log(Number.isInteger(42)); // true
console.log(Number.isNaN(NaN)); // true
```

## 2. Boolean

Represents logical values: true or false.

```javascript
let isActive = true;
let isComplete = false;

// Boolean conversion
console.log(Boolean(1)); // true
console.log(Boolean(0)); // false
console.log(Boolean("")); // false
console.log(Boolean("hello")); // true
console.log(Boolean(null)); // false
console.log(Boolean(undefined)); // false
```

## 3. String

Represents textual data enclosed in single quotes, double quotes, or backticks.

```javascript
let singleQuotes = 'Hello';
let doubleQuotes = "World";
let backticks = `Hello World`;

// String concatenation
let greeting = singleQuotes + " " + doubleQuotes;
console.log(greeting); // "Hello World"

// Template literals
let name = "Alice";
let templateLiteral = `Hello, ${name}!`;
console.log(templateLiteral); // "Hello, Alice!"

// String methods
let str = "JavaScript";
console.log(str.length); // 10
console.log(str.toUpperCase()); // "JAVASCRIPT"
console.log(str.substring(0, 4)); // "Java"
console.log(str.split("")); // ["J","a","v","a","S","c","r","i","p","t"]
```

## 4. Null

Represents the intentional absence of any object value.

```javascript
let empty = null;
console.log(typeof empty); // "object" (This is a historical bug in JavaScript)

// Checking for null
console.log(empty === null); // true
```

## 5. Undefined

Represents a variable that has been declared but not assigned a value.

```javascript
let notDefined;
console.log(notDefined); // undefined
console.log(typeof notDefined); // "undefined"

// Function without return statement returns undefined
function noReturn() {
  // No return statement
}
console.log(noReturn()); // undefined
```

## 6. BigInt

Represents integers of arbitrary precision.

```javascript
// Creating BigInt
let bigInt = 1234567890123456789012345n;
let anotherBigInt = BigInt("9007199254740991");

// Operations
console.log(bigInt + 1n); // 1234567890123456789012346n
console.log(bigInt * 2n); // 2469135780246913578024690n

// Cannot mix with regular numbers
// console.log(bigInt + 1); // TypeError

// Comparison
console.log(1n === 1); // false (different types)
console.log(1n == 1); // true (coerced comparison)
```

## 7. Symbol

Represents a unique and immutable primitive value.

```javascript
// Creating symbols
let sym1 = Symbol();
let sym2 = Symbol("description");
let sym3 = Symbol("description");

console.log(sym2 === sym3); // false (each Symbol is unique)

// Use case: unique property keys
let obj = {};
obj[sym1] = "Value for sym1";
obj[sym2] = "Value for sym2";

// Symbols are not enumerable in for...in
for (let key in obj) {
  console.log(key); // Nothing is logged
}

// Getting symbol properties
console.log(Object.getOwnPropertySymbols(obj)); // [Symbol(), Symbol(description)]
```

## 8. Object

Represents a collection of key-value pairs.

```javascript
// Object literal
let person = {
  name: "John",
  age: 30,
  isEmployed: true,
  greet: function() {
    return `Hello, my name is ${this.name}`;
  }
};

// Accessing properties
console.log(person.name); // "John"
console.log(person["age"]); // 30

// Method invocation
console.log(person.greet()); // "Hello, my name is John"

// Arrays are objects
let colors = ["red", "green", "blue"];
console.log(typeof colors); // "object"

// Functions are objects
function add(a, b) {
  return a + b;
}
console.log(typeof add); // "function" (but is actually an object)

// Built-in objects
let now = new Date();
let regex = /\d+/g;
let map = new Map();
let set = new Set();
```
