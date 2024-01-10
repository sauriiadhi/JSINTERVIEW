  

# create objects in JavaScript

  

Object.create` and the constructor pattern are both ways to create objects in JavaScript, but they have some key differences.

### 1. Constructor Pattern:

  

  

In the constructor pattern, you define a function (constructor function) and use the `new` keyword to create instances of objects.

  

  

``` javascript
// Constructor function
function  Person(firstName, lastName) {
	this.firstName = firstName;
	this.lastName = lastName;
}
// Creating an instance
const  john = new  Person('John', 'Doe');
// Accessing properties
console.log(john.firstName); // John`
```

  

**Key Points:**

  

  

- Uses a function as a constructor.

- Involves the use of the `new` keyword.

- Allows you to define properties and methods within the constructor function.

- Instances inherit properties and methods directly from the constructor's prototype.

  

  

### 2. `Object.create`:

  

  

`Object.create` is a method that creates a new object, using an existing object as the prototype of the new object.

  

  

```javascript
// Creating an object as a prototype
const  personPrototype = {
	sayHello:  function() {
		console.log(`Hello, my name is ${this.firstName} ${this.lastName}.`);
	}
};
// Creating an instance with Object.create
const  john = Object.create(personPrototype);
john.firstName = 'John';
john.lastName = 'Doe';
// Accessing properties and methods
console.log(john.firstName); // John
john.sayHello(); // Hello, my name is John Doe.``
```
  

**Key Points:**

  

  

- Creates a new object with an existing object as its prototype.

  

- No constructor function is necessary.

  

- Properties are typically assigned directly to the created object.

  

  

**Differences:**

  

  

- Constructor pattern involves defining a function, while `Object.create` does not require a constructor function.

  

-  `Object.create` allows for explicit control over the prototype chain by specifying the prototype object.

  

  

**Choosing Between Them:**

  

  

- Use the constructor pattern when you want to create multiple instances with shared methods and properties.

  

- Use `Object.create` when you want more control over the prototype or when you're working with a specific prototype object.

  

  

Both patterns are valid, and the choice depends on the specific requirements of your application.

# properties Add

In JavaScript, there are several ways to add properties to an object. Here are some common methods:

  

1.  **Dot Notation:** You can use dot notation to add a property to an object. If the property does not already exist, it will be added; if it does exist, its value will be updated.

``` javascript
// Creating an object
var  person = {};
// Adding properties using dot notation
person.name = "John";
person.age = 25;
```

2.  **Bracket Notation:** Bracket notation allows you to add properties to an object using a string as the property name. This is particularly useful when the property name is stored in a variable.

``` javascript
// Adding properties using bracket notation
person["gender"] = "Male";
```

3.  **Object Initializer:** You can also add properties when creating an object using an object initializer (object literal).

``` javascript
// Creating an object with properties
var  car = {
	brand:  "Toyota",
	model:  "Camry",
	year:  2022
};
```

4.  **Object.assign:** The `Object.assign()` method is used to copy the values of all enumerable properties from one or more source objects to a target object. This method can also be used to add properties to an object.

``` javascript
// Adding properties using Object.assign
Object.assign(person, { city:  "New York", occupation:  "Engineer" });
```