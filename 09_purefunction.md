# Pure Functions in JavaScript

## What is a pure function?

A **pure function** is a function that, given the same input, will always return the same output and has no side effects. In other words, a pure function's result is solely determined by its input parameters, and it doesn't modify any external state.

### Key Characteristics:

1. **Deterministic:**
   - A pure function is deterministic, meaning that for a given set of inputs, it will always produce the same output.

2. **No Side Effects:**
   - Pure functions have no side effects. They don't modify variables outside their scope, mutate data structures, or perform any observable actions beyond computing a result.

3. **Referential Transparency:**
   - The concept of referential transparency is closely related to purity. It means that a function call can be replaced with its result without changing the program's behavior.

### Example:

```javascript
// Pure Function Example

// Not a pure function
function impureAdd(x, y) {
  // Modifying external state (side effect)
  total = x + y;
  return total;
}

// Pure function
function pureAdd(x, y) {
  // Only performs computation based on input parameters
  return x + y;
}

// Example of impure and pure function usage
let total = 0; // External state

// Impure function usage
console.log(impureAdd(3, 4)); // Outputs: 7
console.log(total); // Outputs: 7 (external state modified)

// Pure function usage
console.log(pureAdd(3, 4)); // Outputs: 7
console.log(total); // Outputs: 7 (external state unchanged)
