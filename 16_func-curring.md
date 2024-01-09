# Function Currying in JavaScript

**Function currying** is a technique in functional programming where a function is transformed into a sequence of functions, each taking a single argument. The idea is to break down a function that takes multiple arguments into a series of unary (single-argument) functions.

## Basic Example:

Consider a traditional function that adds three numbers:

```javascript
function addThreeNumbers(x, y, z) {
  return x + y + z;
  }

  // With currying, it can be transformed into a series of unary functions:

  function curryAdd(x) {
  return function(y) {
    return function(z) {
      return x + y + z;
    };
  };
}

// Usage
const result = curryAdd(1)(2)(3); // Result: 6

```

## Benefits:

1. **Partial Application**: Curried functions enable partial application, allowing you to fix some arguments and generate a new function that takes the remaining ones.

2. **Reusability** : The generated unary functions can be reused in various contexts, promoting code modularity.

```javascript
// Partial Application
const add5 = curryAdd(5);
const result1 = add5(3)(2); // Result: 10

// Reusing Curried Functions
const concatStrings = curryAdd("Hello, ")("world")("!");
const result2 = concatStrings; // Result: "Hello, world!"
```


## Implementation:

```javascript
// Generic Curry Function
function curry(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn(...args);
    } else {
      return function(...moreArgs) {
        return curried(...args, ...moreArgs);
      };
    }
  };
}

// Usage
const curriedAdd = curry(addThreeNumbers);
const result3 = curriedAdd(1)(2)(3); // Result: 6
```

- The curry function is a generic currying function that can be used with various functions.