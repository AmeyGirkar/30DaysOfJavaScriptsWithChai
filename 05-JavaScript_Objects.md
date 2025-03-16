# JavaScript Objects

In JavaScript, an object is a fundamental data structure that allows you to store collections of data and functionality together. Let's explore the key aspects of JavaScript objects:

## What is an Object?
A JavaScript object is a collection of key-value pairs (properties and values). Objects are used to store multiple related values in a single container and represent real-world entities in code.

## Purpose
Objects serve several purposes in JavaScript:
- Group related data and functionality
- Create custom data structures
- Model real-world entities
- Store and organize complex data
- Implement reusable code components

## Creation of Objects
There are multiple ways to create objects in JavaScript:

```javascript
// 1. Object literal (most common)
const person = {
  name: "John",
  age: 30,
  greeting: function() {
    return `Hello, my name is ${this.name}`;
  }
};

// 2. Object constructor
const car = new Object();
car.make = "Toyota";
car.model = "Camry";

// 3. Constructor function
function Book(title, author) {
  this.title = title;
  this.author = author;
}
const myBook = new Book("JavaScript", "John Doe");

// 4. ES6 Class syntax
class Product {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
}
const laptop = new Product("MacBook", 1200);

// 5. Object.create()
const personProto = {
  greet: function() {
    return `Hello, my name is ${this.name}`;
  }
};
const employee = Object.create(personProto);
employee.name = "Sarah";
```

## Properties
Object properties are the key-value pairs that define the object's characteristics. Properties can hold any data type, including other objects and functions.

## CRUD Operations on Objects

### Read
You can access object properties in two ways:

```javascript
const user = {
  firstName: "John",
  lastName: "Doe",
  age: 30
};

// Dot notation
console.log(user.firstName); // "John"

// Bracket notation (useful for dynamic properties)
const propertyName = "age";
console.log(user[propertyName]); // 30
```

### Insert
Adding new properties to an existing object:

```javascript
const user = { name: "John" };

// Add a new property
user.age = 30;
user["email"] = "john@example.com";

console.log(user); // { name: "John", age: 30, email: "john@example.com" }
```

### Update
Modifying existing object properties:

```javascript
const user = { name: "John", age: 25 };

// Update existing properties
user.age = 30;
user["name"] = "John Doe";

console.log(user); // { name: "John Doe", age: 30 }
```

### Delete
Removing properties from objects:

```javascript
const user = { 
  name: "John", 
  age: 30, 
  email: "john@example.com" 
};

// Delete a property
delete user.email;

console.log(user); // { name: "John", age: 30 }
```

## Object Methods

### Object.seal()
Prevents adding or deleting properties from an object, but allows modifying existing properties:

```javascript
const user = { name: "John", age: 30 };
Object.seal(user);

// Modification works
user.age = 31; // OK

// Adding fails silently
user.email = "john@example.com"; // Ignored in non-strict mode

// Deletion fails silently
delete user.age; // Ignored in non-strict mode

console.log(user); // { name: "John", age: 31 }
```

### Object.assign()
Copies all enumerable properties from one or more source objects to a target object:

```javascript
const target = { a: 1, b: 2 };
const source = { b: 3, c: 4 };

const result = Object.assign(target, source);

console.log(target); // { a: 1, b: 3, c: 4 }
console.log(result); // { a: 1, b: 3, c: 4 }
```

### Object.keys()
Returns an array of a given object's property names:

```javascript
const user = { 
  name: "John", 
  age: 30, 
  role: "Admin" 
};

const keys = Object.keys(user);
console.log(keys); // ["name", "age", "role"]
```

Additional useful object methods include:
- `Object.values()`: Returns an array of property values
- `Object.entries()`: Returns an array of [key, value] pairs
- `Object.freeze()`: Makes an object immutable (prevents adding, deleting, or changing properties)
- `Object.hasOwnProperty()`: Checks if an object has a specific property

Is there any specific aspect of JavaScript objects you'd like me to explain in more detail?
