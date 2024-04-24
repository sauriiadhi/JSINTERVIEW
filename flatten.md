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
```
