```javascript
function deepCopy(obj){
  if(obj === null || typeof obj !== 'object'){
    return obj
  }
  let copy = Array.isArray(obj) ? [] :{};
  for(let key in obj){
    if(obj.hasOwnProperty(key)){
      copy[key] = deepCopy(obj[key])
    }
  }
  return copy
}

const originalObject = {
  name: 'John',
  age: 30,
  hobbies: ['reading', 'traveling'],
  address: {
    city: 'New York',
    country: 'USA'
  }
};

const arr = [0,1,2,3,4,[1,2,3,4]]

const copiedObject = deepCopy(originalObject);
copiedObject.address.city = 'USA';
console.log(copiedObject);
console.log(originalObject);
const copiedarr = deepCopy(arr);
copiedarr.push(12)
console.log(copiedarr);
console.log(arr);
```
