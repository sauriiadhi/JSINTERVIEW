# Object Copying in JavaScript

## Shallow Copy:

### Spread Operator (`...`):
```javascript
const shallowCopy = { ...originalObject };
```
### Object.assign:
```javascript
const shallowCopy = Object.assign({}, originalObject);
```
### Array.from (for arrays):
```javascript
const shallowCopy = Array.from(originalArray);
```

## Deep Copy:

### JSON.stringify and JSON.parse:
```javascript
const deepCopy = JSON.parse(JSON.stringify(originalObject));
```
### Lodash Library (for comprehensive deep copy):
```javascript
const _ = require('lodash');
const deepCopy = _.cloneDeep(originalObject);
```
### Copying with Constructor:
```javascript
function CustomObject(value) {
  this.value = value;
}

const originalInstance = new CustomObject(42);
const newInstance = new CustomObject(originalInstance.value);

```
### Copying with Object.create::
```javascript
const copiedObject = Object.create(
  Object.getPrototypeOf(originalObject),
  Object.getOwnPropertyDescriptors(originalObject)
);
```