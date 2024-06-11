```javascript
function cachedApiCall(expiry){
  let cache = {}
  return async function(url,config={}){
    let key = `${url}${JSON.stringify(config)}`
    let entry = cache[key]
    if(!entry || entry?.expiry < Date.now()){
      console.log("Making a fresh api call");
      try{
        const res = await fetch(url,config)
        const data = await res.json();
        cache[key] = {oldvalue:false,value:data,expiry:Date.now()+expiry};
      }catch(e){
        console.log("Making a fresh api call failed",e);
      }
    }
    return {value:cache[key].value}
  }
}

const call = cachedApiCall(1500);
call('https://jsonplaceholder.typicode.com/todos/1', {}).then((a) => console.log("1", a));
setTimeout(() => {
  call('https://jsonplaceholder.typicode.com/todos/1', {}).then((a) => console.log("2", a));
}, 800);
setTimeout(() => {
  call('https://jsonplaceholder.typicode.com/todos/1', {}).then((a) => console.log("3", a));
}, 1700);
```
