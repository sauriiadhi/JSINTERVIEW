# Prototypal Inheritance in JavaScript

  

In JavaScript, prototypal inheritance is a mechanism for object-oriented programming based on prototypes. Each object has an internal link to another object known as its prototype, forming a "prototype chain."

  

## Objects and Prototypes

  

- Every JavaScript object is linked to another object, its prototype.

- Objects inherit properties and methods from their prototypes.

  

## Creating Objects

  

Objects can be created using different methods:

  

```javascript

// Using object literal

var  person = {

name:  "John",

sayHello:  function() {

console.log("Hello, my name is " + this.name);

}

};

  

// Creating an object with person as its prototype

var  john = Object.create(person);

```

  

### Accessing Properties and Methods

- JavaScript looks in the object itself.

- If not found, it searches in the object's prototype, and so on.

```

john.sayHello();

```

  

### Modifying and Adding Properties

  

Changes to the prototype reflect in all inheriting objects, and properties can be added dynamically.

  

```

person.age = 30;

console.log(john.age); // This will print 30

```

  

### Constructor Functions

  

Constructor functions can be used to create objects with a shared prototype.

```

function Person(name) {

this.name = name;

}

  

Person.prototype.sayHello = function() {

console.log("Hello, my name is " + this.name);

};

  

var john = new Person("John");

john.sayHello();

```

  

Prototypal inheritance offers a flexible way to share and reuse code in JavaScript

  
