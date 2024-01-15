# new 
The `new` keyword in JavaScript is used to create an instance of an object, specifically an instance of a constructor function. When you use `new` with a constructor function, it performs the following steps:

1.  **Creates a new object:** A new, empty object is created. This object will become the instance of the constructor function.
    
2.  **Sets the prototype:** The `[[Prototype]]` of the new object is set to the prototype of the constructor function. This step establishes the prototype chain, allowing the new object to inherit properties and methods from the constructor's prototype.
    
3.  **Calls the constructor function:** The constructor function is invoked with the new object as the value of `this`. This allows the constructor to initialize properties and perform any other setup for the new object.
    
4.  **Returns the new object:** If the constructor function doesn't explicitly return an object, the new object created in step 1 is returned. If the constructor returns an object, that object is returned instead.
    

Here's an example to illustrate the use of the `new` keyword:



```javascript
// Constructor function
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// Creating an instance using 'new'
const john = new Person('John Doe', 30);

console.log(john.name); // Output: John Doe
console.log(john.age);  // Output: 30` 
```

In this example, `Person` is a constructor function, and `new Person('John Doe', 30)` creates a new instance of the `Person` object with the specified `name` and `age`. The `john` object now inherits from the `Person` constructor's prototype.