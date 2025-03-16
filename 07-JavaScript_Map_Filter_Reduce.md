# Detailed Guide: Map, Filter, and Reduce Methods in JavaScript

Let's explore these three powerful array methods in depth using the same array example throughout.

## Our Example Array

```javascript
const products = [
  { id: 1, name: "Laptop", price: 999.99, category: "Electronics", inStock: true },
  { id: 2, name: "Smartphone", price: 699.99, category: "Electronics", inStock: true },
  { id: 3, name: "Headphones", price: 199.99, category: "Electronics", inStock: false },
  { id: 4, name: "Coffee Maker", price: 89.99, category: "Kitchen", inStock: true },
  { id: 5, name: "Blender", price: 49.99, category: "Kitchen", inStock: false },
  { id: 6, name: "Monitor", price: 349.99, category: "Electronics", inStock: true }
];
```

## The Map Method

### Purpose
The `map()` method creates a new array by applying a transformation function to each element in the original array.

### Syntax
```javascript
array.map(callback(currentValue, index, array), thisArg)
```

- `callback`: Function that produces an element of the new array
- `currentValue`: The current element being processed
- `index` (optional): The index of the current element
- `array` (optional): The array `map()` was called upon
- `thisArg` (optional): Value to use as `this` when executing callback

### Return Value
A new array with each element being the result of the callback function.

### Examples

#### 1. Extract specific properties
```javascript
const productNames = products.map(product => product.name);
console.log(productNames);
// Output: ["Laptop", "Smartphone", "Headphones", "Coffee Maker", "Blender", "Monitor"]
```

#### 2. Create formatted strings
```javascript
const productDetails = products.map(product => 
  `${product.name} - $${product.price} (${product.inStock ? 'In Stock' : 'Out of Stock'})`
);
console.log(productDetails);
// Output:
// [
//   "Laptop - $999.99 (In Stock)",
//   "Smartphone - $699.99 (In Stock)",
//   "Headphones - $199.99 (Out of Stock)",
//   "Coffee Maker - $89.99 (In Stock)",
//   "Blender - $49.99 (Out of Stock)",
//   "Monitor - $349.99 (In Stock)"
// ]
```

#### 3. Transform object structure
```javascript
const simplifiedProducts = products.map(product => ({
  id: product.id,
  name: product.name,
  priceWithTax: (product.price * 1.08).toFixed(2)
}));
console.log(simplifiedProducts);
// Output:
// [
//   { id: 1, name: "Laptop", priceWithTax: "1079.99" },
//   { id: 2, name: "Smartphone", priceWithTax: "755.99" },
//   { id: 3, name: "Headphones", priceWithTax: "215.99" },
//   { id: 4, name: "Coffee Maker", priceWithTax: "97.19" },
//   { id: 5, name: "Blender", priceWithTax: "53.99" },
//   { id: 6, name: "Monitor", priceWithTax: "377.99" }
// ]
```

#### 4. Using index parameter
```javascript
const productsWithRank = products.map((product, index) => ({
  ...product,
  rank: index + 1
}));
console.log(productsWithRank[0]);
// Output: { id: 1, name: "Laptop", price: 999.99, category: "Electronics", inStock: true, rank: 1 }
```

### Key Points
- **Immutability**: `map()` always returns a new array; it doesn't modify the original array
- **One-to-one mapping**: The resulting array will always have the same length as the original array
- **Transformation**: Used when you need to transform each element in the same way

## The Filter Method

### Purpose
The `filter()` method creates a new array with all elements that pass a test implemented by the provided function.

### Syntax
```javascript
array.filter(callback(element, index, array), thisArg)
```

- `callback`: Function that tests each element; return `true` to keep the element
- `element`: The current element being processed
- `index` (optional): The index of the current element
- `array` (optional): The array `filter()` was called upon
- `thisArg` (optional): Value to use as `this` when executing callback

### Return Value
A new array containing all elements that pass the test.

### Examples

#### 1. Filter by property value
```javascript
const inStockProducts = products.filter(product => product.inStock);
console.log(inStockProducts);
// Output: [
//   { id: 1, name: "Laptop", price: 999.99, category: "Electronics", inStock: true },
//   { id: 2, name: "Smartphone", price: 699.99, category: "Electronics", inStock: true },
//   { id: 4, name: "Coffee Maker", price: 89.99, category: "Kitchen", inStock: true },
//   { id: 6, name: "Monitor", price: 349.99, category: "Electronics", inStock: true }
// ]
```

#### 2. Filter by category
```javascript
const electronicsProducts = products.filter(product => product.category === "Electronics");
console.log(electronicsProducts);
// Output: [
//   { id: 1, name: "Laptop", price: 999.99, category: "Electronics", inStock: true },
//   { id: 2, name: "Smartphone", price: 699.99, category: "Electronics", inStock: true },
//   { id: 3, name: "Headphones", price: 199.99, category: "Electronics", inStock: false },
//   { id: 6, name: "Monitor", price: 349.99, category: "Electronics", inStock: true }
// ]
```

#### 3. Filter by price range
```javascript
const affordableProducts = products.filter(product => product.price < 200);
console.log(affordableProducts);
// Output: [
//   { id: 3, name: "Headphones", price: 199.99, category: "Electronics", inStock: false },
//   { id: 4, name: "Coffee Maker", price: 89.99, category: "Kitchen", inStock: true },
//   { id: 5, name: "Blender", price: 49.99, category: "Kitchen", inStock: false }
// ]
```

#### 4. Multiple conditions
```javascript
const affordableElectronics = products.filter(product => 
  product.category === "Electronics" && 
  product.price < 500 && 
  product.inStock
);
console.log(affordableElectronics);
// Output: [
//   { id: 6, name: "Monitor", price: 349.99, category: "Electronics", inStock: true }
// ]
```

### Key Points
- **Immutability**: `filter()` doesn't modify the original array
- **Subset selection**: The resulting array will be the same length or shorter than the original
- **Boolean test**: Each element is tested against a condition that returns `true` or `false`
- **Empty array**: If no elements pass the test, an empty array is returned

## The Reduce Method

### Purpose
The `reduce()` method executes a reducer function on each element of the array, resulting in a single output value.

### Syntax
```javascript
array.reduce(callback(accumulator, currentValue, index, array), initialValue)
```

- `callback`: Function to execute on each element
- `accumulator`: Accumulated value from previous iterations
- `currentValue`: Current element being processed
- `index` (optional): Index of the current element
- `array` (optional): The array `reduce()` was called upon
- `initialValue` (optional): Value to use as the first argument to the first call of the callback

### Return Value
The single value that results from the reduction.

### Examples

#### 1. Sum all prices
```javascript
const totalPrice = products.reduce((total, product) => total + product.price, 0);
console.log(totalPrice.toFixed(2));
// Output: "2389.94"
```

#### 2. Group by category
```javascript
const groupedByCategory = products.reduce((acc, product) => {
  // If this category doesn't exist yet, create it
  if (!acc[product.category]) {
    acc[product.category] = [];
  }
  // Add the product to the appropriate category
  acc[product.category].push(product);
  return acc;
}, {});

console.log(Object.keys(groupedByCategory));
// Output: ["Electronics", "Kitchen"]
console.log(groupedByCategory.Electronics.length);
// Output: 4
```

#### 3. Find most expensive product
```javascript
const mostExpensive = products.reduce((max, product) => 
  product.price > max.price ? product : max
);
console.log(mostExpensive);
// Output: { id: 1, name: "Laptop", price: 999.99, category: "Electronics", inStock: true }
```

#### 4. Create inventory report
```javascript
const inventoryReport = products.reduce((report, product) => {
  report.totalProducts++;
  report.totalValue += product.price;
  
  if (product.inStock) {
    report.inStockProducts++;
    report.inStockValue += product.price;
  } else {
    report.outOfStockProducts++;
  }
  
  return report;
}, {
  totalProducts: 0,
  inStockProducts: 0,
  outOfStockProducts: 0,
  totalValue: 0,
  inStockValue: 0
});

console.log(inventoryReport);
// Output:
// {
//   totalProducts: 6,
//   inStockProducts: 4,
//   outOfStockProducts: 2,
//   totalValue: 2389.94,
//   inStockValue: 2139.96
// }
```

### Key Points
- **Versatility**: `reduce()` can perform complex operations that transform an array into anything (number, string, object, array)
- **Accumulation**: Each iteration builds upon the result of the previous iteration
- **Initial value**: Always provide an initial value for clarity and to handle empty arrays
- **Reducer function**: The callback must return the updated accumulator on each iteration

## Chaining Methods Together

Since all three methods return arrays (except `reduce()` which can return any type), they can be chained together for powerful data transformations.

```javascript
const result = products
  .filter(product => product.category === "Electronics") // Filter electronics only
  .map(product => ({                                    // Format the data
    name: product.name,
    price: product.price
  }))
  .reduce((total, product) => total + product.price, 0); // Sum prices

console.log(result);
// Output: 2249.96
```

## Performance Considerations

- All three methods iterate through the entire array
- Chaining creates intermediate arrays, which may affect performance for very large datasets
- For simple operations on large arrays, consider using traditional `for` loops for better performance
- For complex operations, the readability and maintainability of these methods often outweigh minor performance differences
