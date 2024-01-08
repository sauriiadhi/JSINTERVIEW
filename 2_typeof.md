# How do you check the type of a variable in JavaScript?

- typeof "Hello" returns "string"
- typeof 42 returns "number"
- typeof true returns "boolean"
- typeof undefined returns "undefined"
- typeof null returns "object" (This is a historical quirk. null is an object, but it's a special case.)



## For more detailed and accurate type checking, especially in scenarios where you need to differentiate between various objects (arrays, functions, etc.), you might use the `Object.prototype.toString`  method:

- For example:
```javascript
function getType(obj) {
    return Object.prototype.toString.call(obj).slice(8, -1);
}

console.log(getType([]));  // Outputs: "Array"
console.log(getType({}));  // Outputs: "Object"
console.log(getType(function () {}));  // Outputs: "Function"
```


