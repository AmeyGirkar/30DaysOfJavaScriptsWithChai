# Conditional Statements and Loops in JavaScript

## Conditional Statements

### If Statement
The `if` statement executes a block of code if a specified condition is true.

```javascript
let age = 18;

if (age >= 18) {
  console.log("You are eligible to vote.");
}

// Output:
// You are eligible to vote.
```

### Else Statement
The `else` statement executes a block of code if the condition in the `if` statement is false.

```javascript
let age = 16;

if (age >= 18) {
  console.log("You are eligible to vote.");
} else {
  console.log("You are not eligible to vote yet.");
}

// Output:
// You are not eligible to vote yet.
```

### Else If Statement
The `else if` statement specifies a new condition if the first condition is false.

```javascript
let score = 75;

if (score >= 90) {
  console.log("Grade: A");
} else if (score >= 80) {
  console.log("Grade: B");
} else if (score >= 70) {
  console.log("Grade: C");
} else if (score >= 60) {
  console.log("Grade: D");
} else {
  console.log("Grade: F");
}

// Output:
// Grade: C
```

### Switch Statement
The `switch` statement selects one of many code blocks to be executed based on a matched value.

```javascript
let day = 3;
let dayName;

switch (day) {
  case 1:
    dayName = "Monday";
    break;
  case 2:
    dayName = "Tuesday";
    break;
  case 3:
    dayName = "Wednesday";
    break;
  case 4:
    dayName = "Thursday";
    break;
  case 5:
    dayName = "Friday";
    break;
  case 6:
    dayName = "Saturday";
    break;
  case 7:
    dayName = "Sunday";
    break;
  default:
    dayName = "Invalid day";
}

console.log(`Today is ${dayName}`);

// Output:
// Today is Wednesday
```

## Loops

### For Loop
The `for` loop repeats a block of code a specified number of times.

```javascript
// Print numbers from 1 to 5
for (let i = 1; i <= 5; i++) {
  console.log(i);
}

// Output:
// 1
// 2
// 3
// 4
// 5

// The three parts of a for loop:
// 1. Initialization (let i = 1)
// 2. Condition (i <= 5)
// 3. Increment/Decrement (i++)
```

### For...of Loop
The `for...of` loop iterates over iterable objects like arrays, strings, etc.

```javascript
// Iterating over an array
const fruits = ["apple", "banana", "orange", "mango"];

for (const fruit of fruits) {
  console.log(fruit);
}

// Output:
// apple
// banana
// orange
// mango

// Iterating over a string
const text = "Hello";

for (const char of text) {
  console.log(char);
}

// Output:
// H
// e
// l
// l
// o
```

### For...in Loop
The `for...in` loop iterates over the enumerable properties of an object.

```javascript
// Iterating over object properties
const person = {
  name: "John",
  age: 30,
  job: "Developer",
  city: "New York"
};

for (const key in person) {
  console.log(`${key}: ${person[key]}`);
}

// Output:
// name: John
// age: 30
// job: Developer
// city: New York

// Using for...in with arrays (not recommended, use for...of instead)
const numbers = [10, 20, 30, 40];

for (const index in numbers) {
  console.log(`Index: ${index}, Value: ${numbers[index]}`);
}

// Output:
// Index: 0, Value: 10
// Index: 1, Value: 20
// Index: 2, Value: 30
// Index: 3, Value: 40
```

## Key Differences and Use Cases

1. **Conditional Statements**:
   - `if-else` is best for simple conditions
   - `else if` is used for multiple related conditions
   - `switch` is ideal for matching a value against multiple possible cases

2. **Loops**:
   - `for` loop: Use when you know the number of iterations in advance
   - `for...of` loop: Use for iterating over array values or other iterables
   - `for...in` loop: Use for iterating over object properties
