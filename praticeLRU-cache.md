```javascript
// function fetchWithAutoRetry(fetcher, count) {
//   return new Promise((resolve, reject) => {
//     function attemptFetch(remainingAttempts) {
//       fetcher()
//         .then(response => {
//           if (!response.ok) {
//             throw new Error('Network response was not ok');
//           }
//           return response.json();
//         })
//         .then(data => resolve(data))
//         .catch(error => {
//           if (remainingAttempts > 1) {
//             console.log(`Retrying... ${remainingAttempts - 1} attempts left`);
//             attemptFetch(remainingAttempts - 1);
//           } else {
//             reject(error);
//           }
//         });
//     }

//     attemptFetch(count);
//   });
// }

function fetchWithAutoRetry(fetcher,count){
  return new Promise((resolve, reject)=>{
    function attemptFetch(remainingAttempts){
      fetcher().then(response=>{
        if(!response.ok){
          throw new Error('Network response was not ok')
        }
        return response.json();
      })
      .then(data => resolve(data))
      .catch(error => {
        if(remainingAttempts > 1){
          console.log(`Retrying... ${remainingAttempts - 1} attempts left`);
          attemptFetch(remainingAttempts-1)
        }else{
          reject(error);
        }
      })
    }
    attemptFetch(count);
  })
}
// const fetcher = () => fetch('https://jsonplaceholder.typicode.com/posts/1');
// Simulated fetcher function
let attempt = 0;
const fetcher = () => {
  return new Promise((resolve, reject) => {
    attempt += 1;
    if (attempt < 3) {
      console.log(`Attempt ${attempt}: Failing`);
      reject(new Error(`Attempt ${attempt} failed`));
    } else {
      console.log(`Attempt ${attempt}: Succeeding`);
      resolve({
        ok: true,
        json: () => Promise.resolve({ data: 'Success on attempt 3' })
      });
    }
  });
};

fetchWithAutoRetry(fetcher, 3)
  .then(data => console.log('Fetched data:', data))
  .catch(error => console.error('Fetch failed:', error));
function LRUCache(capacity){
  let cache = new Map();

  function get(key){
    if(!cache.has(key)){
      return -1;
    }
    const value = cache.get(key);
    cache.delete(key)
    cache.set(key,value)
    return value
  }
  function put(key, value){
    if(cache.has(key)){
      cache.delete(key)
    }else if (cache.size >= capacity){
      const firstkey = cache.key().next().value;
      cache.delete(firstkey)
    }
    cache.set(key, value);
  }
  return {get,put}
}
const lru = LRUCache(2);
lru.put(1, 1);
lru.put(2, 2);
console.log(lru.get(1));
lru.put(1, 3)
console.log(lru.get());
```
