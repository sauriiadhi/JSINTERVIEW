## Function Borrowing vs Method Borrowing

### Function Borrowing

- Involves taking a function from one object and using it as a function, not necessarily a method.
- The borrowed function is applied to another object using methods like `call` or `apply`.
- The primary focus is on reusing a function in a different context.

### Method Borrowing

- Specifically refers to borrowing a method from one object (typically from the prototype) and using it as a method of another object.
- Often involves borrowing methods associated with prototypes.
- Emphasizes the borrowing of object methods, considering the object-oriented nature of JavaScript.

In practice, the terms are sometimes used interchangeably, and the distinction may not be critical in all scenarios. Both involve leveraging existing functions/methods in a different context, but the emphasis on whether it's a function or a method is what sets them apart.
