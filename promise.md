```javascript
// Example using Promise.all
const promise1 = Promise.resolve(1);
const promise2 = new Promise((resolve, reject) => setTimeout(resolve, 100, 'Hello'));
const promise3 = new Promise((resolve, reject) => setTimeout(resolve, 200, 'World'));

Promise.all([promise1, promise2, promise3])
  .then(values => console.log("call1:",values)); // Output: [1, 'Hello', 'World']

// Example using Promise.allSettled
const promises = [
  Promise.resolve('Success'),
  Promise.reject('Error'),
  Promise.resolve('Another Success')
];


Promise.allSettled([promise1, promise2, promise3])
  .then(results => console.log("call2:",results));
// Output:
// [
//   { status: 'fulfilled', value: 'Success' },
//   { status: 'rejected', reason: 'Error' },
//   { status: 'fulfilled', value: 'Another Success' }
// ]

// Example using Promise.race
const promiseA = new Promise((resolve, reject) => setTimeout(resolve, 100, 'A'));
const promiseB = new Promise((resolve, reject) => setTimeout(resolve, 200, 'B'));

Promise.race([promise1, promise2, promise3])
  .then(winner => console.log("call3:",winner)); // Output: 'A' (since promiseA resolves first)

// Example using Promise.any (supported in modern browsers, not in Node.js as of now)
const promisesAny = [
  new Promise((resolve, reject) => setTimeout(reject, 100, 'Error 1')),
  new Promise((resolve, reject) => setTimeout(resolve, 200, 'Success')),
  new Promise((resolve, reject) => setTimeout(reject, 300, 'Error 2'))
];

Promise.any(promisesAny)
  .then(result => console.log("call4:",result)) // Output: 'Success' (first resolved promise)
  .catch(error => console.error("call4:",error)); // Output: 'Error 1' (handled rejection)

// Example using Promise.all with async/await
async function fetchData(urls) {
  const promises = urls.map(url => fetch(url));
  const responses = await Promise.all(promises);
  const data = await Promise.all(responses.map(response => response.json()));
  return data;
}

const urls = ['https://jsonplaceholder.typicode.com/posts/1', 'https://jsonplaceholder.typicode.com/posts/2'];
fetchData(urls)
  .then(data => console.log("call5:",data))
  .catch(error => console.error("call5:",error));
```
