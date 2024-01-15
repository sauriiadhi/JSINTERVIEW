Object destructuring is a feature in JavaScript that allows you to extract values from objects and assign them to variables in a more concise and expressive way. It provides a shorter syntax for extracting properties from an object and can simplify the code, especially when working with objects containing a large number of properties.

Here's a basic overview of object destructuring:

### Basic Syntax:
```javascript
// Object with properties
const person = {
  name: "John",
  age: 30,
  city: "New York"
};

// Object destructuring
const { name, age, city } = person;

// Using the extracted values
console.log(name); // "John"
console.log(age);  // 30
console.log(city); // "New York"` 
```

### Renaming Variables:

You can also rename variables during object destructuring:

```javascript
const { name: personName, age: personAge } = person;

console.log(personName); // "John"
console.log(personAge);  // 30` 
```
### Default Values:

You can provide default values for properties that might be undefined:

```javascript
const { name, age, city, job = "Engineer" } = person;

console.log(job); // "Engineer" (default value)` 
```
### Nested Destructuring:

Destructuring can be applied to nested objects:

```javascript
const user = {
  id: 1,
  details: {
    name: "Alice",
    age: 25
  }
};

const { id, details: { name, age } } = user;

console.log(id);   // 1
console.log(name); // "Alice"
console.log(age);  // 25` 
```
### Function Parameters:

Object destructuring is commonly used with function parameters to extract values from an object passed as an argument:

```javascript
function printPersonInfo({ name, age, city }) {
  console.log(`Name: ${name}, Age: ${age}, City: ${city}`);
}

printPersonInfo(person);`` 
```
Object destructuring provides a more concise and readable way to work with object properties, especially when you only need a subset of the properties or want to alias them. It's widely used in modern JavaScript development.