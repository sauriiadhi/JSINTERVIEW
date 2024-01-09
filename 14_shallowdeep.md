# Shallow Copy vs. Deep Copy in JavaScript

Copying objects and arrays is a common operation in JavaScript, and it's important to distinguish between shallow copy and deep copy.

## Shallow Copy:

A shallow copy creates a new object or array, but it only copies the references to the original nested objects or arrays. The nested objects themselves are not duplicated, meaning changes to nested objects in the copy will affect the original, and vice versa.

### Example of Shallow Copy:

```javascript
const originalArray = [1, 2, { a: 3, b: 4 }];
const shallowCopy = [...originalArray];

shallowCopy[2].a = 99;

console.log(originalArray[2].a); // Output: 99
```

# Deep Copy in JavaScript

Creating a deep copy in JavaScript involves duplicating an entire object or array along with all of its nested objects or arrays. This ensures that modifications to the copied structure do not affect the original and vice versa.

## Using JSON.stringify and JSON.parse

One common method for deep copying is using `JSON.stringify` followed by `JSON.parse`. This approach has some limitations, such as the inability to copy functions and handling circular references.

### Example:

```javascript
const originalObject = { a: 1, b: { c: 2, d: { e: 3 } } };

// Deep copy using JSON.stringify and JSON.parse
const deepCopy = JSON.parse(JSON.stringify(originalObject));

deepCopy.b.d.e = 99;

console.log(originalObject.b.d.e); // Output: 3
```