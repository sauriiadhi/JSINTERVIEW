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
```
