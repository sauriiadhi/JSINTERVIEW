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

function flattenObject(obj) {
  const result = {};
  for (const key in obj) {
    if (
      typeof obj[key] === 'object' &&
      obj[key] !== null &&
      !Array.isArray(obj[key])
    ) {
      const nested = flattenObject(obj[key]);
      for (const nestedKey in nested) {
        result[key + '.' + nestedKey] = nested[nestedKey];
      }
    } else {
      result[key] = obj[key];
    }
  }
  return result;
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
