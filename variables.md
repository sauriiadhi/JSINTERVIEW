# Difference between `let`, `const`, and `var`

In JavaScript, `let`, `const`, and `var` are used to declare variables, but they have some key differences in terms of scope, reassignment, and hoisting.

## `var`

- **Scope:**
  - Function-scoped: Variables declared with `var` are function-scoped, meaning their scope is limited to the function in which they are declared.
  
- **Reassignment:**
  - Can be reassigned: Variables declared with `var` can be reassigned and updated.

- **Hoisting:**
  - Hoisted: Variables declared with `var` are hoisted to the top of their scope, which means they can be used before they are declared.
  - Variables declared with `let` and `const` are also hoisted, but there's a concept called the "temporal dead zone" (TDZ). results to `ReferenceError`

Example:

```javascript
function example() {
  if (true) {
    var x = 10;
  }
  console.log(x); // Outputs 10 (hoisting)
}
```

## `let`

In JavaScript, `let` is used to declare variables that can be reassigned. Here are key points regarding `let`:

- **Scope:**
  -block-scoped: `let` is block-scoped, meaning it is limited to the block (portion of code enclosed in curly braces) in which it is declared.

- **Reassignment:**
  - Variables declared with `let` can be reassigned and updated with new values.

- **Example:**

  ```javascript
  function example() {
    if (true) {
      let x = 10;
      console.log(x); // Outputs 10
      x = 20; // Reassignment is allowed
      console.log(x); // Outputs 20
    }
    console.log(x); // Error: x is not defined (outside the block scope)
  }
  ```

## `const`

`const` is a keyword in JavaScript used to declare variables. Unlike `let`, the value assigned to a variable declared with `const` cannot be reassigned. However, it's important to note that for objects and arrays, while the variable itself cannot be reassigned, the properties or elements within them can be modified.

### Key Features:

- **Scope:**
  - `const` is block-scoped, meaning it is limited to the block (portion of code enclosed in curly braces) in which it is declared.

- **Reassignment:**
  - Variables declared with `const` cannot be reassigned. Once a value is assigned, it cannot be changed.

- **Example:**

  ```javascript
  function example() {
    if (true) {
      const x = 10;
      console.log(x); // Outputs 10
      x = 20; // Error: Assignment to a constant variable
    }
    console.log(x); // Error: x is not defined (outside the block scope)
  }
    ```

### Key diffrence btw `let` & `var`:
- **Scoping:**
- **Hoisting:**
- **Hoisting:**
- **Hoisting:**



## How Does Hoisting Work in JavaScript?

Hoisting is a behavior in JavaScript where variable and function declarations are moved to the top of their containing scope during the compilation phase. This means that you can use variables and functions before they are declared in your code. However, it's important to understand that only the declarations are hoisted, not the initializations.

Let's look at an example:

```javascript
console.log(x); // undefined
var x = 5;
console.log(x); // 5

console.log(y); // ReferenceError: Cannot access 'y' before initialization
let y = 10;
console.log(y); // 10

