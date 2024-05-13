```javascript
function curryAndSum(...args) {
  if (args.length === ARGS_LEN) {
    return args.reduce((a, c) => a + c,0)
  }else{
    const recurr = (...args2) => {
      args = args.concat(args2)
      if (args.length === ARGS_LEN) {
        return args.reduce((a, c) => a + c, 0)
      }else{
        return recurr
      }
    }
    return recurr
  }
}
function flattenObject(obj, parent) {
  const finalObj = {}
  const generateFlatObjects = (obj, parent) => {
    for (let key in obj) {
      const currKey = parent + key;
      const currValue = obj[key]
      if (typeof currValue === 'object'){
        generateFlatObjects(currValue, currKey+".")
      }else{
        finalObj[currKey] = currValue
      }
    }
  }
  generateFlatObjects(obj, parent)
  return finalObj
}

const obj = {
  A: "12",
  B: 23,
  C: {
    P: 23,
    O: {
      L: 56
    },
    Q: [1, 2]
  }
};

console.log(flattenObject(obj, ""))

function curry(){
  let lastS = 0;
  return (newVal = 0) => {
    console.log("lastVAl",lastS)
    lastS += newVal;
    return lastS
  }
}

const sum = curry();
console.log(sum(3))
console.log(sum(5))

function sum2() {
  let lastSum = 0;

  function add(newVal) {
    console.log("lastVAl", lastSum)
    lastSum += newVal;
    return add; // Return the function itself for chaining
  }

  add.valueOf = function () {
    console.log("lastVAl",lastSum)
    return lastSum; // Override valueOf to return the sum when coerced to a primitive
  };

  return add; // Return the inner function for currying
}


console.log(sum2()(3)(4)(5).valueOf()); // Output: 12 (3 + 4 + 5)
console.log(sum2()(1)(2).valueOf()); // Output: 3 (1 + 2)

function sum() {
  let lastSum = 0;

  function add(...args) {
    lastSum = args.reduce((acc, val) => acc + val, lastSum);
    return add; // Return the function itself for chaining
  }

  add.valueOf = function () {
    return lastSum; // Override valueOf to return the last sum when coerced to a primitive
  };

  return add(...arguments); // Immediately invoke add with the initial arguments
}

console.log(sum(3)(4)(5).valueOf()); // Output: 12 (3 + 4 + 5)
function sum(a) {
  return function (b) {
    if (!b) {
      return a;
    }
    return sum(a + b);
  }
}
console.log(sum(1)(2)());
```
