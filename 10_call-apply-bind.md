## Function.prototype.call() in JavaScript

The `Function.prototype.call` method is used to invoke a function with a specified `this` value and individual arguments. It allows you to explicitly set the `this` value for the function and pass arguments individually.

## https://www.javascripttutorial.net/javascript-call/

### Syntax

```javascript
function.call(thisArg, arg1, arg2, ...)
```

## Function.prototype.apply() in JavaScript

The `Function.prototype.apply` method is used to invoke a function with a specified `this` value and arguments as array. It allows you to explicitly set the `this` value for the function and pass arguments as array.

- Using the apply() method to append an array to another

## https://www.javascripttutorial.net/javascript-call/

### Syntax

```javascript
function.apply(thisArg,[args])
```


```javascript
const computer = {
    name: 'MacBook',
    isOn: false,
    turnOn() {
        this.isOn = true;
        return `The ${this.name} is On`;
    },
    turnOff() {
        this.isOn = false;
        return `The ${this.name} is Off`;
    }
};
const server = {
    name: 'Dell PowerEdge T30',
    isOn: false
};
let result = computer.turnOn.call(server);
let resultap = computer.turnOff.apply(server);
```


## Function.bind() in JavaScript

- In this syntax, the bind() method returns a copy of the function fn with the specific this value (thisArg) and arguments (arg1, arg2, …).
- Unlike the `call()` and `apply()` methods, the `bind()` method doesn’t immediately execute the function. It just returns a new version of the function whose this sets to thisArg argument.

## https://www.javascripttutorial.net/javascript-bind/

### Syntax

```javascript
fn.bind(thisArg[, arg1[, arg2[, ...]]])
```