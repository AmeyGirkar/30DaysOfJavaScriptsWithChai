I'll create detailed notes on Spread, Rest, and Destructuring in JavaScript with code snippets and outputs.

```javascript
// ==========================================
// SPREAD OPERATOR (...)
// ==========================================

// 1. Copying properties from one object to another
console.log("=== OBJECT SPREAD ===");

// Original object
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

// Using spread to copy all properties
const personCopy = { ...person };
console.log("Original object:", person);
console.log("Copied object:", personCopy);
// Output:
// Original object: { name: 'John', age: 30, city: 'New York' }
// Copied object: { name: 'John', age: 30, city: 'New York' }

// Adding/overriding properties while copying
const personWithExtras = { 
  ...person, 
  age: 31,      // Override existing property
  job: "Developer" // Add new property
};
console.log("Extended object:", personWithExtras);
// Output:
// Extended object: { name: 'John', age: 31, city: 'New York', job: 'Developer' }

// Merging multiple objects
const address = {
  street: "123 Main St",
  zipCode: "10001"
};

const mergedPerson = { ...person, ...address };
console.log("Merged objects:", mergedPerson);
// Output:
// Merged objects: {
//   name: 'John',
//   age: 30,
//   city: 'New York',
//   street: '123 Main St',
//   zipCode: '10001'
// }

// 2. Copying elements from one array to another
console.log("\n=== ARRAY SPREAD ===");

// Original array
const numbers = [1, 2, 3];

// Using spread to copy all elements
const numbersCopy = [...numbers];
console.log("Original array:", numbers);
console.log("Copied array:", numbersCopy);
// Output:
// Original array: [1, 2, 3]
// Copied array: [1, 2, 3]

// Adding elements while copying
const extendedNumbers = [...numbers, 4, 5];
console.log("Extended array:", extendedNumbers);
// Output:
// Extended array: [1, 2, 3, 4, 5]

// Insert elements in the middle
const insertedNumbers = [0, ...numbers, 4];
console.log("Array with inserted elements:", insertedNumbers);
// Output:
// Array with inserted elements: [0, 1, 2, 3, 4]

// Merging multiple arrays
const moreNumbers = [4, 5, 6];
const mergedNumbers = [...numbers, ...moreNumbers];
console.log("Merged arrays:", mergedNumbers);
// Output:
// Merged arrays: [1, 2, 3, 4, 5, 6]

// Spreading string into characters
const letters = [..."hello"];
console.log("String spread into array:", letters);
// Output:
// String spread into array: ['h', 'e', 'l', 'l', 'o']

// ==========================================
// REST PARAMETER (...)
// ==========================================
console.log("\n=== REST PARAMETER ===");

// Basic rest parameter usage
function sum(...numbers) {
  return numbers.reduce((total, num) => total + num, 0);
}

console.log("Sum of 1, 2, 3:", sum(1, 2, 3));
console.log("Sum of 1, 2, 3, 4, 5:", sum(1, 2, 3, 4, 5));
// Output:
// Sum of 1, 2, 3: 6
// Sum of 1, 2, 3, 4, 5: 15

// Rules of rest parameter:
// 1. Must be the last parameter
function processItems(first, second, ...rest) {
  console.log("First item:", first);
  console.log("Second item:", second);
  console.log("Rest of items:", rest);
}

processItems("apple", "banana", "orange", "grape", "kiwi");
// Output:
// First item: apple
// Second item: banana
// Rest of items: ['orange', 'grape', 'kiwi']

// Order of parameters is important
function getUserInfo(id, username, ...otherInfo) {
  return {
    id,
    username,
    otherInfo
  };
}

const userInfo = getUserInfo(123, "john_doe", "Developer", "New York", 30);
console.log("User info:", userInfo);
// Output:
// User info: {
//   id: 123,
//   username: 'john_doe',
//   otherInfo: ['Developer', 'New York', 30]
// }

// Invalid rest parameter example (would cause syntax error):
// function invalidRest(...params, lastParam) {
//   // This would cause a SyntaxError: Rest parameter must be last formal parameter
// }

// ==========================================
// DESTRUCTURING
// ==========================================
console.log("\n=== OBJECT DESTRUCTURING ===");

// Object Destructuring
const user = {
  firstName: "John",
  lastName: "Doe",
  age: 30,
  email: "john@example.com",
  address: {
    city: "New York",
    country: "USA"
  }
};

// Basic object destructuring
const { firstName, lastName } = user;
console.log("First name:", firstName);
console.log("Last name:", lastName);
// Output:
// First name: John
// Last name: Doe

// Assigning to different variable names
const { firstName: fName, lastName: lName } = user;
console.log("First name (renamed):", fName);
console.log("Last name (renamed):", lName);
// Output:
// First name (renamed): John
// Last name (renamed): Doe

// Default values
const { job = "Unknown" } = user;
console.log("Job:", job);
// Output:
// Job: Unknown

// Nested object destructuring
const { address: { city, country } } = user;
console.log("City:", city);
console.log("Country:", country);
// Output:
// City: New York
// Country: USA

// Rest pattern with objects
const { firstName: fn, ...userRest } = user;
console.log("First name extracted:", fn);
console.log("Rest of user object:", userRest);
// Output:
// First name extracted: John
// Rest of user object: {
//   lastName: 'Doe',
//   age: 30,
//   email: 'john@example.com',
//   address: { city: 'New York', country: 'USA' }
// }

console.log("\n=== ARRAY DESTRUCTURING ===");

// Array Destructuring
const fruits = ["apple", "banana", "orange", "grape", "kiwi"];

// Basic array destructuring
const [first, second] = fruits;
console.log("First fruit:", first);
console.log("Second fruit:", second);
// Output:
// First fruit: apple
// Second fruit: banana

// Skipping elements
const [firstFruit, , thirdFruit] = fruits;
console.log("First fruit:", firstFruit);
console.log("Third fruit:", thirdFruit);
// Output:
// First fruit: apple
// Third fruit: orange

// Default values
const colors = ["red", "green"];
const [primaryColor, secondaryColor, tertiaryColor = "blue"] = colors;
console.log("Primary color:", primaryColor);
console.log("Secondary color:", secondaryColor);
console.log("Tertiary color:", tertiaryColor);
// Output:
// Primary color: red
// Secondary color: green
// Tertiary color: blue

// Rest pattern with arrays
const [head, ...tail] = fruits;
console.log("Head:", head);
console.log("Tail:", tail);
// Output:
// Head: apple
// Tail: ['banana', 'orange', 'grape', 'kiwi']

// Swapping variables without temporary variable
let a = 5;
let b = 10;
console.log("Before swap - a:", a, "b:", b);

[a, b] = [b, a];
console.log("After swap - a:", a, "b:", b);
// Output:
// Before swap - a: 5 b: 10
// After swap - a: 10 b: 5

// Nested array destructuring
const nestedArrays = [1, [2, 3], 4];
const [first1, [second1, second2], fourth] = nestedArrays;
console.log("Nested array values:", first1, second1, second2, fourth);
// Output:
// Nested array values: 1 2 3 4

// Function that returns an array and uses destructuring
function getCoordinates() {
  return [10, 20];
}

const [x, y] = getCoordinates();
console.log("Coordinates:", x, y);
// Output:
// Coordinates: 10 20

// Combined object and array destructuring
const complexData = {
  id: 1,
  info: ["John", 30],
  scores: [90, 85, 95]
};

const { id, info: [name, userAge], scores: [math, ...otherScores] } = complexData;
console.log("ID:", id);
console.log("Name and age:", name, userAge);
console.log("Math score:", math);
console.log("Other scores:", otherScores);
// Output:
// ID: 1
// Name and age: John 30
// Math score: 90
// Other scores: [85, 95]

```


## Spread Operator

### Object Spread
- Copies properties from one object to another: `const copy = { ...original }`
- Can add or override properties during copying: `const extended = { ...original, newProp: value }`
- Merges multiple objects: `const merged = { ...obj1, ...obj2 }`

### Array Spread
- Copies elements from one array to another: `const copy = [...original]`
- Adds elements while copying: `const extended = [...original, 4, 5]`
- Merges arrays: `const merged = [...arr1, ...arr2]`
- Can spread strings into character arrays: `const chars = [..."hello"]`

## Rest Parameter

### Rules
- Must be the last parameter in a function definition
- Collects all remaining arguments into an array
- Uses the same `...` syntax as spread but in parameter position

### Order of Parameters
- Regular parameters come first, rest parameter must be last
- Example: `function process(first, second, ...remainder)`
- Invalid: `function invalid(...args, last)` - causes syntax error

## Destructuring

### Object Destructuring
- Extract properties: `const { prop1, prop2 } = object`
- Rename variables: `const { prop: newName } = object`
- Set default values: `const { prop = default } = object`
- Nested destructuring: `const { outer: { inner } } = object`
- Rest pattern: `const { prop, ...rest } = object`

### Array Destructuring
- Extract elements: `const [first, second] = array`
- Skip elements: `const [first, , third] = array`
- Default values: `const [a, b, c = default] = array`
- Rest pattern: `const [first, ...rest] = array`
- Swap variables: `[a, b] = [b, a]`
- Nested arrays: `const [a, [b, c]] = nestedArray`

The code snippet includes practical examples of each concept with their corresponding outputs.
