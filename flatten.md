```javascript
function flattenArray(arr) {
  return arr.reduce((flat, item) => {
    if (Array.isArray(item)) {
      flat.push(...flattenArray(item));
    } else {
      flat.push(item);
    }
    return flat;
  }, []);
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
```
